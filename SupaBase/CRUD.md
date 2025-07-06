# Config File 



##  1. app/middleware.ts   
 ```typescript
import { createServerClient, type CookieOptions } from "@supabase/ssr";
import { type NextRequest, NextResponse } from "next/server";

export const applyMiddlewareSupabaseClient = async (request: NextRequest) => {
  // Create an unmodified response
  let response = NextResponse.next({
    request: {
      headers: request.headers,
    },
  });

  const supabase = createServerClient(
    process.env.NEXT_PUBLIC_SUPABASE_URL!,
    process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!,
    {
      cookies: {
        get(name: string) {
          return request.cookies.get(name)?.value;
        },
        set(name: string, value: string, options: CookieOptions) {
          // If the cookie is updated, update the cookies for the request and response
          request.cookies.set({
            name,
            value,
            ...options,
          });
          response = NextResponse.next({
            request: {
              headers: request.headers,
            },
          });
          response.cookies.set({
            name,
            value,
            ...options,
          });
        },
        remove(name: string, options: CookieOptions) {
          // If the cookie is removed, update the cookies for the request and response
          request.cookies.set({
            name,
            value: "",
            ...options,
          });
          response = NextResponse.next({
            request: {
              headers: request.headers,
            },
          });
          response.cookies.set({
            name,
            value: "",
            ...options,
          });
        },
      },
    }
  );

  // refreshing the auth token
  await supabase.auth.getUser();

  return response;
};

export async function middleware(request) {
  return await applyMiddlewareSupabaseClient(request);
}

export const config = {
  matcher: [
    /*
     * Match all request paths except for the ones starting with:
     * - _next/static (static files)
     * - _next/image (image optimization files)
     * - favicon.ico (favicon file)
     * Feel free to modify this pattern to include more paths.
     */
    "/((?!_next/static|_next/image|favicon.ico|.*\\.(?:svg|png|jpg|jpeg|gif|webp)$).*)",
  ],
};

```








##  2. utils/supabase.client.ts   

```bash

npm install @supabase/ssr
```

 ```typescript
"use client";

import { createBrowserClient } from "@supabase/ssr";

export const createBrowserSupabaseClient = () =>
  createBrowserClient(
    process.env.NEXT_PUBLIC_SUPABASE_URL!,
    process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!
  );


```



##  2. utils/supabase.server.ts   


 ```typescript
"use server";

import { createServerClient, type CookieOptions } from "@supabase/ssr";
import { cookies } from "next/headers";
import { Database } from "../../types_db";

export const createServerSupabaseClient = async (
  cookieStorePromise: ReturnType<typeof cookies> = cookies(),
  admin: boolean = false
) => {
  const cookieStore = await cookieStorePromise;
  return createServerClient<Database>(
    process.env.NEXT_PUBLIC_SUPABASE_URL!,
    admin
      ? process.env.NEXT_SUPABASE_SERVICE_ROLE!
      : process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!,
    {
      cookies: {
        get(name: string) {
          return cookieStore.get(name)?.value;
        },
        set(name: string, value: string, options: CookieOptions) {
          try {
            cookieStore.set({ name, value, ...options });
          } catch (error) {
            // The `set` method was called from a Server Component.
            // This can be ignored if you have middleware refreshing
            // user sessions.
          }
        },
        remove(name: string, options: CookieOptions) {
          try {
            cookieStore.set({ name, value: "", ...options });
          } catch (error) {
            // The `delete` method was called from a Server Component.
            // This can be ignored if you have middleware refreshing
            // user sessions.
          }
        },
      },
    }
  );
};

export const createServerSupabaseAdminClient = async (
  cookieStore: ReturnType<typeof cookies> = cookies()
) => {
  return createServerSupabaseClient(cookieStore, true);
};



```





##  3. app/page.tsx  Create 



 ```typescript
"use client";
import { useEffect, useState } from "react";
import { createTodo, getTodos } from "../../action/todo-action";


// action/todo-action.ts
  export async function getTodos({ searchInput }: { searchInput?: string }) {
    const supabase = await createServerSupabaseClient();
    const query = supabase.from("ToDo").select("*").order("created_at", { ascending: false });
  
    if (searchInput) {
      query.ilike("title", `%${searchInput}%`);
    }
  
    const { data, error } = await query;
    if (error) throw error;
    return data;
  }

export default function Home() {
  const [searchInput, setSearchInput] = useState("");
  const [todos, setTodos] = useState<any[]>([]); // 실제 타입 지정해도 됨

    const fetchTodos = async () => {
    const data = await getTodos({ searchInput });
    setTodos(data);
  };

 

export async function createTodo(todo: { title: string; completed: boolean }) {
  const supabase = await createServerSupabaseClient();
  const { data, error } = await supabase.from("ToDo").insert(todo).select();
  if (error) throw error;
  return data;
}


const handleCreate = async () => {

      if (!searchInput.trim()) {
    alert("할 일을 입력해주세요.");
    return;
  }

    const data = await createTodo({
    title: searchInput,
    completed: false,
  });

    console.log("New Todo Created:", data);

      setSearchInput(""); 
      fetchTodos(); 

    
  };



 

```

##  4. Delete , Update 



 ```typescript


export async function deleteTodo(id: string) {
  const supabase = await createServerSupabaseClient();
  const { error } = await supabase.from("ToDo").delete().eq("id", id);
  if (error) throw error;
}

export async function updateTodo(todo: { id: string; completed: boolean; title?: string }) {
  const supabase = await createServerSupabaseClient();
  const { error } = await supabase
    .from("ToDo")
    .update({ completed: todo.completed, updated_at: new Date().toISOString(), title: todo.title })
    .eq("id", todo.id);
  if (error) throw error;
}



const handleDelete = async (id: string) => {
    await deleteTodo(id);
    fetchTodos();
  };


   const handleToggleCompleted = async (todo: any) => {
    await updateTodo({
      id: todo.id,
      completed: !todo.completed,
    });
    fetchTodos();
  };

  const handleEdit = async (todo: any) => {
    const newTitle = prompt("새로운 할 일 내용을 입력하세요:", todo.title);
    if (newTitle && newTitle.trim() !== "" && newTitle !== todo.title) {
      await updateTodo({
        id: todo.id,
        title: newTitle,
      });
      fetchTodos();
    }
  };


 return (
    <main>
      <h2>SupaBase! CRUD</h2>

      <input
        type="text"
        value={searchInput}
        onChange={(e) => {
          setSearchInput(e.target.value);
        }}
        placeholder="할일 추가하셈!"
      />



      <button onClick={handleCreate}>할일 추가</button>




      <ul style={{ marginTop: "20px" }}>

        {todos.map((todo) => (
          <li key={todo.id} style={{ marginBottom: "10px" }}>
            <span
              style={{
                textDecoration: todo.completed ? "line-through" : "none",
                marginRight: "10px",
              }}
            >
              {todo.title}
            </span>




            <button onClick={() => handleToggleCompleted(todo)}>
              {todo.completed ? "✅ 완료됨 (클릭 시 되돌리기)" : "☐ 미완료"}
            </button>

          <button
              onClick={() => handleEdit(todo)}
              style={{ marginLeft: "10px", color: "blue" }}
            >
              ✏️ 수정
            </button>




            <button onClick={() => handleDelete(todo.id)} style={{ marginLeft: "10px", color: "red" }}>
              삭제
            </button>


          </li>
        ))}
      </ul>


    </main>
  );
}

  ```

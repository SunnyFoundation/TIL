# ReactQuery

⚡️ You can get data from server and we manage the data so easily and auto cache too 





## 1. Wrap QueryClientProvider

  npm install @tanstack/react-query


``` typescript 


import { QueryClient, QueryClientProvider } from '@tanstack/react-query';

const queryClient = new QueryClient();

export default function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <YourApp />
    </QueryClientProvider>
  );
}


```


## 2. useQuery



``` typescript 


import { useQuery } from "@tanstack/react-query";

async function fetchMovies() {
  const res = await fetch("https://api.example.com/movies");
  if (!res.ok) throw new Error("데이터 가져오기 실패");
  return res.json();
}

export default function MovieList() {
  const { data, isLoading, error } = useQuery({
    queryKey: ["movies"],
    queryFn: fetchMovies,
  });

  if (isLoading) return <p>로딩 중...</p>;
  if (error) return <p>에러 발생!</p>;

  return (
    <ul>
      {data.map((movie) => (
        <li key={movie.id}>{movie.title}</li>
      ))}
    </ul>
  );
}


```




## 3. useMutation



``` typescript 


import { useMutation, useQueryClient } from "@tanstack/react-query";

async function addMovie(newMovie) {
  const res = await fetch("https://api.example.com/movies", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify(newMovie),
  });

  if (!res.ok) throw new Error("추가 실패");
  return res.json();
}

export default function AddMovie() {
  const queryClient = useQueryClient();

  const mutation = useMutation({
    mutationFn: addMovie,
    onSuccess: () => {
      // movies 목록 다시 불러오기
      queryClient.invalidateQueries({ queryKey: ["movies"] });
    },
  });

  function handleAdd() {
    const newMovie = { title: "인셉션", year: 2010 };
    mutation.mutate(newMovie);
  }

  return (
    <div>
      <button onClick={handleAdd}>영화 추가</button>
      {mutation.isPending && <p>추가 중...</p>}
      {mutation.isSuccess && <p>추가 완료!</p>}
      {mutation.isError && <p>오류 발생!</p>}
    </div>
  );
}



```

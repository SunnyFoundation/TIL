


##  1. Email Setting

### Go To Auth Section
<img width="192" alt="스크린샷 2025-07-09 오전 9 19 26" src="https://github.com/user-attachments/assets/17b77875-7c27-4140-b06d-918022696f2a" />


### Go To Email Section
<img width="230" alt="스크린샷 2025-07-09 오전 9 20 20" src="https://github.com/user-attachments/assets/704e3f4f-83b8-44ab-9c7a-21a39406f4e6" />



###  setting Email Form that  user receive email
<img width="805" alt="스크린샷 2025-07-09 오전 9 23 38" src="https://github.com/user-attachments/assets/2e4fdf05-f84a-483f-a569-45d8accdb3f9" />


###  Go To URL configuration
<img width="207" alt="스크린샷 2025-07-09 오후 7 00 28" src="https://github.com/user-attachments/assets/e3c5e2be-1b89-48c6-9fc0-33cd5a8e7a45" />

###  setting when user signup and redirect page

<img width="1008" alt="스크린샷 2025-07-09 오후 7 00 35" src="https://github.com/user-attachments/assets/dae532a6-be1c-47ee-a011-5a3bb4fcd4ac" />



##  1. Setting auth-provider.tsx
 ```typescript

"use client";

import { usePathname, useRouter } from "next/navigation";
import { useEffect } from "react";
import { createBrowserSupabaseClient } from "utils/supabase/client";

export default function AuthProvider({ accessToken, children }) {
  const supabase = createBrowserSupabaseClient();
  const router = useRouter();

  useEffect(() => {
    const {
      data: { subscription: authListner },
    } = supabase.auth.onAuthStateChange((event, session) => {
      if (session?.access_token !== accessToken) {
        router.refresh();
      }
    });

    return () => {
      authListner.unsubscribe();
    };
  }, [accessToken, supabase, router]);

  return children;
}
```


##  2. wrap authProvider into layout.tsx


 ```typescript
   return (
    <html lang="en">
      <body>
    <AuthProvider accessToken={session?.access_token}>
              {session?.user ? <MainLayout>{children}</MainLayout> : <Auth />}
    </AuthProvider>
    </body>
    </html>
  );


```

##  3. check User's  login session


 ```typescript
 const supabase = await createServerSupabaseClient();
  const {data : { session }, } = await supabase.auth.getSession(); 
  console.log(session);


```



##  4. Sign Up


 ```typescript
 const {data , error} = await supabase.auth.signUp({
            email,
            password,
        })



```


##  5. OTP Auth


 ```typescript

   const {data , error} = await supabase.auth.verifyOtp({
            type : "signup",
            email,
            token: otp,
        });
```

 


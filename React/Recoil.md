# Recoil

⚡️ Manage your state all over the globe 





## 1. Wrap RecoilProvider



``` typescript 

  ‘use client’ 

Import {RecoilRoot} from “recoil”

Export default function RecoilProvider ({children}) {
      Return <RecoilRoot> {children} </RecoilRoot>
   }



```


## 2.  layout.tsx



``` typescript 

    <RecoilProvider>
       <html lang=“en”>
          <body>
             {children}
         </body>
      </html>
     </RecoilProvider>


```


## 3.  atoms.ts



``` typescript 

Export const userState = atom({

    Key : “userState”,
    Default: { 
           Email : null,
           Name : null 
        }     

})


```





## 4.  Just use whatever you want 



``` typescript 
Import {userState} from  recoil/atoms


Const [user, setUser] = useRecoilState(userState);  // you can change data in atom state

Const user = useRecoilValue(userState);  // You only read date in atom state


```

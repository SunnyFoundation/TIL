# Dynamic Url Parameter



![스크린샷 2025-06-21 오전 11 54 17](https://github.com/user-attachments/assets/c5716e3b-b2f6-4756-860b-299c8c5af044)





``` typescript 

import { useRouter } from "next/router"

export default function Page() {
    const router = useRouter();
    const  {id} = router.query;

    return <h1>book{id}</h1>
}
```

# Layout

⚡️ Layout page covered page.tsx 


<img width="159" alt="스크린샷 2025-06-25 오후 8 20 16" src="https://github.com/user-attachments/assets/0fdea0bd-b9ab-43f7-8243-1cf3edcf28da" />

￼



``` typescript 

1. User enter your search page
2. Layout page show up
3. Page.tsx show up
export default function Layout({children} : {children : React.ReactNode}) {
    return  (
        <div>
            <div>Layout page first show up</div>
             {children} // page.tsx 
        </div>
    )
}

```

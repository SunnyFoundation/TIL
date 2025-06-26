# params

⚡️ you can receive URL parameter







``` typescript 

export default async function  Page({params}: Promise<{params: {id:string}}>) {
    const {id} = await params;
    return (
        <div>{id}</div>
    )
}

```

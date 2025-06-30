# Streaming

⚡️ When browser request async page then your server First of all send page that not too long rendering page <br>  Finally send aysnc page that too long rendering page 







``` typescript 


import { Suspense } from "react";
import NewsList from "./NewsList";

export default function Page() {
  return (
    <div>
      <Header />
      <Suspense fallback={<div>뉴스 불러오는 중...</div>}>
        <NewsList />
      </Suspense>
    </div>
  );
}


```

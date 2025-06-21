# API Route



![스크린샷 2025-06-21 오후 12 39 30](https://github.com/user-attachments/assets/a35bef0a-eadb-4634-9476-f4b42aa6bdcd)





``` typescript 


import type { NextApiRequest, NextApiResponse } from "next";



export default function handler(
  req: NextApiRequest,
  res: NextApiResponse,
) {

  const date = new Date();
  res.json({ time : date.toLocaleDateString()})
}


```

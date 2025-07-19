# Run Next.js using docker compose 




## 1️⃣ Create next.js project

```mkdir nextjsComposeProject ```  
```cd nextjsComposeProject ```  
``` Code . ```  
``` npx create-next-app@latest nextjscomposeproject ```

## 2️⃣ Create DockerFile

```dockerfile

FROM node

WORKDIR /app

COPY . .

RUN npm install 

RUN npm run build

EXPOSE 3000

ENTRYPOINT [ "npm", "run", "start" ]

```


## 3️⃣ Create compose.yml

```compose.yml
services:
  my-web-server:
   build: .
   ports:
     - 80:3000
```


## 4️⃣ ```docker compose up -d  —- build ```

<img width="662" height="500" alt="스크린샷 2025-07-19 오전 11 36 31" src="https://github.com/user-attachments/assets/f3602c77-ce54-4ea9-955e-0a85c4d5a383" />



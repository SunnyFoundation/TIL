# 🤔 What is Compose
Let's get started What Compose is  
Manage  multiple container in one file so you can run your container just one CLI





## 1️⃣  Create compose.yml file


```compose.yml
    services:  
      my-web-server:
      container_name: web-server
      image: nginx
      ports:
       - 80:80

```


##  ``` docker compose up ```

  run your compose file 

  
  <img width="641" height="273" alt="스크린샷 2025-07-19 오전 11 10 17" src="https://github.com/user-attachments/assets/f83f4de3-abc9-4bcb-ad69-20cefe8f8c8a" />



  ##  ``` docker compose down ```

  remove your compose 








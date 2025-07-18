# COPY


##it can copy from your host folder directory 


```dockerfile

FROM node

COPY my-app /my-app/

ENTRYPOINT [ "/bin/bash", "-c", "sleep 500" ]
```


### 1. docker build -t my-server .
### 2. docker run -d my-server
### 3. docker ps -a
### 4. docker exec -it 8efd bash
### 5. root@8efd9320d6f5:/# ls
```
### bin  boot  dev  etc  home  lib  media  mnt  my-app  opt  
proc  root  run  sbin  srv  sys  tmp  usr  var
```


### 6. root@8efd9320d6f5:/# cd my-app

### 7 .root@8efd9320d6f5:/my-app# ls


```
app.tsx

```



### 8. root@8efd9320d6f5:/my-app# cat app.tsx

```
console.log(‘Hello ‘Docker);

```



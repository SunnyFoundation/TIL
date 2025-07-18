# DockerFile

⚡️ File that can create your own docker image 




## Create own your Base image

```DockerFIle
FROM node // what kind of base Image you use?


ENTRYPOINT [ "/bin/bash", "-c", "sleep 500" ]  // when container first open then first executed command
```


## docker build -t my-node-server .
```DockerFIle
standard of dockerfile  it can created your own image 
```


## docker image ls
```DockerFIle
 check your image 
```



## docker run -d my-node-server

```DockerFIle
 Executed your container
```



## docker exec -it [container ID] bash


```DockerFIle
 Enter your Container
```



## Check your Container through terminal


```DockerFIle
node -v // v24.4.1

```







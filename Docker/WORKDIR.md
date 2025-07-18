# WORKDIR


##  ⚡️ when Your image first executed then First open your file or folder




```dockerfile


FROM node

WORKDIR /my-dir

COPY ./ ./

ENTRYPOINT [ "/bin/bash", "-c", "sleep 500" ]


```

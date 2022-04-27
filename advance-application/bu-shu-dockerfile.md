# 部署 dockerfile

### dockerfile

分為兩階段

* 第一階段 build出可執行檔 （golang升级1.18后， go.sum 要記得COPY）
* 第二階段 可以將執行檔與config放入即可，執行時帶入🍊式需要的啟動參數

```
FROM golang:1.17-alpine AS builder

ENV GO111MODULE=on
RUN go env
WORKDIR /go/src/eda/rest-push-device

RUN apk update && apk add  pkgconfig build-base git
# Copy go.mod and go.sum files to workspace
COPY go.mod ./
COPY go.sum ./
RUN go mod download
# Copy the source code
COPY . ./
RUN go build -o <your-app>

FROM alpine

COPY --from=builder /go/src/<workfolder>/<your-app>/<your-app> /<your-app>
COPY --from=builder /go/src/<workfolder>/<your-app>/configs/docker/configuration.toml /configs/docker/configuration.toml

ENTRYPOINT ["/<your-app>","--profile=docker","--confdir=/configs"]
```



.dockerignore 這個檔案裡的會被忽略造成COPY no such file or direct，需注意內容



參考出處

* [copying-a-file-in-a-dockerfile-no-such-file-or-directory](https://stackoverflow.com/questions/32997269/copying-a-file-in-a-dockerfile-no-such-file-or-directory)
* [How To Containerize Your Go Application with Docker](https://aws.plainenglish.io/how-to-containerize-your-go-application-with-d-4b6fc118bf23)
* [golang升级1.18后，DockerFile报错 missing go.sum entry](https://www.jianshu.com/p/a13e343f95a0)\
  \





---
description: Golang 在 1.11 開始就推出了 Go Module，我是從這邊就直接使用 Go Module了
---

# Go Module

### go Module 語法

幾個與moudule 有關的指令與參數紀錄

```
go mod init 
go mod tidy 添加需要用到但go.mod中查不到的模块,删除未使用的模块
go mod download
go mod graph
go mod why
go env -w GOFLAGS=-mod=mod
go help get usage: go get [-d] [-t] [-u] [-v] [-insecure] [build flags] [packages]
```



如果你看到以下錯誤訊息，表示沒有先下go mod init

```
//go.mod file not found in current directory or any parent directory; see 'go help modules'
```

### 參考

* 官方Go Modules Reference  [https://go.dev/ref/mod](https://go.dev/ref/mod)
* go mod graph 可视化——gmchart\
  [https://segmentfault.com/a/1190000038897207](https://segmentfault.com/a/1190000038897207)




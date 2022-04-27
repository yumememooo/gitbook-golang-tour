# 不同版本的差異

### 不同版本的功能

Go 1.15 以前

* go get 拉取依賴庫，並安裝執行檔

Go1.16&#x20;

* **GO111MODULE 環境變數默認 on**
* 更新依赖**只能使用 go get 命令**，go build 和 go test 將不在更改mod相關文件。
* 下載安裝 Go 二進位制程式，<mark style="color:orange;">不再使用 go get，而是 go install</mark>，go get 只用來下載普通包 必須要避免執行 go get 命令時，讓它接觸到我們的 go.mod 檔案 ，否則它會將我們安裝的工具作為一個依賴。
* 另外新增版本`撤回`。



Go 1.17&#x20;

新特性:這次最主要的變化有：

* Module graph pruning：Module 依賴圖修剪&#x20;
  * module依賴圖修剪也帶來了一個副作用，那就是go.mod文件size的變大。
  * 因為Go 1.17版本後，每次go mod tidy（當go.mod中的go版本為1.17時），go命令都會對main module的依賴做一次深度掃描(deepening scan)，並將main module的所有直接和間接依賴都記錄在go.mod中（之前說的版本只記錄直接依賴）。go 1.17將直接依賴和間接依賴分別放在兩個不同的require塊兒中。
* Lazy Loading：Module 延遲載入 Go 1.17 開發新的 Module 功能，特別是懶惰Module載入，這將使 Module 載入過程更快、更穩定。延遲載入就一句話：那些根本沒有用上的模組（比如上面例子中的模組 c），Go 1.17 後，Go 命令不會去讀取其 go.mod 檔案。如果之後需要了，再會去載入。
* 新增`廢棄Deprecated` 註釋

\
\




#### -mod=mod的功能

以下解釋來自 \[Go Modules Reference]\(https://go.dev/ref/mod#introduction)

In Go 1.15 and lower, the `-mod=mod` flag was enabled by default, so updates were performed automatically. Since Go 1.16, the `go` command acts as if `-mod=readonly` were set instead: if any changes to `go.mod` are needed, the `go` command reports an error and suggests a fix.

*   The `-mod` flag controls whether `go.mod` may be automatically updated and whether the `vendor` directory is used.

    * `-mod=mod` tells the `go` command to ignore the vendor directory and to [automatically update](https://go.dev/ref/mod#go-mod-file-updates) `go.mod`, for example, when an imported package is not provided by any known module.
    * `-mod=readonly` tells the `go` command to ignore the `vendor` directory and to report an error if `go.mod` needs to be updated.
    * `-mod=vendor` tells the `go` command to use the `vendor` directory. In this mode, the `go` command will not use the network or the module cache.
    * By default, if the [`go` version](https://go.dev/ref/mod#go-mod-file-go) in `go.mod` is `1.14` or higher and a `vendor` directory is present, the `go` command acts as if `-mod=vendor` were used. Otherwise, the `go` command acts as if `-mod=readonly` were used.

    \
    \
    See [https://golang.org/ref/mod#go-get](https://golang.org/ref/mod#go-get) for details.\
    See 'go help install' or [https://golang.org/ref/mod#go-install](https://golang.org/ref/mod#go-install) for details.

### 參考文章

* &#x20;golang 1.14 1.15 1.16 新特性一览\
  [https://www.jianshu.com/p/f27c4f561544#module](https://www.jianshu.com/p/f27c4f561544#module)
* Go 1.16 中關於 go get 和 go install 你需要注意的地方\
  [https://iter01.com/572906.html](https://iter01.com/572906.html)
* Go 1.17 新特性：Module 有哪些變化？\
  [https://www.gushiciku.cn/pl/gnIA/zh-tw](https://www.gushiciku.cn/pl/gnIA/zh-tw)
* Go 1.17中值得关注的几个变化\
  [https://tonybai.com/2021/08/17/some-changes-in-go-1-17/](https://tonybai.com/2021/08/17/some-changes-in-go-1-17/)

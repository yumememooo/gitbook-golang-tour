# nil channel



### nil\_channel

* go中，可以對nil值channel進行讀寫操作，但會永遠阻塞，而為nil值的channel调用close()會panic
* \`註:這邊不像nil map一樣塞值就會引發panic

#### 例子1:往nil\_channel送值

* 當channel只有宣告，但沒有經過make，預設值是nil

```
func main() {
	var stringChan chan string
	fmt.Println(stringChan)
	stringChan <- "hello world"
	time.Sleep(time.Minute) //模擬用 讓程式暫緩退出
}
```

> 結果: 因為送不進去就會塞住bloak，等不到有其他goroutines取走資料 出現fatal error: all goroutines are asleep - deadlock!

#### 例子2:非同步往nil\_channel送值

```
func main() {
	var stringChan chan string
	// stringChan := make(chan string)
	go func() {
		stringChan <- "hello world"
        fmt.Println("inpt channal")
	}()
	

	time.Sleep(time.Minute) //模擬用 讓程式暫緩退出
}
```

* 結果: 什麼事都沒發現，但也塞不進去，形成阻塞，當前goroutines在阻塞等待

**例子三:非同步往nil\_channel送值，並從nil讀取**

```
func main() {
	var stringChan chan string
	// stringChan := make(chan string)
	go func() {
		stringChan <- "hello world"
	}()
	fmt.Println(<-stringChan)

	time.Sleep(time.Minute) //模擬用 讓程式暫緩退出
}

// <!-- go run main.go
// fatal error: all goroutines are asleep - deadlock!

// goroutine 1 [chan receive (nil chan)]:
// main.main()
//         D:/go/src/demo-go/12-go-channel/main.go:15 +0x4e

// goroutine 6 [chan send (nil chan)]:
// main.main.func1()
//         D:/go/src/demo-go/12-go-channel/main.go:12 +0x25
// created by main.main
//         D:/go/src/demo-go/12-go-channel/main.go:11 +0x45
// exit status 2 -->
```

* 結果 引發fatal error: all goroutines are asleep - deadlock!

**參考文章**

* [为什么 Go 会有 nil channels](https://lingchao.xin/post/why-are-there-nil-channels-in-go.html)
  * 這個例子看起來利用Nil作為判斷條件。

# for循環+goroutine的坑

#### for循環+goroutine的坑 (<mark style="color:red;">Golang中Routine闭包中的一个坑/協程引用迴圈變數的問題</mark>)

* 主協程的迴圈很快就跑完了，而各個協程才開始跑，此時 `i` 的值可能會重複出現指向最後一個值

```
func testRoutine() { //Golang中Routine闭包中的一个坑
	for i := 0; i < 100; i++ {
		go func() { //这是因为很有可能当 for-loop 执行完之后 goroutine 才开始执行，这个时候 val 的值指向切片中最后一个元素。
			fmt.Println(i) //值可能是0-100中的任意数字的，有一些可能会重复出现-->引用传递（同一个对象）给了子协程
		}()
	}
	time.Sleep(1 * time.Second)
}
```



#### 解決方法

* 將參數傳進go func(xxxx)

```go
func testRoutineFix2() {
	for i := 0; i < 100; i++ {
		go func(ii int) {
			fmt.Println(ii)
		}(i) //参数都是通过值传递进行传递的
	}
	time.Sleep(1 * time.Second)
}
```

* 另一種方法是在循環內定義新的變量，由於在循環內定義的變量在循環遍歷的過程中是不共享的

```
func testRoutineFix3() {
	for i := 0; i < 100; i++ {
		ii := i
		go func() {
			fmt.Println("testRoutineFix3",ii)
		}()
	}
	time.Sleep(1 * time.Second)
}

```



<details>

<summary>完整程式碼</summary>

[https://github.com/yumememooo/go-my-playground/blob/main/2.gorountine/2.for-go/main.go](https://github.com/yumememooo/go-my-playground/blob/main/2.gorountine/2.for-go/main.go)

結果：

```
testRoutine 3
testRoutine 10
testRoutine 10
testRoutine 10
testRoutine 10
testRoutine 10
testRoutine 10
testRoutine 10
testRoutine 10
testRoutine 10
testRoutineFix1 0
testRoutineFix1 9
testRoutineFix1 1
testRoutineFix1 6
testRoutineFix1 7
testRoutineFix1 8
testRoutineFix1 3
testRoutineFix1 2
testRoutineFix1 4
testRoutineFix1 5
testRoutineFix2 0
testRoutineFix2 4
testRoutineFix2 1
testRoutineFix2 3
testRoutineFix2 6
testRoutineFix2 7
testRoutineFix2 9
testRoutineFix2 2
testRoutineFix2 8
testRoutineFix2 5
testRoutineFix3 0
testRoutineFix3 1
testRoutineFix3 2
testRoutineFix3 3
testRoutineFix3 9
testRoutineFix3 4
testRoutineFix3 5
testRoutineFix3 6
testRoutineFix3 7
testRoutineFix3 8
```





</details>


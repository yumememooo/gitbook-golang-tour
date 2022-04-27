# 使用Select實現無阻塞讀取

* 可以使用select+default 實現無阻塞讀取，但需要注意default條件處理，避免丟失。

```
go func() {
	select {
	case eventChan <- value:
		fmt.Println("add chan done")
	default:
		fmt.Println("default:", value)// receiving from c would block
	}
}()

```

* 可以使用select+Timeout 超時機制,超過一定時間後就做其他事情,給通道增加讀寫數據的時間

```
go func() {
 		timeout := time.NewTimer(time.Microsecond * 500)
select {
case eventChan <- value:
fmt.Println("add chan done")
case <-timeout.C:
fmt.Println("write time out")
}
}()

```


# 創建Goroutine

**啟動方式，只需使用關鍵字 go 在函數前面即可。**

Demo: https://play.golang.org/p/FhKQDc7Z8Dk

```
package main

func main() {
    go say("Hello World")
……..
}

func say(s string) {
    println(s)
}

```

**匿名函數**

```
func main() {
 
	go func() { //匿名函數
		 println("Hello World")
	}()
	...
}

```

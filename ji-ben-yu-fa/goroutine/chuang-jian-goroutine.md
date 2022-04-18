# 創建Goroutine

#### Go 的併發：Goroutine

goroutine 是一種"go的協程"，與其他語言的協程類似，不須yield 和 resume，而是用channel來通信。&#x20;

Go runtime 會負責調度，會把發生阻塞的goroutine調度走，可以在有限CPU下做有效的利用。&#x20;

GOMAXPROCS: 預設是CPU用到的最大核心數量，N個goruntine會對應到M個thread上。 Goroutines又稱輕量級線程，開一個gorountine默認只需2\~4KB的空間，相較於thread是MB級的空間，開銷小。&#x20;

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

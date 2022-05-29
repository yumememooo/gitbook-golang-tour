# 併發與協程



**併發與協程**

並行Parallel 是利用多個 CPU 達到同時並行處理任務的需求&#x20;

併發Concurrent 是許多任務在爭搶同一個 CPU 的資源,切換非常快，使用者通常不會感覺到任務實際上一直在切換。



**程式**（Application ）>>進程（ Process ）

線程/執行緒（ Thread ):由系統面 CPU 內核去進行調度&#x20;

協程（ Coroutine ）:調度由程式面用戶控制

#### Go 的併發：Goroutine

* goroutine 是一種"go的協程"，與其他語言的協程類似，不須yield 和 resume，而是用channel來通信。&#x20;
* Go runtime 會負責調度，會把發生阻塞的goroutine調度走，可以在有限CPU下做有效的利用。&#x20;
* GOMAXPROCS: 預設是CPU用到的最大核心數量，N個goruntine會對應到M個thread上
* Goroutines又稱輕量級線程，開一個gorountine默認只需2\~4KB的空間，相較於thread是MB級的空間，開銷小。&#x20;

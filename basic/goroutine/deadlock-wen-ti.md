---
description: 解說all goroutines are asleep - deadlock!
---

# deadlock問題

在同步資料時，錯誤的處理容易發生死鎖，golang會拋出`all goroutines are asleep - deadlock!`

> * 出錯資訊的意思是在main goroutine線中， 期待從其他goroutine線放入資料 ，但是其他goroutine線都已經執行完了(<mark style="color:red;">all goroutines are asleep</mark>)，就<mark style="background-color:red;">永遠不會有資料放入管道。</mark> 所以main goroutine線在等一個永遠不會來的資料，那整個程式就永遠等下去了
> * [golang報錯： all goroutines are asleep - deadlock!](https://www.gushiciku.cn/pl/21LJ/zh-tw)
> *   <mark style="color:red;">死鎖</mark>
>
>     > 所有的並發協程彼此等待，除非外界的干預，否則程式將永遠無法恢復運行。

#### 範例

* <mark style="background-color:red;">unbuffered channal</mark> block example

```
package main

import "fmt"

func main() {
	ch := make(chan int)
	
	ch <- 1 // 等到天荒地老
	fmt.Println(<-ch)
}
// fatal error: all goroutines are asleep - deadlock!

// goroutine 1 [chan send]:
// main.main()
```

---
description: '使用channel : goroutine之間的溝通橋樑'
---

# channel

Channel 用途&#x20;

* Channel就像是一個Queue, 遵守著FIFO的規則
* 保證收發資料的順序 訊息通道與傳遞：
* 生產者消費者模型&#x20;
* 互斥鎖, channel内部有Mutex&#x20;
* 含有buffersize 的通道 預設雙向，可以控制關閉通道。

![](../../.gitbook/assets/go.png)

#### 宣告方式:&#x20;

var 通道名稱 <mark style="background-color:green;">chan</mark> 通道類型&#x20;

透過make來產生實例。



ch := make(chan int)&#x20;

ch <- v **// Send v to channel ch**

v := <-ch **// Receive from ch, and // assign value to v.**

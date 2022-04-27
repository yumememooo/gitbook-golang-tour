# 記憶體洩漏

使用當gorountine需注意的問題:

* 雖然開gorountine的基本開銷小，無限制的gorountine數量仍會造成記憶體的消耗。&#x20;
* 須注意gorountine的終止與銷毀是否正常。&#x20;
* 記憶體洩漏:&#x20;
  * 雖然go有自動垃圾回收，但是當gorountine沒有辦法正確終止時(尤其用了channel發生阻塞時)，go channel使用不當，也極易引起goroutine泄漏，導致記憶體問題。
* &#x20;可以透過pprof 或其他監測工具觀察gorountine 創建數量及記憶體是否正常。&#x20;
* 可以透過分析 go tool pprof 找出發生阻塞的地方。

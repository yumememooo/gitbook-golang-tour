---
description: 是一種類型，更準確的說 interface 是一種具有一組方法的類型，這些方法定義了 interface 的行為。
---

# interface

安全的斷言類型,型別判定 (type assertion) 應該增加型別判斷 https://wangdaming.gitbooks.io/golang/content/xing\_bie\_zhuan\_huan\_jian\_cha.html

用空介面當成萬用型別，interface{}，由於任何類型都至少實現了0個方法，所以空接口可以承接任意類型。

//\[Golang] interface的類型斷言是如何實現 https://segmentfault.com/a/1190000039894161 因為Go中是沒有泛型，所以我們可以用空的interface{}來作為一種偽泛型使用 類型斷言的性能損耗

在Golang中實作多型 須仰賴interface Golang - 深入理解interface 常見用法 https://blog.kennycoder.io/2020/02/03/Golang-%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3interface%E5%B8%B8%E8%A6%8B%E7%94%A8%E6%B3%95/

***

Golang Reflection https://ithelp.ithome.com.tw/articles/10261443

Golang Tag

---
description: Go是Google開發的一種靜態強型別、編譯型、並發型，並具有垃圾回收功能的程式語言。
cover: ../.gitbook/assets/go_google_case_study_carousel.png
coverY: 0
---

# Go intro.

**設計初衷**：設計Go語言是為了解決當時Google開發遇到的一些問題: C++編譯慢、沒有入門級友好的內存（記憶體）管理 數以萬計行的代碼，失控的依賴難以維護 部署的平台各式各樣，交叉編譯困難

列出幾個優點：

＃開發人員友善：語法簡潔，編譯快，啟動速度快，有垃圾回收(Garbage Collection, GC)

＃沒用到的import 或者是 變數, 都會在編譯時期給予警告

＃部署方便：Go 交叉編譯(跨平台編譯)，二進位制可執行檔案

＃簡單方便的併發機制 輕量級線程Goroutines，天生併發的設計，開銷小

**預期可縮小70\~80% storage/memory**

****

**To Go or Not to ?**

![](../.gitbook/assets/motorcycle.svg)

[https://go.dev/blog/](https://go.dev/blog/)

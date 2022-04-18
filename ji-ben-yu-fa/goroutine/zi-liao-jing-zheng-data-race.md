---
description: 'Data race: 指多個gorountine處理同一個共享變數存取導致出現結果可能不正確的情況。'
---

# 資料競爭 data race

### go自帶檢測方法: -race&#x20;

加在go run -race main.go執行，可以找出問題。

#### 遇到data race 的幾種處理方法:

1. Atomic 原子操作(效能較鎖好,但只有簡單的型態可用)
2. 加鎖:互斥鎖
3. Channel






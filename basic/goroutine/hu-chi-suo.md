# 互斥鎖

### 互斥鎖

互斥鎖: 傳統的併發會使用鎖來確保區域內只會有一個線程來存取&#x20;

```
sync.Mutex
mutex.Lock
…. //只有擁有互斥鎖的goroutine 可以執行
mutex.UnLock
```

#### 使用鎖的注意事項:

* Lock/Unlock 需要成對出現，鎖了一次又鎖一次 or 忘了解鎖&#x20;
* 盡量減少鎖的持有時間&#x20;
* 可使用defer來正確解鎖

```
mu.Lock()
defer mu.Unlock()  // defer 在函數返回前會執行
….//過程中發生錯誤才不會沒有解鎖
```

**\*如果發生deadlock，有時不會發生警告，而是程式就像是卡住一樣。**

```
fatal error: all goroutines are asleep - deadlock
```


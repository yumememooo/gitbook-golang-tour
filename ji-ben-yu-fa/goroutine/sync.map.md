# sync.map

### 介紹：

[https://pkg.go.dev/sync#Map](https://pkg.go.dev/sync#Map)

* sync.Map是類似於map\[interface{}]interface{} but is safe for concurrent，不需額外使用鎖
* The zero Map is empty and ready for use. A Map must not be copied after first use.
* Map 類型針對兩種常見用例進行了優化：(1) 當給定鍵的條目只被寫入一次但讀取多次時，如在只會增長的緩存中，或 (2) 當多個 goroutine 讀取、寫入和讀取時覆蓋不相交的鍵集的條目。在這兩種情況下，與使用單獨的 Mutex 或 RWMutex 配對的 Go map 相比，使用 Map 可以顯著減少鎖爭用。



#### sync.Map 的元素遍歷

不可以使用 for 循環 或者 for range 循環，而是使用 Range 配合一個回調 函數 進行遍歷操作。

回調函數的返回值在需要繼續遍歷時，返回 true，終止遍歷時，返回 false。

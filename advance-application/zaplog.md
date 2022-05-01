# zaplog

#### 功能

* 實作使用高性能 zap log 框架
* 擁有 log level 配置 (常用 debug/warn/info/error)與程式碼位置
* 可以選擇印出在 console 或是文件（要外掛 lumberjack 去分割）



#### LOG 輸出選擇

* zap.Logger 輸出需針對 Type 去輸入，使用跟印出看起來都比較麻煩一點
* zap.SugaredLogger 就像是語法糖,函式可以增加易用性，但犧牲效能

#### 時間格式：

\#### ISO8601TimeEncoder&#x20;

```
encoderConfig.EncodeTime = zapcore.ISO8601TimeEncoder 
//"2006-01-02T15:04:05.000Z0700"
```

時間顯示 2022-04-15T08:24:16.474+0800 INFO

\#### 自定義：時間顯示到ms

```
encoderConfig.EncodeTime = zapcore.TimeEncoderOfLayout("2006-01-02T15:04:05.000000")
```

時間顯示 2022-04-15T09:50:40.456340



\#### 參考

Go：zap 自义定时间戳格式\
[https://blog.csdn.net/test1280/article/details/117266333](https://blog.csdn.net/test1280/article/details/117266333)

更多格式\
[https://golang.cafe/blog/golang-time-format-example.html](https://golang.cafe/blog/golang-time-format-example.html)



> \
>

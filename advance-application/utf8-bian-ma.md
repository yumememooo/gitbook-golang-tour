# UTF-8编码

Golang 源码本身使用的是UTF-8编码（非utf-8格式的源码不能编译），除了ascii，golang 也可以打印Unicode的字符编码



判斷是否是big5或是gbk的範例碼

<details>

<summary>範例</summary>

```go

func isBig5(data []byte) bool {
length := len(data)
var i int = 0
for i < length {
if data[0] >= 0x81 && data[0] <= 0xFE {
//if(strIn[0]>=(char)0x81 && strIn[0]<=(char)0xFE)

if data[1] >= 0x40 && data[1] <= 0x7E {
// if(strIn[1]>=(char)0x40 && strIn[1]<=(char)0x7E)
return true
} else if data[1] >= 0xA1 && data[1] <= 0xFE {
// if(strIn[1]>=(char)0xA1 && strIn[1]<=(char)0xF1)

return true
} else {
return false

}
} else {

return false

}
}
return true
}
--------
func isBig5(data []byte) bool {
length := len(data)
var i int = 0
for i < length {
if data[i] >= 0x81 && data[i] <= 0xFE {
//if(strIn[0]>=(char)0x81 && strIn[0]<=(char)0xFE)
i++
if data[i] >= 0x40 && data[i] <= 0x7E {
// if(strIn[1]>=(char)0x40 && strIn[1]<=(char)0x7E)
i++
continue
} else if data[i] >= 0xA1 && data[i] <= 0xFE {
// if(strIn[1]>=(char)0xA1 && strIn[1]<=(char)0xF1)

i++
continue
} else {
return false

}
} else {

return false

}
}
return true
}

go
```

</details>

\
GO程式碼實現判斷字元編碼格式及編碼格式轉換（utf-8、gbk）\
[https://www.gushiciku.cn/pl/pfkW/zh-tw](https://www.gushiciku.cn/pl/pfkW/zh-tw)\
但是如果原本就是UTF-8 再轉又會變成亂碼

\
\[小知識] 判斷是否為繁體字(Big5)\
[https://blog.csdn.net/CuGBabyBeaR/article/details/8664694](https://blog.csdn.net/CuGBabyBeaR/article/details/8664694)\
\
\
\==========\
\
MQTT.fx Send:简体字\\\tNXT-H07\\\t7\\\t20210504105551\\\t4\\\t9\
?体字\\\tNXT-H07\\\t7\\\t20210504105551\\\t4\\\t9\
isUtf8:false\
isGBK:true\
2022-01-03T10:14:35.176+0800 DEBUG mqclient/devicelisten.go:129 \[MQTT Client] RawData : ={?�^�r\\\tNXT-H07\\\t7\\\t20210504\
105551\\\t4\\\t9 1641176075173 \[]}\
\
Cient Send简体字\
蝞�雿枏�\
isUtf8:true\
isGBK:false\
2022-01-03T10:14:00.320+0800 DEBUG mqclient/devicelisten.go:129 \[MQTT Client] RawData : ={简体字 1641176040318 \[]}

\
\
\
\

---
description: 2006-01-02 15:04:05-0700是一串go獨特神奇的對應順序。可以看time/format.go
---

# time 時間包

* 2006-01-02 15:04:05-0700是一串go獨特神奇的對應順序。
  * 2006-01-02 15:04:05-0700 對應到 yyyy-MM-dd HH:mm:ss Z
  * `記憶順序有點像是06代表年，後面則是1,2,3,4,5,7`
  * [time/format.go](https://go.dev/src/time/format.go) 了解更多alias寫法(01或1...)
  * [golang 與java time的對照表](https://programming.guide/go/format-parse-string-time-date-example.html) 瞭解與java的不同



#### 時間的轉換

* case1:時間戳轉換成時間
* case2:將時間做格式化輸出 layout1 := "2006-01-02T15:04:05"  t.Format(layout1)
* case3:時區轉換: FixedZone(name,位移的秒數)，可以自訂時區命名信息，loc := time.FixedZone(“UTC-8”, -8 \* 60 \* 60)第二個參數轉移多少秒，可以改+8時區等等
*   case4:時區轉換:&#x20;

    * LoadLocation(name)，可以輸入空值，”UTC”，”Local”，或是時區的資料庫 EX: “Asia/Taipei”，命名使用的資料庫為[IANA Time Zone database](https://en.wikipedia.org/wiki/List\_of\_tz\_database\_time\_zones)
    *   好處是不用自己輸入到底是＋8還加多久，知道時區命名就好，但是背後的定義還是會依下列順序去找尋對應資料：

        * ZONEINFO 環境變數所指定的zip文件
        * Unix系统中已经安装的
        * $GOROOT/lib/time/zoneinfo.zip



    > 因此如果在windows系统上，没有安装go語言環境，time.LoadLocation會失敗，建議用time.FixedZone。
    >
    > 另外在docker環境裡也要注意使用的image是否已經有包含這些資料，否則會出現unknown time zone XXXX的錯誤，解決方法需要加入以下設定
    >
    > ```
    > FROM alpine
    > ...
    > COPY --from=0 /usr/local/go/lib/time/zoneinfo.zip /opt/zoneinfo.zip
    > ENV ZONEINFO /opt/zoneinfo.zip
    > OR
    > RUN apk --no-cache add tzdata
    > ...
    > ```



* 範例程式：

```
package main

import (
	"fmt"
	"time"
)

func main() {
	var Time int64
	Time = 1619083664867 //ms->2021-04-22 17:27:44

	t := time.Unix(0, Time*int64(time.Millisecond))
	fmt.Println("case1: timestamp to time:", t)
	
	
	layout1 := "2006-01-02T15:04:05"
	fmt.Println("case2: Formatlayout1:", t.Format(layout1))
	
	zone := time.FixedZone("", +0*60*60)
	newTimezone0 := t.In(zone)
	fmt.Println("case3: Timezone at +0:", newTimezone0.Format(layout1))

	// name := "America/New_York"
	name := "Asia/Taipei"
	t, err := TimeIn(t, name)
	if err != nil {
		fmt.Println("err:", err)
	}
	fmt.Println("case4: Timezone at Taipei:", t.Format(layout1))

}
func TimeIn(t time.Time, name string) (time.Time, error) {
	loc, err := time.LoadLocation(name)
	if err == nil {
		t = t.In(loc)
	}
	return t, err
}


timestamp: 1619083664867
case1: timestamp to time: 2021-04-22 09:27:44.867 +0000 UTC
case2: Formatlayout1: 2021-04-22T09:27:44
case3: Timezone at +0: 2021-04-22T09:27:44
case4: Timezone at Taipei: 2021-04-22T17:27:44
```

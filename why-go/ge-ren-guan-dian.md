# 個人觀點

{% hint style="info" %}
<mark style="color:red;">僅個人使用意見</mark>
{% endhint %}

### 優點

#### 開發效率快

後端工作上有維護同樣都是web服務的ＡＰＩ，一個由sprint建置的java與由Ｇin建置的go，光啟動速度，一個幾十秒，一個十秒內就差很多了！！ 而java建置的服務記憶體會有200Mb以上，go建置的才在20Mb以上，節省了90%!

#### 併發（輕量線程）操作

雖然一開始併發操作對初學者來講很難看懂，但比起其他語言，要完成不同併發之間的溝通互動，go天生的設計還是看起來比較簡易，（不知道為什麼，有些併發功能我還是不懂怎麼用其他語言去完成ˊˋ 查半天還是不會），但是用go去寫，簡簡單單快快速速就完成了！？＠＠&#x20;

#### 任何平台都可以運行

編譯上簡單，也可以用exe執行，簡單快速就可以demo，不須在平台上再安裝什麼，也不用管執行指令還要多設定main class等等，就點運行就對了！



### 缺點

#### 某些支援庫不足

在某些特定的協定或應用上，go往往出的比其他語言來的晚，所以隱含踩到的bug/issue都比較多....，所以在選用上要先比較支援庫是否夠成熟，星星數多不多，好不好用，不然真的會很悲劇...





### 結論

如果是常見的基本程式處理，用go去處理真的沒什麼不可，而且用過就回不去了！只是不太懂為什麼普遍企業用的並不多，java還是普遍大宗，（但自己就是看不懂java那複雜又難debug的結構？或許是個人問題ＸＤ沒有紮實地學好ˊˋ），但就如上述缺點所說，某些功能可能就無法用go去實現，這時又很麻煩，所以建議還是有在採用微服務的架構會比較好，就**可以根據不同服務的功能，去選用適合的語言去運行**！









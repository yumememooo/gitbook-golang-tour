---
description: 開發Go環境的安裝步驟，
---

# \[開始Go旅程] Install Go

### 步驟:

1.去官網下載msi安裝go&#x20;

確認安裝，開啟終端機輸入go version

```
>go version
go version go1.17.6 windows/amd64
```

2.下載IDE vscode \[個人習慣用IDE]

3.開啟vscode 安裝插件extension Go&#x20;

右下角會要求你安裝周邊的go tool。 會被安裝在 $GOPATH\bin下。

* 預設環境變數(Windows)

```
set GOBIN=
set GOPATH=C:\Users\<your name>\go
set GOROOT=C:\Program Files\Go 
set GOMODCACHE=C:\Users\<your name>\go\pkg\mod
PATH:=%USERPROFILE%\go\bin 
預設%USERPROFILE%就是C:\Users\<your name>
```

如果有執行過安裝Tool工具，就會發現C:\Users\xxx\go資料夾被新增，且內部還有bin/pkg的資料夾。



\--------------------------------------------------

#### 自己的放置習慣 (windows)-自行更改系統環境變數

```
GOPATH=D:\go
GOBIN=%GOPATH%\bin
PATH 加入%GOBIN% //要加這段，才可以執行執行工具安裝好的指令 

D:\go\src 程式碼區
D:\go\bin 安裝工具，資料夾會自動建立
D:\go\pkg 安裝相依庫，資料夾會自動建立。
```

> 其實也可以從下載資料夾直接安裝，相關的環境變數要設定好。

{% hint style="info" %}
開始寫個簡單的範例main.go

檢查autoimport或是autocompelte會不會運作，開發環境就完成了。

_<mark style="color:purple;">有的時候無法自動import可能只是func.name打錯字了=.=</mark>_
{% endhint %}

#### Bin資料夾被安裝的工具

![](../.gitbook/assets/bin\_tools.PNG)


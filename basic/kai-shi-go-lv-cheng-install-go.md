---
description: 開發Go環境的安裝步驟，
layout: editorial
---

# \[Start! ->] Install Go

### 安裝三步驟

1. 去官網下載msi安裝go&#x20;

確認安裝，開啟終端機輸入go version

```
>go version
go version go1.17.6 windows/amd64
```

安裝完後會有預設的環境變數，可以用自己習慣的環境變數更改．

2\. 下載IDE vscode \[個人習慣用IDE]

3\. 開啟vscode 安裝插件extension Go&#x20;

右下角會要求你安裝周邊的go tool。 會被安裝在 $GOPATH\bin下。



\=============================

#### 預設環境變數說明：

```
GOROOT // ＧＯ的安裝資料夾位置，之後要升級就改這個資料夾
GOBIN // 安裝的可執行檔
GOPATH //程式碼位置，建議更改到自己習慣的資料夾
```



### &#x20;(windows)-自行更改系統環境變數

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

自己的放置習慣

```
GOPATH=D:\go
GOBIN=%GOPATH%\bin
PATH 加入%GOBIN% //要加這段，才可以執行執行工具安裝好的指令 

D:\go\src 程式碼區
D:\go\bin 安裝工具，資料夾會自動建立
D:\go\pkg 安裝相依庫，資料夾會自動建立。
```



### (MAC)配置環境變數 <a href="#mac-an-zhuang-bi-ji" id="mac-an-zhuang-bi-ji"></a>

* vi \~/.bash\_profile

```
//輸入a編輯
export GOROOT="/usr/local/go"
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin 
export PATH=$PATH:$GOROOT/bin

//GOROOT表示GO安裝的目錄
//GOPATH是自訂想要放置程式的地方
//打完後esc輸入：wq存擋
```

* 執行 bash profile

```
source ~/.bash_profile
```





{% hint style="info" %}
開始寫個簡單的範例main.go

檢查autoimport或是autocompelte會不會運作，開發環境就完成了。

_<mark style="color:purple;">有的時候無法自動import可能只是func.name打錯字了=.=</mark>_
{% endhint %}

#### Bin資料夾被安裝的工具

```
D:\go\bin>dir /B
dlv-dap.exe
dlv.exe
go-outline.exe
goimports.exe
gomodifytags.exe
gopkgs.exe
goplay.exe
gopls.exe
gotests.exe
impl.exe
staticcheck.exe
```

#### 升版降版

通常我在win環境都是直接更換安裝目錄c:/go

程式面debug工具可能需要重新更換一下

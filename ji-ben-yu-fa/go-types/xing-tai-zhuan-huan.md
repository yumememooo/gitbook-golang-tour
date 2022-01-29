# 型態轉換

#### 自動類型轉換&#x20;

var myInt =123

#### 隱式整數類型轉換&#x20;

日常使用並不會感覺到 在Go中，變量之間沒有隱式類型轉換。但是，編譯器可以進行變量和常量之間的隱式類型轉換&#x20;

```
var myInt int = 123
var myInt int = 123.0
var myInt int = 123.1 
var myFloat float64 = 1var myFloat float64 = 1
```

#### &#x20;顯式轉換 強制轉換Type conversions&#x20;

The expression T(v) converts the value v to the type T.


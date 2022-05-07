---
description: Type convert 型態轉換
---

# Type convert

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

The expression <mark style="color:blue;">T(v)</mark> converts the value v to the type T.

```
func main() {
	var myInt8 int8 = 88
	myInt64 := int64(myInt8)
	fmt.Printf("Type: %T myInt64: %v\n", myInt64, myInt64)

	myInt8_2 := int8(myInt64)
	fmt.Printf("Type: %T myInt8_2: %v\n", myInt8_2, myInt8_2)

	var myInt8_3 int8 = -88
	myInt8_4 := uint8(myInt8_3)
	fmt.Printf("Type: %T myInt8_2: %v\n", myInt8_4, myInt8_4)
}
```

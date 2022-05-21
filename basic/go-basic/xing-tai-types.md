---
description: 基本型態介紹
---

# base Types

### 常量宣告

常量是一個簡單值的標識符，在程序運行時，不會被修改的量。

```
const identifier [type] = value
```

### 變量宣告

```
var 變量名 變量類型
var a, b *int//指针类型
```

#### new

* <mark style="background-color:red;">new 會並且返回儲存位址</mark> <mark style="background-color:red;"></mark><mark style="background-color:red;">**且**</mark><mark style="background-color:red;">自動用 zeroed value 來初始化型別</mark>
* 但要注意像是map/slice/chan等會是nil，直接使用可能會引發錯誤，通常會另外make來宣告使用。
* map/slice/chan 常用make宣告時就不會拿到指標，要拿到指標請用new

```
func main() {
	myInt := new(int)
	fmt.Println(myInt). //記憶體位置0xc00009c000
	fmt.Println(*myInt).  //初始值 0 
	fmt.Printf("%#v", myInt) //%#v 先输出结构体名字值，再输出结构体（字段名字+字段的值） (*int)(0xc00009c000)
}
```

* 使用new(struct)雖然可以快速初始化，但是無法一開始就給指定內容，因此常使用\&Struct{Field:xxx}來使用．

### 型態用法

* <mark style="color:blue;">值類型</mark>包括 int、float、bool、string、struct 以及數組(array)
* <mark style="color:blue;">引用類型</mark>包括指針(Pointer)、切片(slice)、map、通道(chan)&#x20;
* 可以透過fmt.Printf("Type: %T ", xx) 印出該類型的type
* 可以通過 math.MaxInt64、math.MinInt64 的方式得到預定義的某類型最大最小值。
* <mark style="background-color:yellow;"></mark>

### Zero values

* <mark style="color:blue;">**0**</mark> for numeric types
* <mark style="color:blue;">**false**</mark> for the boolean type
* <mark style="color:blue;">**""**</mark> (the empty string) for strings.
* <mark style="color:blue;">**nil**</mark> for Pointer/Interface/Slice/Map/Channel/Function

### Basic types

* 基本類型如下：

```
bool
string
int、int8、int16、int32、int64
uint、uint8、uint16、uint32、uint64、uintptr
byte // uint8 的别名
rune // int32 的别名 代表一个 Unicode 码
float32、float64
complex64、complex128
```

* 範圍與大小

| type                                                                   | Size                                                                         | range                                                                                                  |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| bool                                                                   | 8bit(1 byte)                                                                 | 0,1                                                                                                    |
| string                                                                 | 16bit (2 byte)                                                               | \*byte陣列的最大長度可以是65535(more)                                                                            |
| <p>//Signed Integers<br>//Unsigned Integers</p>                        |                                                                              |                                                                                                        |
| <p>int<br>uint<br>uintptr</p>                                          | <p>32 bits wide on 32-bit systems </p><p>64 bits wide on 64-bit systems.</p> |                                                                                                        |
| <p>int8<br>uint8<br>byte // alias for uint8</p>                        | <p>8bit (1 byte)<br>2的8次方=256</p>                                            | <p>-128 to 127<br>0 and 255 , binary:00000000~11111111 (8bit)</p>                                      |
| <p>int16<br>uint16</p>                                                 | <p>16bit<br>2的16次方=65536</p>                                                 | <p>-32,768 and 32,767<br>(-2的15次方 to 2的15次方-1 )<br>0 and 65535</p>                                     |
| <p>int32<br>rune // alias for int32 (Unicode code point)<br>uint16</p> | 32bit                                                                        | <p>-2,147,483,648 and 2,147,483,647.<br>#0 and 4,294,967,295</p>                                       |
| <p>int64<br>uint64</p>                                                 | 64bit (8 byte)                                                               | <p>#-9,223,372,036,854,775,808 and 9,223,372,036,854,775,807.<br>#0 and 18,446,744,073,709,551,615</p> |
| float32                                                                | 32bit (4 byte)                                                               | //1.401298464324817070923729583289916131280e-45 and 3.40282346638528859811704183484516925440e+38.      |
| float64                                                                | 64bit (8 byte)                                                               | //4.940656458412465441765687928682213723651e-324 and 1.797693134862315708145274237317043567981e+308.   |
| complex64                                                              | 64bit (8 byte)                                                               |                                                                                                        |
| complex128                                                             | 128bit (16 byte)                                                             |                                                                                                        |





###

#### 參考

* go範例程式與範圍: [https://www.callicoder.com/golang-basic-types-operators-type-conversion/](https://www.callicoder.com/golang-basic-types-operators-type-conversion/)

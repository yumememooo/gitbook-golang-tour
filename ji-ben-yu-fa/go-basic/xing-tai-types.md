---
description: 基本型態介紹
---

# 型態 Types

### 型態用法

* 值類型包括 int、float、bool、string、struct 以及數組(array)
* 引用類型包括指針(Pointer)、切片(slice)、map、通道(chan)&#x20;
* 可以透過fmt.Printf("Type: %T ", xx) 印出該類型的type
* 可以通過 math.MaxInt64、math.MinInt64 的方式得到預定義的某類型最大最小值。
* new 會自動用 zeroed value 來初始化型別，但要注意像是map/slice/chan等會是nil。

### Zero values

* <mark style="color:blue;">**0**</mark> for numeric types
* <mark style="color:blue;">**false**</mark> for the boolean type
* <mark style="color:blue;">**""**</mark> (the empty string) for strings.
* <mark style="color:blue;">**nil**</mark> for Pointer/Interface/Slice/Map/Channel/Function

### Basic types

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

---
description: 基本型態介紹
---

# 型態 Types

###

* 值類型包括 int、float、bool、string、struct 以及數組&#x20;
* 引用類型包括指針、切片、map、chan（通道）&#x20;
* 可以透過fmt.Printf("Type: %T ", xx) 印出該類型的type
* 可以通過 math.MaxInt64、math.MinInt64 的方式得到預定義的某類型最大最小值。

### Basic types

| type                                                                   | Size                                                                         | range                                                                                                  |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| bool                                                                   |                                                                              |                                                                                                        |
| string                                                                 |                                                                              |                                                                                                        |
| <p>//Signed Integers<br>//Unsigned Integers</p>                        |                                                                              |                                                                                                        |
| <p>int<br>uint<br>uintptr</p>                                          | <p>32 bits wide on 32-bit systems </p><p>64 bits wide on 64-bit systems.</p> |                                                                                                        |
| <p>int8<br>uint8<br>byte // alias for uint8</p>                        | <p>8bit<br>2的8次方=256</p>                                                     | <p>-128 to 127<br>0 and 255 , binary:00000000~11111111 (8bit)</p>                                      |
| <p>int16<br>uint16</p>                                                 | <p>16bit<br>2的16次方=65536</p>                                                 | <p>-32,768 and 32,767<br>(-2的15次方 to 2的15次方-1 )<br>0 and 65535</p>                                     |
| <p>int32<br>rune // alias for int32 (Unicode code point)<br>uint16</p> | 32bit                                                                        | <p>-2,147,483,648 and 2,147,483,647.<br>#0 and 4,294,967,295</p>                                       |
| <p>int64<br>uint64</p>                                                 | 64bit                                                                        | <p>#-9,223,372,036,854,775,808 and 9,223,372,036,854,775,807.<br>#0 and 18,446,744,073,709,551,615</p> |
| float32                                                                |                                                                              | //1.401298464324817070923729583289916131280e-45 and 3.40282346638528859811704183484516925440e+38.      |
| float64                                                                |                                                                              | //4.940656458412465441765687928682213723651e-324 and 1.797693134862315708145274237317043567981e+308.   |
| complex64                                                              |                                                                              |                                                                                                        |
| complex128                                                             |                                                                              |                                                                                                        |

*





### Zero values

* <mark style="color:blue;">**0**</mark> for numeric types,&#x20;
* <mark style="color:blue;">**false**</mark> for the boolean type
* <mark style="color:blue;">**""**</mark> (the empty string) for strings.

#### 參考

* go範例程式與範圍: [https://www.callicoder.com/golang-basic-types-operators-type-conversion/](https://www.callicoder.com/golang-basic-types-operators-type-conversion/)

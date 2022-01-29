# GO types

### Basic types

```
bool
string
//Signed Integers
int   
int8   Size:8bit, Range: -128 to 127
int16  Size:16bit,Range:-2的15次方 to 2的15次方-1 //-32,768 and 32,767
int32  Size:32bit,Range: -2,147,483,648 and 2,147,483,647.
int64  Size:64bit,Range:-9,223,372,036,854,775,808 and 9,223,372,036,854,775,807.
//Unsigned Integers
uint 
uint8   Size:8bit,,Range:0 and 255 , binary:11111111
uint16  Size:16bit,Range:0 and 65535
uint32  Size:32bit,Range:0 and 4,294,967,295
uint64  Size:64bit,Range:0 and 18,446,744,073,709,551,615

uintptr

byte // alias for uint8
rune // alias for int32// represents a Unicode code point

float32  //1.401298464324817070923729583289916131280e-45 and 3.40282346638528859811704183484516925440e+38.
float64  //4.940656458412465441765687928682213723651e-324 and 1.797693134862315708145274237317043567981e+308.

complex64 complex128
```

* 值類型包括 int、float、bool、string、struct 以及數組&#x20;
* 引用類型包括指針、切片、map、chan（通道）&#x20;
* The `int`, `uint`, and `uintptr` types are usually 32 bits wide on 32-bit systems and 64 bits wide on 64-bit systems.

可以透過fmt.Printf("Type: %T ", xx) 印出該類型的type

可以通過 math.MaxInt64、math.MinInt64 的方式得到預定義的某類型最大最小值。





### Zero values

* <mark style="color:blue;">**0**</mark> for numeric types,&#x20;
* <mark style="color:blue;">**false**</mark> for the boolean type
* <mark style="color:blue;">**""**</mark> (the empty string) for strings.

#### 參考

* go範例程式與範圍: [https://www.callicoder.com/golang-basic-types-operators-type-conversion/](https://www.callicoder.com/golang-basic-types-operators-type-conversion/)
* 數字type範圍[https://ado.xyz/blog/go-numerical-type-ranges/](https://ado.xyz/blog/go-numerical-type-ranges/)

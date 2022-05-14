---
description: Type convert 型態轉換
---

# Type convert

### 自動類型轉換&#x20;

```
顯式類型定義： const b string = "abc"
隱式類型定義： const b = "abc"

var myInt = 123
fmt.Printf("%T %v \n", myInt, myInt) //自動類型轉換 int 123 
```

### 隱式整數類型轉換&#x20;

使用並不會感覺到，變量之間沒有隱式類型轉換。但是編譯器可以進行變量和常量之間的隱式類型轉換&#x20;

```
package main

import "fmt"

func main() {

	var myInt1 int = 123 //將常量 123 的整數型別隱式轉換為 int 型別的值
	var myInt2 int = 123.0 //將浮點型別的常量隱式轉換為整數變數
	//var myInt3 int = 123.1//這樣是不行的 cannot use 123.1 (untyped float constant) as int value in variable declaration (truncated) compiler TruncatedFloat
	var myFloat1 float64 = 1 //在整數型別的常量到 float64 型別的變數之間執行隱式轉換

	fmt.Printf("%T %v \n", myInt1, myInt1)//int 123 
	fmt.Printf("%T %v \n", myInt2, myInt2)//int 123 
	fmt.Printf("%T %v \n", myFloat1, myFloat1)//float64 1 
}

```

### 強制轉換 <mark style="color:blue;">T(v)</mark> Type conversions &#x20;

* 又稱顯式（explicitly）轉換
* The expression <mark style="color:blue;">T(v)</mark> converts the value v to the type T.
* 相同結構struct（忽略struct tag）也可以互轉 . &#x20;
  * see [https://tip.golang.org/doc/go1.8#language](https://tip.golang.org/doc/go1.8#language)

```
type User struct {
	Name string
}

type UserStru2 struct {
	Name string
}

func main() {
	var myInt8 int8 = 88
	myInt64 := int64(myInt8)
	fmt.Printf("Type: %T myInt64: %v\n", myInt64, myInt64)

	myInt8_2 := int8(myInt64)
	fmt.Printf("Type: %T myInt8_2: %v\n", myInt8_2, myInt8_2)

	var myInt8_3 int8 = -88
	myInt8_4 := uint8(myInt8_3)
	fmt.Printf("Type: %T myInt8_2: %v\n", myInt8_4, myInt8_4)
	
	user1 := User{Name: "test"}
	fmt.Printf("%T %v \n", user1, user1) //main.User {test}
	user2 := User(UserStru2{Name: "test"}) //T(v)
	fmt.Printf("%T %v \n", user2, user2)//main.User {test}
}
```

### 斷言轉換 x.(T) Type assertions

see [https://go.dev/ref/spec#Type\_assertions](https://go.dev/ref/spec#Type\_assertions)

斷言通過判斷變量是否可以轉換成某一個類型

```
var s = x.(T)
```

如果斷言類型成立，則表達式返回值就是T 類型的x，如果斷言失敗就會觸發panic。

```
s, ok := x.(T)
```

是ok 會返回是否斷言成功不會出現panic，ok 就表示是否是成功了。

#### switch 的斷言方法

go 語法種還提供了另外一種類型switch 的斷言方法。

```
switch i := x.(type) {
case nil:
    print("x is nil")                
case int:
    print(i)                            
case float64:
    print(i)                        
case func(int) float64:
    printFunction(i)                       
case bool, string:
    print("type is bool or string")  
default:
    print("unknown type")     
}

```

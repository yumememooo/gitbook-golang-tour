# array/slice/map 宣告

### 陣列`Array`

* 陣列在初始化時必須指定大小
* 陣列為**按值傳遞**的，函式內對陣列的值的改變不影響初始陣列
* 陣列作為函式引數時，必須指定引數陣列的大小，且傳入的陣列大小必須與指定的大小一致
* 不可以使用append

```
var arr1 [5]int 
//聲明大小為5的陣列，預設初始值為[0,0,0,0,0]

arr2 := [5]int{1} 
//宣告並初始化了一個大小為5的陣列的第一個元素，初始化後值為[1,0,0,0,0]

arr3 := [...]int{1, 2, 3} 
//通過...自動獲取陣列長度，根據初始化的值的數量將大小初始化為3，初始化後值為[1,2,3]

arr4 := [...]int{4: 1} 
//指定序號為4的元素的值為1，通過...自動獲取長度為5，初始化後值為[0,0,0,0,1]
```

### 切片 `slice`

* 一種資料型別，從概念上說是一個結構體。可以理解為**動態長度**的陣列
* 傳遞時為**按引用傳遞**的，函式內對slice內元素的修改將導致函式外的值也發生改變

宣告

```
s1 := []int{1,2,3}	
//通過陣列的引用初始化，值為[1,2,3],長度和容量為3

arr := [5]int{1,2,3,4,5}
s2 := arr[0:3]	
//通過陣列的切片初始化，值為[1,2,3]，長度為3，容量為5

s3 := make([]int, 3)	
//通過make函式初始化，值為[0,0,0]，長度和容量為3

s4 := make([]int, 3, 5)	
//通過make函式初始化，值為[0,0,0]，長度為3，容量為5
```

### 映射 `MAP`

`宣告`

* 使用var m map\[string]int 可以宣告一個nil的map，<mark style="color:red;">需注意未初始化就塞值會引發panic</mark>
* **使用內建的 `make()` 函數初始化 map，**該函數將返回已初始化及可以使用的 map。
  * 或是var map\[string]int{}可以透過將大括號留空，建立一個空 map
* 傳遞時為**按引用傳遞**的，對元素的修改將導致函式外的值也發生改變

```

import "fmt"

func main() {
	var m map[string]int //語法宣告 map ///map 的零值是 nil
	fmt.Println(m)
	if m == nil {
		fmt.Println("m is nil")
	}
	// m["one hundred"] = 100 //panic: assignment to entry in nil map

	var m2 = make(map[string]int) //使用內建的 make() 函數初始化 map

	fmt.Println(m2)

	if m2 == nil {
		fmt.Println("m2 is nil")
	} else {
		fmt.Println("m2 is not nil")
	}

	m2["one hundred"] = 100
	fmt.Println(m2)

	var m3 = map[string]int{} //可以透過將大括號留空，使用 map 定數來建立一個空 map
	if m3 == nil {
		fmt.Println("m3 is nil")
	} else {
		fmt.Println("m3 is not nil")
	}
	m3["one hundred"] = 100
	fmt.Println(m3)
}


```

#### Map literals

Map literals are like struct literals, but the keys are required.



```go
package main

import "fmt"

type Vertex struct {
	Lat, Long float64
}

var m = map[string]Vertex{
	"Bell Labs": Vertex{
		40.68433, -74.39967,
	},
	"Google": Vertex{
		37.42202, -122.08408,
	},
}

func main() {
	fmt.Println(m)
}

```



#### 參考網址

Map from [https://go.dev/tour/moretypes/20](https://go.dev/tour/moretypes/20)

使用陣列 (Array) 和切片 (Slice)\
[https://opensourcedoc.com/golang-programming/array-slice/](https://opensourcedoc.com/golang-programming/array-slice/)

Go語言Array和Slice的區別\
[https://www.gushiciku.cn/pl/gWSH/zh-tw](https://www.gushiciku.cn/pl/gWSH/zh-tw)

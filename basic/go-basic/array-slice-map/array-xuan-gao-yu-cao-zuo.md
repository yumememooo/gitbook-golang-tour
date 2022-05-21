# array 宣告與操作

#### 陣列`Array 宣告` <a href="#die-dai-map" id="die-dai-map"></a>

* 陣列在初始化時必須指定大小，<mark style="color:red;">\[...]也是指定大小的意思</mark>
* 陣列為<mark style="color:red;">**按值傳遞**</mark>的，函式內對陣列的值的改變不影響初始陣列
* 陣列作為函式引數時，必須指定引數陣列的大小，且傳入的陣列大小必須與指定的大小一致
* <mark style="color:red;">不可以使用append</mark>

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

### &#x20;

#### 走訪array <a href="#die-dai-map" id="die-dai-map"></a>

* <mark style="color:red;">注意不可以直接在range中修改元素</mark>，若要修改陣列中的元素，要以索引走訪陣列，再修改陣列的元素的值(跟slice一樣)

```
package main

import "fmt"

func ModifyArray(arr [5]int) {
	arr[0] = 5
	fmt.Println(arr) // [5,0,0,0,1]
}

func main() {
	a := [...]int{4: 1} //陣列為按值傳遞的，函式內對陣列的值的改變不影響初始陣列
	ModifyArray(a)
	fmt.Println(a) // [0,0,0,0,1]
	b := a
	b[0] = 88
	fmt.Println("b:", b) //修改b也不會影響到b
	fmt.Println("a:", a)

	fmt.Println("mo arr")
	arr := [5]int{1, 2, 3, 4, 5}

	for i, e := range arr {
		fmt.Println(fmt.Sprintf("%d: %d", i+1, e))
		e = e * e //不可以使用range中修改元素
	}
	fmt.Println(arr)

	for i := 0; i < len(arr); i++ {
		arr[i] = arr[i] * arr[i] //若要修改陣列中的元素，要以索引走訪陣列，再修改陣列的元素的值
	}
	fmt.Println(arr)
	//arr = append(arr, 1)//invalid argument: arr (variable of type [5]int) is not a slice
}

```

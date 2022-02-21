# slice 宣告與操作

####

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

#### 新增元素:動態改變slice大小

切片長度可以動態改變，這時候會使用 `append` 函式

沒有移除元素的函式，但可以用一些技巧移掉某一個元素

```
slice = append(slice, 6, 7, 8)
// Remove the 3rd element.
slice = append(slice[0:2], slice[3:5]...)
```

#### 走訪array <a href="#die-dai-map" id="die-dai-map"></a>

* 注意不可以直接在range中修改元素，若要修改中的元素，要以修改陣列的元素的值
* 傳遞時為**按引用傳遞**的

```
package main

import (
	"fmt"
)

func modifySlice(s []string) {
	s[3] = "PHP_M"
}

func main() {
	langs := []string{"Go", "Python", "Ruby", "PHP"}

	s2 := langs
	s2[1] = "NA"
	fmt.Printf("angs: %v\n", langs) //[Go NA Ruby PHP]
	fmt.Printf("s2: %v\n", s2)      //按引用傳遞的 改變s2也會改變
	fmt.Print("-----modifySlice------\n")

	modifySlice(langs)
	fmt.Printf("angs: %v\n", langs)
	fmt.Printf("s2: %v\n", s2)

	fmt.Print("-----range------\n")
	for _, e := range langs {
		e = e + "xxx" //這樣改無效
		fmt.Println(e)
	}
	fmt.Printf("angs: %v\n", langs)
	for i, e := range langs {
		langs[i] = e + "iiii" //要用index改
		fmt.Println(e)
	}
	fmt.Printf("angs: %v\n", langs)
	for i := 0; i < len(langs); i++ {
		langs[i] = langs[i] + "xxxx"
	}
	fmt.Printf("angs: %v\n", langs)

}

```

# \[pkg]fmt包

### fmt

完整文件：[https://pkg.go.dev/fmt](https://pkg.go.dev/fmt)



#### %v %+v %#v

> %v the value in a default format when printing structs, the plus flag (%+v) adds field names
>
> %v會簡單印出內容值，但%+v會印欄位名
>
> %#v a Go-syntax representation of the value
>
> 會印結構名

* 範例：

這邊可以看到前兩者欄位之間還會有空白

```
package main

import "fmt"

type student struct {
	name string
	age  int
}

func main() {
	s := &student{"lili", 12}
	fmt.Printf("%%v的方式  = %v\n", s)  //&{lili 12}
	fmt.Printf("%%+v的方式 = %+v\n", s) //&{name:lili age:12}
	fmt.Printf("%%#v的方式 = %#v\n", s) //&main.student{name:"lili", age:12}

	s2 := student{"amy", 12}
	fmt.Printf("%%v的方式  = %v\n", s2)  //{amy 12}
	fmt.Printf("%%+v的方式 = %+v\n", s2) //{name:amy age:12}
	fmt.Printf("%%#v的方式 = %#v\n", s2) //main.student{name:"amy", age:12}
	
	
}

```

延伸

* \[关于fmt包Fprint系列方法的性能问题]\([https://blog.csdn.net/FishGoddess/article/details/104809139](https://blog.csdn.net/FishGoddess/article/details/104809139))

# map 操作

#### 加入鍵值到 map <a href="#jia-ru-xiang-mu-jian-zhi-dui-dao-map" id="jia-ru-xiang-mu-jian-zhi-dui-dao-map"></a>

```go
m[key] = value
```

#### 從 map 中刪除鍵 <a href="#cong-map-zhong-shan-chu-jian" id="cong-map-zhong-shan-chu-jian"></a>

`delete()` 函數不會返回任何值。另外，如果該鍵不存在於 map，它也不會執行任何操作。&#x20;

```go
delete(map, key)
```

**檢查鍵是否存在於 map**

```go
value, ok := m[key]
```

#### 迭代 map <a href="#die-dai-map" id="die-dai-map"></a>

* map 是沒有順序的集合，不能保證 map 的迭代順序都相同。

```
for key, value:= range m{
}
```

#### map 是參考型別 <a href="#map-shi-can-kao-xing-bie" id="map-shi-can-kao-xing-bie"></a>

當你將 map 分派給新變數時，它們都參考相同的底層資料結構



範例:

```
package main

import "fmt"

func main() {
	var personAgeMap1 = map[string]int{
		"Apple": 25,
		"James": 32,
		"Sarah": 29,
	}
	age, ok := personAgeMap1["Apple"]
	fmt.Println("age:", age, ",ok", ok)

	var m2 = personAgeMap1 //，它們都參考相同的底層資料結構
	fmt.Println("--ori.---")
	fmt.Println("personAgeMap1 = ", personAgeMap1)
	fmt.Println("m2 = ", m2)
	fmt.Println("-modify personAgeMap1=18----")
	for name, age := range personAgeMap1 {
		fmt.Println(name, age)
		personAgeMap1[name] = 18
	}

	fmt.Println("personAgeMap1 = ", personAgeMap1)
	fmt.Println("m2 = ", m2)
	fmt.Println("-modify add m2["Amy"] = 10----")
	m2["Amy"] = 10
	fmt.Println("personAge = ", personAgeMap1)
	fmt.Println("m2 = ", m2)
	fmt.Println("--modifymap(personAgeMap1)---")
	modifymap(personAgeMap1)
	fmt.Println("personAge = ", personAgeMap1)
	fmt.Println("m2 = ", m2)
	
}

func modifymap(personAge map[string]int) {
	for name := range personAge {
		personAge[name] = 20
	}
	delete(personAge, "Apple")
}

```

結果:

```
age: 25 ,ok true
--ori.---
personAgeMap1 =  map[Apple:25 James:32 Sarah:29]
m2 =  map[Apple:25 James:32 Sarah:29]
-modify personAgeMap1=18----
Apple 25
James 32
Sarah 29
personAgeMap1 =  map[Apple:18 James:18 Sarah:18]
m2 =  map[Apple:18 James:18 Sarah:18]
-modify add m2[Amy] = 10----
personAge =  map[Amy:10 Apple:18 James:18 Sarah:18]
m2 =  map[Amy:10 Apple:18 James:18 Sarah:18]
--modifymap(personAgeMap1)---
personAge =  map[Amy:20 James:20 Sarah:20]
m2 =  map[Amy:20 James:20 Sarah:20]
```

# struct tag

Struct是由一组field组成，每个field屬性包括了命名和類型，Field可以像f3和f4公用一个類型

### struct tag

* 有時候會在字段定義後面带上一个字符串(tag)，Tags可以由鍵值對组成，空格用來分割鍵值對
* Tag可以使用reflection包來讀取，並可以通過Lookup(建議)或者Get來獲取鍵值對的值。
* 什麼時候用到了Tag? ex json(Un)marshaling/ORM/go vet可以檢查出你的tag是否合理等等都有利用到tag來做解析。

```

import (
	"encoding/json"
	"fmt"
	"reflect"
)
type T struct {
	f1     string "f one"
	f2     string
	f3     string `f three 123`
	f4, f5 int64  `one:"1" two:"2"blank:""`
	Name   string `json:"name"` //注意要大寫開頭命名
	na     int    `json:"na"` //小寫開頭命名json會被丟棄
}
func main() {
	t := reflect.TypeOf(T{})
	f1, _ := t.FieldByName("f1")
	fmt.Println(f1.Tag) // f one
	f4, _ := t.FieldByName("f4")
	fmt.Println(f4.Tag) // one:"1" two:"2"blank:""
	f5, _ := t.FieldByName("f5")
	fmt.Println(f5.Tag) // one:"1" two:"2"blank:"" 共用 同上
	v, ok := f5.Tag.Lookup("one")
	fmt.Printf("%s, %t\n", v, ok) //1, true

	tt := T{"1", "0", "2", 3, 6, "kiki", 6}
	b, err := json.Marshal(tt)
	if err != nil {
		panic(err)
	}
	fmt.Printf("%s\n", b) //{"name":"kiki"} 只有json tag會被解析出來

	
}

```

#### json/bson/swagger 用到的範例

參考:[https://github.com/swaggo/swag](https://github.com/swaggo/swag)

```
type Who struct {
	Id        primitive.ObjectID `json:"id" bson:"_id,omitempty"` //mongo ObjectId
	Sub      `bson:",inline"`    // inline stored in mongo
	Docs string `json:"docs,omitempty"`
	Name       string   `json:"name" bson:"name" example:"mira"`
 IsActive *bool `json:"isActive,omitempty"`
}
type Sub struct {
	Name       string   `json:"name" bson:"name" example:"name"`
	Labels      []string `json:"labels" bson:"labels" example:"123"`
	Description string   `json:"description"  bson:"description" example:"1234567"`
 Bar string `minLength:"4" maxLength:"16"`
 Baz int `minimum:"10" maximum:"20" default:"15"`
  Qux []string `enums:"foo,bar,baz"`
}
```

#### 參考及延伸文章:

Golang的Tag语法https://studygolang.com/articles/14469

自訂golang如何使用struct的tag屬性 //https://www.gushiciku.cn/pl/2xWn/zh-tw

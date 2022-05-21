# json

### json Marshel

* 返回 v 的 JSON 编码&#x20;
* supported type See \[json/encode]\([https://github.com/golang/go/blob/master/src/encoding/json/encode.go](https://github.com/golang/go/blob/master/src/encoding/json/encode.go))
* 將struct 轉成 json string
* struct tag : field要大寫開頭，tag各有其功用
* Marshel如果字串含有HTML特殊字元會被轉換，如果不想要被轉換需要自己將EscapeHTML設為false

<details>

<summary>[線上範例](<a href="https://go.dev/play/p/GL8zgnPMKpv">https://go.dev/play/p/GL8zgnPMKpv</a>)</summary>

```go
package main

import (
"bytes"
"encoding/json"
"fmt"
)

//field要大寫開頭，tag各有其功用
type UserDetail struct {
Name string `json:"name"`
NickName string `json:"nick_name,omitempty"` // Field appears in JSON as key "myName" and the field is omitted from the object if its value is empty,
Address string `json:",omitempty"` //Field appears in JSON as key "Field" (大寫), but the field is skipped if empty.
A string `json:"-"` // Field is ignored by this package.
B string `json:"-,"` // Field appears in JSON as key "-".
AgeString int64 `json:"AgeString,string"` //將輸出轉為string
Age int64 `json:"Age"`
}
type User struct {
Name string `json:"name"`
}

func main() {
user1 := UserDetail{Name: "123", NickName: "123", Address: "123", A: "A", B: "B", AgeString: 123, Age: 12}
jsonMarshal(user1) //-> json str: {"name":"123","my_name":"123","MyName2":"123","-":"B","int64string":"123","int64":123}

value := make(chan int) //unsupportedTypeEncoder #ref1
jsonMarshal(value) //->Marshal err: json: unsupported type: chan int json str:

user2 := User{Name: "<h1>123</h1>"}
jsonMarshal(user2) //->json str: json str: {"name":"\u003ch1\u003e123\u003c/h1\u003e"}
JsonMarshalEscapeHTMLfalse(user2) ->json str: {"name":"<h1>123</h1>"}
}

//struct to json string
func jsonMarshal(u interface{}) {
ub, err := json.Marshal(u)
if err != nil {
fmt.Println("Marshal err:", err)
}
fmt.Println("json str:", string(ub))
}

func JsonMarshalEscapeHTMLfalse(u interface{}) {
ub, err := JsonEscapeHTMLfalse(u)
if err != nil {
fmt.Println("JsonEscapeHTMLfalse err:", err)
}
fmt.Println("json str:", string(ub))
}

func JsonEscapeHTMLfalse(t interface{}) ([]byte, error) {
buffer := &bytes.Buffer{}
encoder := json.NewEncoder(buffer)
encoder.SetEscapeHTML(false)
err := encoder.Encode(t)
return buffer.Bytes(), err
}
o
```

</details>

### &#x20;json.Unmarshal

* 將json string轉為struct，需了解傳送過來json的結構, 利用type struct 去定義好之後再進行解析
* 利用 \`map\[string]interface{}\`轉換，但想要取資料解析後比較麻煩，不像是知道結構方便
* 可以用map取第一層，下一層需reflect，下下層也是...或是利用斷言
* 僅僅需要將某字串格式化可用

<details>

<summary> (ex1):<a href="https://go.dev/play/p/kFzxUGvoDNJ">https://go.dev/play/p/kFzxUGvoDNJ</a></summary>

```
package main

import (
"encoding/json"
"fmt"
)

type User struct {
Name string `json:"name"`
Age int64 `json:"Age"`
Detail Detail `json:"detail"`
}

type Detail struct {
Address string `json:"address"`
}

func main() {
s := `{"name": "123",
"age": 23,
"detail": {
"Address": "abd"
}
}`

var d2 User //定義已知結構
if err := json.Unmarshal([]byte(s), &d2); err != nil {
fmt.Println(err)
}
fmt.Println(d2)
fmt.Println(d2.Detail.Address) //可以很輕鬆拿到內容

}
```

</details>

#### json.Compact

如果json string是beautify JSON String，json.Compact可以做壓縮。

<details>

<summary>範例</summary>

```go
/func main() {
s := `{"name": "123",
"age": 23,
"detail": {
"Address": "abd"
}
}` //json字串是 beautify JSON String

minfy := compactJSON([]byte(s))
fmt.Println(string(minfy))

}

//json.Compact
func compactJSON(js []byte) []byte {
buf := new(bytes.Buffer)
if err := json.Compact(buf, js); err != nil {
fmt.Println(err)
return nil
}
return buf.Bytes()
}

```

</details>

#### 轉換練習

* JSON String to String, string to JSON String
* [https://go.dev/play/p/04-7p4anrQk](https://go.dev/play/p/04-7p4anrQk)
* beautify JSON String to String, string to JSON String
* [https://go.dev/play/p/ySUIE73ls23](https://go.dev/play/p/ySUIE73ls23)\
  \


#### reference

* ref1: json.Marshal types
  * \[What input will cause golang's json.Marshal to return an error?]\(https://stackoverflow.com/questions/33903552/what-input-will-cause-golangs-json-marshal-to-return-an-error)
* \[Golang JSON 處理]\([https://blog.dexiang.me/zh-tw/technologies/golang-json/](https://blog.dexiang.me/zh-tw/technologies/golang-json/))
* struct tag 還可以有以下功能
* \[Golang中的读写数据（下）--JSON数据的编码与解码（筑基三层）]\([https://www.icodebang.com/article/252820](https://www.icodebang.com/article/252820))
* printJson(key string, value interface{})
* Ｇolang — json Unmarshal 轉換碰上type interface {} does not support indexing]\(https://sam66.medium.com/%EF%BD%87olang-json-unmarshal-%E8%BD%89%E6%8F%9B%E7%A2%B0%E4%B8%8Atype-interface-does-not-support-indexing-48e6b03aa7c1)
* &#x20;\[还在用 map\[string]interface{} 处理 JSON？告诉你一个更高效的方法——jsonvalue]\(https://segmentfault.com/a/1190000023564781)\
  \

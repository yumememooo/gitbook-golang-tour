# ERROR介面

Go除以錯誤可以分一般錯誤error與嚴重錯誤panic

### 錯誤介面 <a href="#cuo-wu-jie-mian" id="cuo-wu-jie-mian"></a>

如果想實作自己的錯誤物件，Go 提供一個公開介面，只要符合該介面的要求即可。

```
type error interface {
    Error() string
}
```

#### 可用套件回覆：

* &#x20;`errors` package 提供的 `errors.New()` 來產生錯誤訊息
* `fmt.Errorf()`為Go的標準函式庫，可產生帶格式化錯誤訊息的`error`。
* `errors.Errorf()`為第三方函式庫，可產生帶格式化錯誤訊息及stack trace紀錄的`error`。

例如下面使用`%+v`符號可印出`errors.Errorf()`的stack trace訊息。

```
package main

import (
	"fmt"

	"github.com/pkg/errors"
)

func main() {
	err := errors.New("建立錯誤訊息")
	print(err)
	printErr(err)
	fmt.Printf("--------\n")

	err1 := errors.Errorf("格式化錯誤訊息 %d", 10)
	print(err1)
	printErr(err1)

	fmt.Printf("--------\n")
	err2 := fmt.Errorf("格式化錯誤訊息  %d", 100)
	print(err2)
	printErr(err2)
}

func print(err error) {
	fmt.Printf("%s\n", err.Error())
}

func printErr(err error) {
	fmt.Printf("%+v\n", err)
}

```



#### 自定義錯誤介面

* 可以自定義錯誤介面內容，來定義更多錯誤資訊．
* 拿到錯誤時，先斷言判斷是否是自己定義的錯誤來拿到自定義的內容，就不用會只拿到錯誤字串而已．

```
type DefinedError interface {
	Error() string
	Code() int
}

type definedError struct {
	code    int
	message string
}

func newDefinedError(code int, message string) error {
	return &definedError{code: code, message: message}
}

func (e *definedError) Code() int {
	return e.code
}

func (e *definedError) Error() string {
	return e.message
}

------------------------------

使用
func xxx() error{
	err := newDefinedError(http.StatusNotFound, "description")
	return err
}

判斷

if IErr, ok := err.(DefinedError); ok {  //這邊用到轉型的概念，可以做為判斷
	router.ErrResponse(c, IErr.Code(), IErr)
	return
}
```

#### reference

* #### fmt.Errorf() 與 github.com/pkg/errors.Errorf() 區別
* [https://matthung0807.blogspot.com/2021/09/go-fmt-errorf-errors-errorf-difference.html](https://matthung0807.blogspot.com/2021/09/go-fmt-errorf-errors-errorf-difference.html)

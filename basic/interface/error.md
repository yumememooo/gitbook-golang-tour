# ERROR介面

Go除以錯誤可以分一般錯誤error與嚴重錯誤panic

### 錯誤介面 <a href="#cuo-wu-jie-mian" id="cuo-wu-jie-mian"></a>

如果想實作自己的錯誤物件，Go 提供一個公開介面，只要符合該介面的要求即可。

```
type error interface {
    Error() string
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

# Gin+swagger

### 範例程式碼

[lib\_framwork/gin](https://github.com/yumememooo/go-my-playground/tree/main/2.\_advance/lib\_framwork/gin)

### 參考

#### Gin 教學

Gin - 好用的 web framework https://ithelp.ithome.com.tw/articles/10234075

#### 中間件

```
如果沒特別處理，一般就會顯示 not found string預設顯示
r.NoMethod(HandleNotFound)
r.NoRoute(HandleNotFound)
```



#### 建立swagger

https://github.com/gin-gonic/gin

https://github.com/swaggo/gin-swagger

swag tool install https://github.com/swaggo/swag

安裝完工具後下swag version就會出現版本

下swag init就會根據註解產生對應的file

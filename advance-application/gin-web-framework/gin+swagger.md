# Gin+swagger

### Gin 教學

Gin - 好用的 web framework https://ithelp.ithome.com.tw/articles/10234075

#### 中間件

```
如果沒特別處理，一般就會顯示 not found string預設顯示
r.NoMethod(HandleNotFound)
r.NoRoute(HandleNotFound)
```

#### Setting up Route Not Found in Gin

[https://stackoverflow.com/questions/32443738/setting-up-route-not-found-in-gin](https://stackoverflow.com/questions/32443738/setting-up-route-not-found-in-gin)

#### rate limiter <a href="#rate-limiter" id="rate-limiter"></a>

希望API不要被特定節點頻繁存取以致於造成伺服器端的過載

{% embed url="https://blog.jln.co/Rate-limit-with-Go-and-Gin/" %}

<details>

<summary>範例程式碼<a href="https://github.com/yumememooo/go-my-playground/tree/main/2._advance/lib_framwork/gin">b_framwork/gin</a></summary>



</details>

### 建立swagger

https://github.com/gin-gonic/gin

https://github.com/swaggo/gin-swagger

swag tool install https://github.com/swaggo/swag

安裝完工具後下swag version就會出現版本

下swag init就會根據註解產生對應的file

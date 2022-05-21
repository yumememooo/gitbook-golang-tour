# Table of contents

* [🌸 About Golang Tour](README.md)

## basic

* [why Go ?](basic/go-intro..md)
* [\[Start! ->\] Install Go](basic/kai-shi-go-lv-cheng-install-go.md)
* [Go Module](basic/go-module.md)
* [GO basic](basic/go-basic/README.md)
  * [base Types](basic/go-basic/xing-tai-types.md)
  * [Type convert](basic/go-basic/xing-tai-zhuan-huan-type-convert.md)
  * [array/slice/map](basic/go-basic/array-slice-map/README.md)
    * [array 宣告與操作](basic/go-basic/array-slice-map/array-xuan-gao-yu-cao-zuo.md)
    * [slice 宣告與操作](basic/go-basic/array-slice-map/slice-xuan-gao-yu-cao-zuo.md)
    * [map 宣告與操作](basic/go-basic/array-slice-map/map-xuan-gao-yu-cao-zuo.md)
  * [struct](basic/go-basic/struct.md)
  * [struct tag](basic/go-basic/struct-tag.md)
  * [Reflection](basic/go-basic/reflection.md)
  * [unsafe.Sizeof](basic/go-basic/unsafe.sizeof.md)
  * [參考文章](basic/go-basic/can-kao-wen-zhang.md)
* [interface](basic/interface/README.md)
  * [空的接口，interface{}](basic/interface/kong-de-jie-kou-interface.md)
  * [用interfce定義行為](basic/interface/yong-interfce-ding-yi-hang-wei.md)
  * [ERROR介面](basic/interface/error.md)
* [Goroutine](basic/goroutine/README.md)
  * [創建Goroutine](basic/goroutine/chuang-jian-goroutine.md)
    * [for循環+goroutine的坑](basic/goroutine/chuang-jian-goroutine/for-xun-huan-+goroutine-de-keng.md)
    * [deadlock問題](basic/goroutine/chuang-jian-goroutine/deadlock-wen-ti.md)
  * [資料競爭 data race](basic/goroutine/zi-liao-jing-zheng-data-race.md)
  * [互斥鎖](basic/goroutine/hu-chi-suo.md)
  * [channel](basic/goroutine/channel/README.md)
    * [nil channel](basic/goroutine/channel/nil-channel.md)
    * [使用Select實現無阻塞讀取](basic/goroutine/channel/shi-yong-select-shi-xian-wu-zu-sai-du-qu.md)
  * [記憶體洩漏](basic/goroutine/ji-yi-ti-xie-lou.md)
  * [sync.map](basic/goroutine/sync.map.md)
* [不同版本的差異](basic/bu-tong-ban-ben-de-cha-yi.md)
* [time 時間包](basic/time-shi-jian-bao.md)
* [\[pkg\]fmt包](basic/pkgfmt-bao.md)

## advance-application

* [部署 dockerfile](advance-application/bu-shu-dockerfile.md)
* [Gin Web Framework](advance-application/gin-web-framework/README.md)
  * [Gin+swagger](advance-application/gin-web-framework/gin+swagger.md)
* [zaplog](advance-application/zaplog.md)
* [WebSocket](advance-application/websocket.md)
* [md5加密庫(crypto/md5)](advance-application/md5-jia-mi-ku-cryptomd5.md)
* [Viper](advance-application/viper.md)
* [格式](advance-application/ge-shi/README.md)
  * [UTF-8编码](advance-application/utf8-bian-ma.md)
  * [json](advance-application/ge-shi/json.md)

## monitor-quality

* [pprof](monitor-quality/pprof.md)
* [壓測工具](monitor-quality/ya-ce-gong-ju.md)
* [gosec](monitor-quality/gosec.md)

## more

* [收藏庫](more/shou-cang-ku.md)
* [\[IDE\] VSCODE相關設定](more/ide-vscode-xiang-guan-she-ding/README.md)
  * [\[Code Snippet\] 程式碼快捷鍵](more/ide-vscode-xiang-guan-she-ding/code-snippet-cheng-shi-ma-kuai-jie-jian.md)
  * [\[插件\]開發推薦使用](more/ide-vscode-xiang-guan-she-ding/cha-jian-kai-fa-tui-jian-shi-yong.md)
  * [\[debug setting\]](more/ide-vscode-xiang-guan-she-ding/debug-setting.md)

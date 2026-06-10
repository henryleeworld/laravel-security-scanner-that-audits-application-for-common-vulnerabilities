# Laravel 12 用於稽核應用程式常見漏洞的安全掃描

引入 andreapollastri 的 checkpoint 套件來擴增用於稽核應用程式常見漏洞的安全掃描，只需執行單一 Artisan 指令列，即可檢查常見漏洞與暴露（CVE）、已寫死機密、SQL 注入及跨網站指令碼（XSS）等項目。

## 使用方式
- 把整個專案複製一份到你的電腦裡，這裡指的「內容」不是只有檔案，而是指所有整個專案的歷史紀錄、分支、標籤等內容都會複製一份下來。
```sh
$ git clone
```
- 將 __.env.example__ 檔案重新命名成 __.env__，如果應用程式金鑰沒有被設定的話，你的使用者 sessions 和其他加密的資料都是不安全的！
- 當你的專案中已經有 composer.lock，可以直接執行指令以讓 Composer 安裝 composer.lock 中指定的套件及版本。
```sh
$ composer install
```
- 產生 Laravel 要使用的一組 32 字元長度的隨機字串 APP_KEY 並存在 .env 內。
```sh
$ php artisan key:generate
```
- 執行 __Artisan__ 指令的 __checkpoint:scan__ 來執行全部檢查。
```sh
$ php artisan checkpoint:scan
```

----

## 畫面截圖
![](https://i.imgur.com/WLCKA2b.png)
> 對原始碼進行檢測，並不會攔截套件的安裝流程認

---
layout: post
title:  "mitmproxy - an interactive HTTPS proxy"
date:   2018-08-22 08:30:47
categories: jekyll update
---

# 利用 mitmproxy 監控 Android 應用程式的 HTTP 網路傳輸

## 需求

- Docker，請自行參考 Docker 官網安裝 docker
- 同一個區網，最簡單就是連到同一臺 WIFI

## 啓動 mitmproxy

在筆電執行以下指令，-v 是用來儲存 mitmproxy 產生的 SSL 憑證。

```sh
docker run --rm -it -v ~/.mitmproxy:/home/mitmproxy/.mitmproxy -p 8080:8080 mitmproxy/mitmproxy
```

執行完 mitmproxy 即啓動監控畫面，在監控畫面中按下 q 再按 y 即可離開並關閉程式。

此時請參考 https://www.wikihow.com/Find-out-Your-IP-Address 找出筆電在區網的 IP。

這個 IP 就是之後會用到的代理伺服器 IP。

## 設定 Android 代理伺服器

請參考 https://www.wikihow.com/Change-Proxy-Settings#Android_sub 設定 Android 代理伺服器。

設定代理伺服器時，IP 填前一個步驟找出來的區網 IP，port 請填 8080。

設定完代理伺服器後請重開 Android 無線網路連線。

## 加入 mitmproxy 的 SSL 憑證到 Android

用瀏覽器打開 mitm.it，此時應看到如下畫面 https://web.archive.org/web/20180831150259/https://blog.youapp.co/images/mitmproxy/mitmproxy_website.jpg

此時請按下 Android 圖示安裝 mitmproxy 產生的 SSL 憑證。

根據官網描述，信任這個憑證並不表示也信任了其他人安裝的 mitmproxy 的憑證，每個 mitmproxy 個別獨立，自己有自己的憑證。

打開 mitm.it 後如看到 If you can see this, traffic is not passing through mitmproxy. 有幾個可能：

1. 設定 Android 代理伺服器的步驟做錯了
2. 有其他 Android 應用程式干涉網路設定，例如 DNS66，此時關掉相關的 app 就好。

## 監控 Android 應用程式的 HTTP 傳輸

此時回到 mitmproxy 監控畫面，再打開任何想監控的 Android app，即可看到網路傳輸。

按 j / k 移動指標，enter 查看傳輸內容，tab 切換傳輸內容分頁，q 回到傳輸列表。

在傳輸列表按 e1 可另存成 curl，此時請輸入路徑 ~/.mitmproxy/<檔名>.sh 即可存檔。

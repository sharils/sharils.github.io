---
layout: post
title:  "Securing Web Sites Made Them Less Accessible"
date:   2018-08-10 11:55:46
categories: jekyll update
---

這篇提到的事情很重要，一定要推一下。作者是寫 CSS: The Definitive Guide 的 Eric Mayer。

簡言之：請用 Service Worker 裡的 Cache API 把網頁內容加入快取。以下文長。

因爲現在大力推廣 HTTPS everywhere 的關係，所以導致使用衛星連接網際網路的地方使用者體驗變差，例如烏干達。

衛星連網是什麼概念呢？ 1. 理論上 ping 最快也要 500 毫秒，因爲要從地上打到衛星，而理論指的是傳輸路徑完全真空 2. 50% 甚至 80% 封包遺失完全可以預期 3. 每個月整條線路只有 50G，超過就付錢或等下個月 4. 發出請求後 15-20 秒網頁才開始顯現，運氣不好的時候則將近 1 分鐘，維基百科、Google、CNN 都是如此

以上這三個現象可以透過快取解決（例如代理伺服器）改善，但問題是透過 HTTPS 傳輸的內容在一般情況下無法被代理伺服器存入快取！！！因爲對代理伺服器而言，內容是加密的。

所以 HTTPS everywhere 這件事情會把第三世界與現代世界的距離拉得更開，因爲資訊存取變得更加困難。之所以是第三世界，是因爲使用衛星連接網際網路的地方正是因爲基礎建設不足，所以需要透過衛星。

那麼身爲前端工程師，我們可以做的是，用 Service Worker 的 Cache API 把傳輸內容存入瀏覽器的快取中。

前面提到透過 HTTPS 傳輸的內容在一般情況下無法被代理伺服器存入快取，這個問題的另一個解法是在每一個瀏覽器裏面安裝代理伺服器的 Root SSL 憑證，這樣就會變成二段 SSL，第一段先到代理伺服器，第二段再從代理伺服器到目的地，但這樣的缺點是必須在個別的瀏覽器內加入新的憑證。

那麼爲什麼不把 HTTPS 改成透過 HTTP 就好了？因爲有一些政府會審查傳輸的內容，沒加密就會被審查。

還有一些 ISP 會在網頁內嵌入追蹤使用者行爲的內容，想像你打開的所有網頁 `</body>` 的前面都被 ISP 加入一個 `src` 指向 1px 透明圖片的 `<img />` 標籤，然後你的瀏覽器預設允許接受第三方 Cookie（只有 Safari 預設不接受），於是當瀏覽器發出這個請求的時候，Cookie 也跟着被送出去，而 `src` 指向的伺服器靠着 HTTP 的 `Referrer` Header 就可以知道這個請求是來自那個網頁，再加上 Cookie 就可以判斷是否爲同一個人，於是你就這樣被追蹤了。

所以這是個兩難的問題，我們只能盡我們所能的去做。

來源：https://meyerweb.com/eric/thoughts/2018/08/07/securing-sites-made-them-less-accessible/

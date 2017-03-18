---
title: 使用 Postman 進行 API 測試
date: 2017-03-19 00:24:17
tags:
- Postman
- Web API
- Dev Tools
---
最近本部門在帶領新人進行訓練時，由於其中一項作業是開發 Web API 程式，
於是在進入到簡單的前端開發前，會使用 Postman 當作測試 API 功能是否正常的工具，
但是工具用的不對，誤認為是開發的程式錯誤，豈不是很浪費時間。
<!--more-->

過去 Postman 做為 Chrome 的頁籤外掛, 整個介面比較單純,
除了左側的歷史紀錄, 主要頁面就是輸入 API 網址及選擇 HTTP method,
常用的選項都可以很明顯的出現在畫面上不太會發生操作錯誤的問題。
![舊版 Postman](/images/postman-old.jpg)

不過也許是 Google 打算停止頁籤外掛上的支援, 
於是 Postman 也不知在何時已經改版成現在橘色背景的火箭人了(我的猜測啦),
除了支援 Chrome 外掛的安裝，也可以做為獨立的桌面程式進行安裝。
![新版 Postman](/images/postman-new.jpg)

進入到新版 Postman 程式可以發現多了不少的功能,
不過這些新功能我倒是還沒研究過, 改天有些心得再來發表XD
雖然新版的畫面對於開發人員使用上有滿多方便的地方,
但有些小細節對於新手來說, 在沒有注意的情況下就會發生操作錯誤的情形,
本篇文章先說明 Web API 常用的 GET 及 POST method 說明。

## HTTP GET
一般來說, 測試 GET method API 通常不太會有什麼問題，
輸入 API 網址, 按下 Send 按鈕就可以確認結果是不是正常,
如果有 Url query, 按下 Params 按鈕後, 輸入對應的 key/value,
或是直接把整串有包含 Url query API 網址, 輸入到網址列也可以。
![HTTP GET](/images/postman-get.jpg)

## HTTP POST
最常發生測試錯誤的, 幾乎都是在 POST method,
由於通常會在 GET 測試OK後, 接著進行 POST 新增資料的測試,
這時常常會把 API 所需的資料直接填在 Params 的 key/value,
卻發現無法新增資料, 如果新增資料是存在資料庫時, 搞不好會以為是語法還是資料庫設定上的問題,
但這時如果使用 Debug 模式測試程式, 其實可以發現資料並沒有送到。
![HTTP POST](/images/postman-post-1.jpg)
關鍵在於上圖圈選的 Body 頁籤, 可以發現當 method 由 GET 改為 POST 時,
頁籤功能從不可點選變成可點選, 但是對比舊版是直接跳出這個功能的內容確實容易讓人忽略,
![HTTP POST](/images/postman-post-2.jpg)
點開之後可以看到有四種資料傳輸的方式, 大部分的情況選擇 form-data 就可以正常使用了,
在 form-data 選項下, 可以發現一樣有 key/value 的資料設定,
這邊使用 Postman 所提供的一個測試 API 可以發現回的傳識別結果是不同的,
所以當測試 POST API 程式時, 由於程式在取得 form-data 資料時,
發現裡面是空的, 當然也就會發生錯誤了!
但是對於開發新手來說, 可能會一直無法發現為什麼會收不到資料, 而浪費不少時間。
(這個問題對於老手也是很容易發生, 但通常很快就會想到應該要把資料填在 form-data, 就很少成為問題)

------

打這篇文章主要是做個紀錄, 其實前兩天協助看新人測試程式時, 我也沒有在第一時間發現是這個問題,
由於這也不是第一次發生的事, 所以先做個小紀錄, 或許可以讓未來新進人員查到這篇文章, 減少浪費的時間。


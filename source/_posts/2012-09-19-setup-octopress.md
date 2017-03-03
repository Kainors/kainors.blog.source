---
layout: post
title: "安裝Octopress on github"
date: 2012-09-19 15:04
comments: true
categories: 
- Learn
- Octopress
tags:
- Octopress
- GitHub
---
在壞朋友的推坑下，以及Visual Studio持續無法使用<br  />
不小心就搞出這個站!!<br />
接著因為Visual Studio SP1在搞鬼!!<br />
乾脆順便把Octopress的安裝過程整理一下好了!!
<!-- more -->
***
1.首先要安裝Git以及申請github的帳號，<br />
這點就不多說了，請看以下連結<br />
<a href="http://itspg.github.com/blog/2012/02/29/github-on-windows-tutorial/">itsPG.org [教學] 在windows上使用github 新手教學 / 初學者指南</a><br />
但在這篇文章只要做到第四點就好，<br />
接著在github的頁面點選Create a New Repo(目前應該在個人頁面的右上角中)<br />
在Repository name的欄位中輸入「自己的帳號.github.com」後，按下下方的Create repository<br />
接下來的頁面中有Quick setup，可以選擇HTTP及SSH，將這兩個內容選一個先記著吧!!
***
2.接著安裝ruby及Octopress<br />
也是請看一下連結<br />
<a href="http://itspg.github.com/blog/2012/02/29/octopress-on-windows-tutorial/">itsPG.org [教學] 在windows上安裝octopress 新手教學 / 初學者指南</a>

雖然照著這篇文章，應該可以正常完成，<br />
不過因為我實在遇到太多問題，所以才要特別紀錄這篇!!<br />
依照文章完成到第四點後先暫停，<br />
這時先到Octopress下載的資料夾中，用任何文字編輯器打開Rakefile這個檔案<br />
搜尋&amp;hellip;這個字串，然後把它刪除後存檔(這是針對在windows下的情況)<br />
接著繼續在Command Line輸入:<br />
    rake setup_github_pages
<br />後，出現Repository url:將第一步所記下的SSH位址輸入，<br />
格式如：git@github.com:帳號/帳號.github.com.git<br />
接著繼續教學文件中的第六步做下去，<br />
大致上就就可以在github上建立好一個Blog囉!!
***
最後提醒一下，<br />
因為預設建立起來的檔案是ANSI編碼，<br />
但我們會輸入中文字，所以要用文字編輯器將檔案重新存檔成UTF-8編碼，<br />
這樣才有辦法建立起來喔!!
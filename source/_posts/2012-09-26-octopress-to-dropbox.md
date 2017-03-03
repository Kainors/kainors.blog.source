---
layout: post
title: "將Octopress source備份至Dropbox"
date: 2012-09-26 09:53
comments: true
categories: 
- Learn
- Octopress
tags:
- Octopress
- Git
- GitHub
---
在好不容易建立了自己的部落格  
並且也建立了文章讓部落格慢慢的豐富起來  
雖然在Github上有完整的文章內容  
但也都是編譯過而發佈出去的內容  
而原始編輯的檔案還是在本機端  
如果電腦掛掉，辛苦建立的心血就這樣沒了  
<!--more-->
當然為了避免這種情況，得將Octopress的source部分備份起來  
剛好友人給了篇文章可以利用Dropbox當作Private的Repo  
[原文在此](http://orihubon.com/blog/2012/03/18/change-upstream-of-source-to-dropbox/)  
不過內容是使用Linux  
雖然windows下是大同小異  
但我也還是在這篇文章內紀錄一下步驟
***
1.首先要先安裝Dropbox的client端同步程式

2.接著在開啟命令提示字元後，首先移動到使用者資料夾下的Dropbox資料夾，  
　以Windows 7來講會在C:\Users\使用者帳號\Dropbox
  
3.接著建立要備份的資料夾，並使用git初始化，範例如下  
    mkdir kainors-blog.git  
    cd kainors-blog.git  
    git --bare init  

4.接著移動到本機端octopress的資料夾下，先查看remote path  
    git remote -v
    octopress       https://github.com/imathis/octopress.git \(fetch\)
    octopress       https://github.com/imathis/octopress.git \(push\)
    origin  git@github.com:Kainors/kainors.github.com.git \(fetch\)
    origin  git@github.com:Kainors/kainors.github.com.git \(push\)
	
5.接著將剛剛在Dropbox新增的目錄加到到remote path  
    git remote add dropbox C:\Users\使用者帳號\Dropbox\kainors-blog.git
    
6.再次確認remote path  
    git remote -v
    dropbox C:\Users\使用者帳號\Dropbox\kainors-blog.git \(fetch\)
    dropbox C:\Users\使用者帳號\Dropbox\kainors-blog.git\ (push\)
    octopress       https://github.com/imathis/octopress.git \(fetch\)
    octopress       https://github.com/imathis/octopress.git \(push\)
    origin  git@github.com:Kainors/kainors.github.com.git \(fetch\)
    origin  git@github.com:Kainors/kainors.github.com.git \(push\)
    
7.接著將source push到Dropbox上  
    git push -u dropbox source
---
layout: post
title: "Octopress程式碼Highlight問題-2"
date: 2012-10-04 17:39
comments: true
categories: 
- Learn
- Octopress
tags:
- Octopress
- Ruby
---
這是因為手癢  
把公司的電腦重灌成Windows 8後  
想說把ruby、python跟git都裝一裝後  
應該就沒什麼問題了吧!!
<!--more-->
結果只要用程式碼區塊需要用到Highlight語法時  
就給我蹦出`SyntaxError`的訊息  
上Google一看原來是Python版本的問題  
Octopress用的是Python2.X版，不過我再重灌時沒有注意  
想說就直接裝最新的Python3.X版  
於是就將Python移掉再重新安裝  
結果再generate時，反而蹦出更多error  
再搞了好久還是搞不定，一氣之下就把Ruby跟Python刪的一乾二淨  
然後再重新裝起，一切又好了  ψ(｀∇´)ψ
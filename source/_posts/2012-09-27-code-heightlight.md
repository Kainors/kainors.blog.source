---
layout: post
title: "在Windows下讓Octopress可以顯示漂亮的程式碼區塊"
date: 2012-09-27 14:13
comments: true
categories: 
- Learn
- Octopress
tags:
- Octopress
---

雖然Markdown語法中，可以標註程式碼區塊  
不過Octopress還可以讓程式碼更漂亮的顯示  
這些在官方的文件都有說明!!  
但在Windows編譯的環境下，卻遇到了些問題!
<!--more-->
一開始是測試`backtick_codeblock`語法如下：  
	``` [language] [title] [url] [link text]  
	code snippet  
	```  
雖然第一行的敘述可加可不加，  
在沒有任何敘述時可以正常運作  
但只要在第一行加上內容後，會造成頁面一片空白

接著測試Codeblock的方式：  
	{\% codeblock [title] [lang:language] [url] [link text] %}  
	code snippet  
	{\% endcodeblock %}  
只要加上`lang:某語言`的敘述  
就會出現  
	Liquid error: No such file or directory - python -c “import sys; print sys.executable”  
	# or  
	Liquid error: undefined method `Py_IsInitialized’ for RubyPython::Python:Module  
後來在網路上找了一下，才看到[這篇](http://www.blogjava.net/lishunli/archive/2012/03/18/372115.html)  
原來還要裝上python才能讓程式碼區塊正常辨識語法及顯示Highlight  
這麼一來一切問題就解決了  

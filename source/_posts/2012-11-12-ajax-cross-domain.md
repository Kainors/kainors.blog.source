---
layout: post
title: "使用XMLHttpRequest執行AJAX跨網域存取"
date: 2012-11-12 14:15
comments: true
categories: Learn
tags: ajax
---
最近開發的東西，開始嘗試使用Web App的方式來製作  
當然會用到許多Ajax的Request來傳遞資料  
而後臺的掌控權是在另一位同事的手上  
於是在測試時，要調用後台的資料便出現了Cross Domain的問題  
<!--more-->
因為javascript本身的限制(許多broswer端的
雖然這個問題可以自己寫個proxy的站台  
將資料處理好後，再傳送到前端頁面  
不過未來的產品上，雖然有http的service  
但不見得有完整的web server  
所以寫proxy的想法就先放一邊  
就在邊找解決辦法時  
看到原來Ajax的XMLHttpRequest本身就提供cross domain的解決方法  
不過server side也得提供相對應的response header
就是`Access-Control-Allow-Origin`  
下面就以PHP作為範例
```php cross.php
<?php
    header("Access-Control-Allow-Origin: http://kainors.github.com");
    echo "Cross Domain OK!!";
?>
```
而`Access-Control-Allow-Origin`這個header後面就是限制可存取的網域  
如果希望可以讓所有網站都可以存取可以使用"*"

接著測試的頁面中主要的JavaScript如下：
```javascript
function createCrossReuqest(method, url){
    var xhr = new XMLHttpRequest();
    if("withCredentials" in xhr){
        xhr.open(method, url, true);
    }
    else if(typeof XDomainRequest != "undefined"){
        xhr = new XDomainRequest();
        xhr.open(method, url);
    }
    else{
        xhr = null;
    }
}

var request = createCrossRequest("get", "http://www.testsite/cross.php");
if(request){
    request.onload = function(){
        alert(request.responseText);
    };
    request.send();
}
```
雖然這個方法，還是無法直接讓javascript執行跨網域的存取  
但只要在server side增加`Access-Control-Allow-Origin`這個header就能解決問題  
在團隊開發中，至少還是個不錯的方法  


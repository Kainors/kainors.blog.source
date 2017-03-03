---
layout: post
title: "初探OpenLayers"
date: 2012-10-04 11:50
comments: true
categories: Learn
tags:
- Map
- OpenLayers
- javascript
---
因為工作上，老闆提到這玩意兒  
先拿來稍微做一下研究，並做點紀錄  
<!--more-->
OpenLayers的網站[在此](http://openlayers.org/)  
只要將整個API下載下來就可以使用了  
而裡面的example資料夾中也有許多範例程式碼  
因為一開始自己直接寫，發現不管怎樣都不會出現地圖  
於是乾脆參考範例，才發現放地圖的那個DIV容器還需要設定寬高才會顯示  
白白的浪費不少時間測試  
下次就記得有新的API要玩就直接看範例來玩吧XD  

廢話不多說  
要建立OpenLayers的地圖  
首先先將下載來的檔案中`OpenLayers.js`、`img資料夾`及`lib資料夾`  
放到自己網站中，注意這三個要放在同一個資料夾中  
另外，`theme資料夾`有一些預設的樣式可以用  
就順便放在一起吧!!  
接著就開一個新的html頁面來編輯  
```html
<!DOCTYPE html>
<html>
    <head>
        <script src="./OpenLayers.js" type="text/javascript"></script>
        <style>
            #map{
                width:300px;
                height:200px;
                border: 1px solid #ccc;"
            }
        </style>
        <script type="text/javascript">
            function init(){
                var map = new OpenLayers.Map("my_map");
            }
        </script>
    </head>
    <body onLoad="init()">
        <div id ="my_map"></div>
    </body>
</html>
```
非常簡單只要把要當作容器的DIV ID設定給OpenLayers.Map中  
我們就可以有一個Map容器  
但是只有這樣還是不會有地圖的  
還要為這個Map容器放入地圖圖層才能使用  
在這邊用Google Map來當作範例  
在此之前要先引用Google Map的API  
```html
<script src="http://maps.google.com/maps/api/js?v=3&amp;sensor=false"></script>
```
接著在原先的`init()`function中加入  
```js
var gmap = new OpenLayers.Layer.Google(
    "Google Streets", // the default
    {numZoomLevels: 20, visibility: false}
);
map.addLayer(gmap);	
map.setCenter(new OpenLayers.LonLat(10.2, 48.9).transform(
    new OpenLayers.Projection("EPSG:4326"),
    map.getProjectionObject()
), 5);
```
如此一來就可以看到地圖了!!  
效果如下！

<script src="http://openlayers.org/api/OpenLayers.js"></script>
<script src="http://maps.google.com/maps/api/js?v=3&amp;sensor=false"></script>
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script>
<script type="text/javascript">
    $(function(){
        var map = new OpenLayers.Map("my_map");
        var gmap = new OpenLayers.Layer.Google(
            "Google Streets", // the default
            {numZoomLevels: 20, visibility: false}
        );
        map.addLayer(gmap);	
        map.setCenter(new OpenLayers.LonLat(121.5, 23.6).transform(
            new OpenLayers.Projection("EPSG:4326"),
            map.getProjectionObject()
        ), 7);
    });
</script>
<div id="my_map" style="width:300px;height:200px;border: 1px solid #ccc;"></div>
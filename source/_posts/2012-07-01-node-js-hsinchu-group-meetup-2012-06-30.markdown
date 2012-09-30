---
layout: post
title: "Node.JS Hsinchu Party 2012/06/30"
date: 2012-07-01 20:50
comments: true
categories: [nodejs, event, note]
---
![](http://i.imgur.com/zFjtc.png)

這次Node.JS Hsinchu Party，除了有[JackBean][jack]提供的免費場地、Nausca大大熱情贊助的飲料外，
還有大家期待已久的、一樣是由[storiii][]的Yusen大大來分享的兩個主題：[EJS][]與[Y-combinator][Y]。

[jack]:http://blog.jackbean.tw
[Y]:http://en.wikipedia.org/wiki/Y_Combinator#Y_combinator
[EJS]:https://github.com/visionmedia/ejs#readme
[NPM]:http://npmjs.org/
[storiii]:http://storiii.com/
[exp]:http://expressjs.com/

<!--more-->

##[EJS][]
[EJS][]是一個以JavaScript實作的Template Engine，基本用法跟ASP、JSP的tag library很類似：
    <% if(user.name) {%>
        <h2><%= user.name %></h2>
    <% } %>

它可以直接在NODE以[NPM][]安裝使用（可以完美配合[express.js][exp]），也可以在broswer端呼叫使用。
基本的介紹其實到這邊就講完了（咦!?）


###Use case
EJS看似一個簡單的工具，要如何把它用到出神入化的境界呢？
講者舉了像iPad上flipboard上可依內容做出的動態排版為例，
提到了「設計師心目中的排版」與「工程師心目中的排版」觀念上的落差。

若只討論單純的切割畫面，可以是一種程式先決的過程；
而設計先決，是請設計師先決定怎樣叫好看的方塊：例如設計出大塊/中塊/小塊三種不同的方塊外觀，
對應到重要性或關聯性為高、中、低的文章，
然後再設計填充畫面的演算法。在範例中，講者將整個畫面切成grid，
對應到程式上的二維陣列，再請設計師用小格子去排，
把排版問題轉換成排積木問題：laout problem -> packing problem。
最後，計算造成多少破洞，找出第一個符合標準的排版組合，進行layout。

<!--
慧眼挑金eat people
cinder: C++做到JS的感覺
-->




##Y Combinator
第二個主題是大家耳熟能詳的Y-combinator。
但要講的不是那間國外有名的創投，而是那個傳說中的functional programming技巧！
（現場三個人裡面也是有兩個以為是要講創投，不過謎底揭曉後，大家興致更高昂了XD）

YuSen大大用最經典的費伯納西遞迴函式開始進行推導，經過curry等技巧的一番最佳化之後，
最後生成的是一個讓人看不懂的Y函式，還有分離出來費氏數列邏輯的函式。

###[詳細推導過程請見YuSen大大的網站投影片](http://storiii.com/player.html)

雖然Y combinator本身是經過層層推導出的結果，無法讓人一眼看懂，
不過可以將它理解成「遞迴引擎」。只要將邏輯傳進去，就可以利用它生成一個單一參數的遞迴函式。
這樣做的優點是可以減少撰寫遞迴函式犯錯的機會；另外更實用的，
我們可以透過改善Y遞迴函式引擎，讓所有使用它的函式得到加速的效果。

在投影片中Memorized Y的範例，藉由將Y導入快取機制來避開重複運算，達到神級的效能增益：
加速前`fib(50)`要耗時520秒；使用加速後的`fibM()`後，執行速度快到無法以毫秒單位估計，
直到‵fibM(1000)`才終於花了1毫秒，但是此時計算出的數值已經大到超越JS提供的精準度了！

<!--
functor
functional composition?
-->

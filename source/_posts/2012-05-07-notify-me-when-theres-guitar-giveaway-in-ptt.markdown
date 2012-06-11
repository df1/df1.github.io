---
layout: post
title: "無聊分享：PTT有人在送吉他時候跟我說一聲"
date: 2012-05-07 22:24
comments: true
categories: [boring, ptt, pipes, mashup, rss]
---
又來做無聊分享了！話說PTT的give（贈送板）真的是個好地方，幾乎是什麼都送，什麼都不奇怪，連吉他、電吉他都有很多佛心來的版友大方割愛。不過對於工作忙碌、在公司又不能上PTT的的宅宅工程師而言，絕對是搶不贏那些全職鄉民的orz

這時候若是有個機器人可以隨時幫我爬文通知該有多好！不過機器人其實不用自己寫，有個N年前發表之後一直維持冷門狀態的服務--[Yahoo Pipes](http://pipes.yahoo.com)可以派上用場！

##製作Pipe

其實Pipes功能相當多，但其最終的目的就是幫我們從許多資料來源中擷取出我們自己想要的內容。這裡我就不對詳細使用方法多作介紹，若有興趣網路上有許多相關資料。

Pipes的一大特點就是他的視覺化畫布，讓你對資料的『管路』一目瞭然。看圖就可以知道我在做啥：
<!--more-->
{%img /attachments/2012-05-07-notify-me-when-theres-guitar-giveaway-in-ptt/pipes.png "專門PTT送吉他的Pipe" %}
###小解說
1.	資料來源有兩個：give板與guitar板。
2.	give板過濾標題關鍵字有『吉他』的；guitar板過濾有『送』的
3.	取聯集
4.	一一去撈對應的PTT Web板頁面內容，把它塞進`item.description`中方便即時觀看（沒辦法，公司不能上orz）


做完之後，在頁面上有一堆格式的輸出可以隨便拿，例如可以拿RSS再加上自己chrome的RSS通知外掛，若有新資料就自動彈出小視窗；或是直接點`Results by Email or Phone`讓Yahoo Alert傳email或簡訊通知。
欸，至於收到通知後若是在上班怎辦？當然是直接call萬能的老弟叫他幫忙丟水球回站內信囉XD

{%img /attachments/2012-05-07-notify-me-when-theres-guitar-giveaway-in-ptt/reader.png "將RSS餵給Google Reader" %}

###Pipe連結：[PTT送吉他](http://pipes.yahoo.com/s911131/pttguitar)，歡迎fork！


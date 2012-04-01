---
layout: post
title: "Web豆知識：在URL後面帶個#xxx就顯示對應的主題是怎麼做的？location.hash與onhashchange event (Ext.history/jQuery.history)"
date: 
published: false
comments: true
categories: [ExtJS, hash, hashbang, html5, jQuery, JS]
---
標題寫那麼長，不過我覺得還是很難被需要的人搜尋到XD<br />
<br />
其實一開始找資料的時候，根本不知道那個東西叫做location hash，更不知道#號的英文叫hash mark，只能在關鍵字打&lt;a name&gt;或是page anchor change event之類的。(根本忘記當初怎麼找到的)<br />
<br />
講到SEO(搜尋引擎最佳化)，讓我想到上禮拜去找同學時候聊到一個樂團叫fun.，喇賽說他們取團名時絕對沒考慮SEO問題，這樣我們以後乾脆取個http://樂團或是特殊符號樂團之類的讓沒人找得到我們XDD(題外話)<br />
<br />
總之，我要講的就是類似這些：<br />
<br />
<ol>
<li>Ext JS的API：網址像這樣
<a href="http://docs.sencha.com/ext-js/4-0/#!/guide/application_architecture">http://docs.sencha.com/ext-js/4-0/<b>#!/guide/application_architecture</b></a>&nbsp;他的hash會讓頁面裡的tab打開對應的主題，並focus到對應的method的段落之類的。</li>
<li>之前介紹過的impress.js：網址像這樣
<a href="http://bartaz.github.com/impress.js/#/bored">http://bartaz.github.com/impress.js/#/bored</a>&nbsp;
他的hash會開始過場特效，把投影片導到對應的頁面。</li>
</ol>
<br />
目標就是讓網站可以根據#後面的東西，在不換頁的情況下對頁面做一些事，使用者也可以透過上一頁、下一頁來操作系統。
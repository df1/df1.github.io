---
layout: post
title: Web豆知識：網址後面帶個#!xxx（井號驚嘆號）就顯示對應的內容是怎麼做的？Hashbang/Shebang URL 與 Responsive Web Design
date: 2012-04-08 13:17
comments: true
published: false
categories: [JS, hashbang, responsive, jQuery, ExtJS]
---
累了嗎？先來聽一首關於Shebang的歌吧！（請先看標題自行斟酌是否按下去XD）
<iframe width="420" height="315" src="http://www.youtube.com/embed/5ihtX86JzmA?rel=0" frameborder="0" allowfullscreen></iframe>

<!--
location.hash與onhashchange event (Ext.history/jQuery.history)
-->


標題寫那麼長，不過我覺得還是很難被需要的人搜尋到？
其實一開始找資料的時候，根本不知道URL後面那個東西叫做`location.hash`；不知道#號的英文叫hash mark；更不知道`!#`有個公認的綽號叫做shebang或hashbang。只能在關鍵字打&lt;a name&gt;或是page anchor change event之類的。（根本忘記當初怎麼找到的）
題外話，講到SEO搜尋引擎最佳化，讓我想到之前去找同學時候聊到一個樂團叫fun.，喇賽說他們取團名時絕對沒考慮SEO問題，這樣我們以後乾脆取個http://樂團或是特殊符號樂團之類的讓沒人找得到我們XDD


總之，我要講的就是類似這些
1.	Twitter的網址長這樣
2.	Ext JS的API：網址像這樣<a href="http://docs.sencha.com/ext-js/4-0/#!/guide/application_architecture">http://docs.sencha.com/ext-js/4-0/<b>#!/guide/application_architecture</b></a>&nbsp;他的hash會讓頁面裡的tab打開對應的主題，並focus到對應的method的段落之類的。</li>
3.	之前介紹過的impress.js：網址像這樣
<a href="http://bartaz.github.com/impress.js/#/bored">http://bartaz.github.com/impress.js/#/bored</a>&nbsp;
他的hash會開始過場特效，把投影片導到對應的頁面。</li>


目標就是讓網站可以根據#後面的東西，在不換頁的情況下對頁面做一些事，使用者也可以透過上一頁、下一頁來操作系統。

<script async class="speakerdeck-embed" data-id="4de55b8d5753082e3c000002" data-ratio="1.3333333333333333" src="//speakerdeck.com/assets/embed.js"></script>

##參考連結
*	[Responsive web design from the future][responsive] - kneath
*	[Making AJAX Applications Crawlable][crawl] - Google Webmaster EDU
*	[HTML5 History API][html5] - HTML5 Demos
*	[Start using HTML5 History API today][brooky] - brooky's blog（中文）
*	[Create gmail like app using html5 history api and hashbang][gmail] - Amit Patil
*	[What's the shebang/hashbang (#!) in Facebook and new Twitter URLs for?][stack] (stackoverflow)
*	[It's About The Hashbangs][dan] - Dan Webb
*	[Side Effects of Hash-Bang URLs][side] - Danny Thorpe
*	[jQuery hashchange event][jquery] - Ben Alman
*	[Thoughts on the Hashbang][thoughts] - ben cherry
*	[Breaking the Web with hash-bangs][breaking] - isolani
*	[Ext.util.History][ext] - Ext JS 4.0 API Documentation

[responsive]: http://warpspire.com/talks/responsive/
[crawl]: https://developers.google.com/webmasters/ajax-crawling/?hl=zh-TW
[html5]: http://html5demos.com/history/
[brooky]: http://brooky.cc/2011/06/27/start-using-html5-history-api-today/
[gmail]: http://www.amitpatil.me/create-gmail-like-app-using-html5-history-api-and-hashbang/
[stack]: http://stackoverflow.com/questions/3009380/
[dan]: http://danwebb.net/2011/5/28/it-is-about-the-hashbangs
[side]: http://dannythorpe.com/2011/02/09/side-effects-of-hash-bang-urls/
[jquery]: http://benalman.com/projects/jquery-hashchange-plugin/
[ext]: http://docs.sencha.com/ext-js/4-0/#!/api/Ext.util.History
[thoughts]: http://www.adequatelygood.com/2011/2/Thoughts-on-the-Hashbang
[breaking]: http://isolani.co.uk/blog/javascript/BreakingTheWebWithHashBangs
http://shkspr.mobi/blog/index.php/2012/05/interesting-twitter-hashbang-bug/
http://www.adequatelygood.com/2011/2/Thoughts-on-the-Hashbang

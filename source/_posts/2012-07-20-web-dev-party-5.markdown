---
layout: post
title: "Web Dev Party #5 活動小記"
date: 2012-07-20 19:40
comments: true
categories: [event, html5]
---

今天請假北上參加了年度的[Java大拜拜](https://service.ithome.com.tw/20120720Java/)，剛好有機會參加這次在蛙.咖啡 (frog.cofe)舉辦的[Web Dev Party #5](http://registrano.com/events/webdev-party-05)！這可是傳說中全台最有梗、一票難求，大大、神人、正妹(!)一次到位的熱鬧技術趴，快來一探究竟吧！

這次的主題是關於現正快速崛起的新的Web標準-- [HTML5](http://zh.wikipedia.org/wiki/Html5)的應用，一共有兩個講題：Responsive WAT Design 與 HTML5 JavaScript APIs。還是要先提醒的是，如果您用的是IE且版本是10以前，還是先換個瀏覽器再來玩下面的東西吧`>_^`

<!--more-->

![閃光洽 - Rsponsive WAT Design](https://i.imgur.com/Cnu9x.jpg)

![保哥 - HTML5 JavaScript APIs](https://i.imgur.com/8QbM1.jpg)


##Responsive WAT Design
*   講者：[閃光洽](http://about.me/hinablue)
*   部落格：[HINA::工程幼稚園](http://blog.hinablue.me)
*   噗浪：[Cain Chen](http://www.plurk.com/hinablue)

由**大澤木小鐵**大大簡單的開場後，首先登場的是**閃光洽**大大分享的Responsive WAT Design。
據說這次開場前投影片發生了*杯具*，於是破天荒的直接開vim當投影片用（驚）！

(雖然沒有正式的投影片，講者還是講了不少[疑似之前分享過的投影片(?)](http://rwd.hinablue.me/)←投影片本身也是responsive，可以用手機觸控喔！)

###WAT is Responsive Web Design!?
Responsive Web Design (RWD) 從字面上看來是指「會依環境而反應的網頁設計」(Web design that responds to the environment)。這個UX議題最近愈來愈廣泛地被討論，其中也包含[許多不同面向](https://speakerdeck.com/u/kneath/p/responsive-web-design-from-the-future)，
不過最基本也最常提到的一項，還是要讓網頁在不同螢幕大小、不同裝置類型、橫向或縱向切換時，能有相對應的顯示方式。

要做到這功能，除了自己用[CSS3的media query](http://www.w3.org/TR/css3-mediaqueries/)硬刻以外，講者也推薦了一些好用的現成工具，如[Initialzr](http://www.initializr.com/)與Twitter的[bootstrap](http://twitter.github.com/bootstrap/)等等。另外也秀了一個經典的responsive + fluid範例：[Golden Grid System](http://goldengridsystem.com/)，裡面提供以網格為基礎的許多responsive設計細節（看了一下..有點難懂囧）


##HTML5 JavaScript APIs
*   講者：Will保哥
*   部落格：[The Will Will Web](http://blog.miniasp.com/)
*   FB粉絲團：[Will 保哥的技術交流中心](http://www.facebook.com/will.fans)


中場休息吃吃喝喝閒聊過後，接下來這個主題的範圍就更廣了，保哥即將為我們介紹HTML5所有新標準還有對應的JS寫法！

可惜的是投影片似乎還沒公開，不過[保哥在微軟大拜拜的講題](http://www.microsoft.com/taiwan/events/learn/?id=6d9b008a0aa5)中有一些類似的內容！
（[直接下載影片](http://content3.catalog.video.msn.com/e2/ds/b29005d2-4459-42d4-9b80-7af66875bf50.mp4)）

以下是我的零星小筆記：

###async
以前的script tag就可以使用[defer][]的屬性，讓頁面載入完成之後才執行script tag內的code：
    <script src...
    <script defer src...
現在多了新的[async][]屬性。因為預設瀏覽器載入、執行script tag的行為是會block住整個頁面載入的process；
但套用了async之後，script tag載入就會變成非同步，不會阻擋畫面的載入。
    <script async...
    <script async defer ...
[defer]:http://www.w3schools.com/tags/att_script_defer.asp
[async]:http://www.w3schools.com/html5/att_script_async.asp


[async的範例(微軟網站)](http://ie.microsoft.com/testdrive/Performance/AsyncScripts/Default.html)
在第一個範例中，可以很清楚的看出當欲載入的JS檔過大時使用async屬性的好處。
第二個範例是示範在JS裡面生出來的script tag（範例是動態生成外部script tag來顯示圖片）。在每個script在載入時間不同的情況下，原本JS執行是非同步的特性會造成他呈現的圖片順序無法控制；如果在這時候把async屬性設成false，script才會乖乖的一個接一個載入。

###Sandbox
    <iframe sandbox="allow-forms allow-same-origin" ...
<del>如果你有跟IE簽下契約成為XSS少女</del>...
阿不是啦，是說例如我們在部落格裡面常常會有許多的iframe（你的初音時鐘還有噗浪徽章啥的），
這些iframe常常成為XSS攻擊的隱患。
如果將iframe設定sandbox沙盒模式屬性，iframe裡面的網頁就會被視為cross-domain且無法執行script、plugin、form等等行為。當然如果要允許其中某些行為也是都可以設定的，如上面範例就可以允許iframe裡的form submit且不會強制當常cross-domain。

[sandbox範例(微軟網站)](http://ie.microsoft.com/testdrive/HTML5/sandbox/Default.html)


###離線WebApp: Application Cache

    <html manifest="clock.appcache"

    mime: text-cache-manifest
這部分講者分享了許多他自己使用這個離線快取實作的經驗，還有許多的悲劇跟實務上的大陷阱。
不過我...我...那時候聽得太入神忘了做筆記了囧，等有研究到這塊應該會想起來，到時候再補上吧！（喂喂喂來人阿把他帶走）

###Web Storage: local storage + session storage
當我們要在用戶端存資料時，通常會想到使用cookie。
但它有些限制：每個domain最多300個、最大4K、效能不彰、無法在client區分不同視窗等等。
Web storage克服了以上的cookie做不到的事；
另外在安全性上，web storage的內容server side是抓不到的。
API中提供以下兩種類型的web storage：
*   sessionStorage：同域名下、在同一視窗存取資料
*   localStorage：跨視窗存取資料

不過Web Storage還是有一些限制如：W3C建議不超過5MB、只能存字串等等。


###Web DB
W3C放棄了SQLite規格，之後會改往IndexedDB發展。
Indexed DB：key是字串，value可以是object
[使用Web DB實作的TODO List範例](http://www.html5rocks.com/en/tutorials/indexeddb/todo/)


###Geolocation
地理位置的API不是在window下，而是在navigator下。有兩個主要功能：
1.  取得當前座標資訊
2.  持續追蹤座標資訊

[DEMO](http://html5demos.com/geo/)


###Web Audio
![HTML5 Audio Editor](http://www.html5audio.org/item_images/plucked-de.png)
講者示範了一個令人大為驚豔的作品：[html5 audio editor](http://plucked.de)。
這個web app竟然在網頁上實現了一個混音軟體，而且還是學生的作品！
（[網址](http://plucked.de)、[Github上的原始碼](https://github.com/plucked/html5-audio-editor)）

##Ending
快樂的時光總是特別快，因為場地時間限制的關係，趴踢還是得散場Q\_Q。
但講了那麼多，實際上還講不到一半的投影片內容（驚）！
話說以現在Web的天下大勢可說是瞬息萬變，即使是大神如估狗、巨人如M$，也是都看不準的。
若之後有機會聽到完整版，想必又會有許許多多不同的梗、不同的感受吧！

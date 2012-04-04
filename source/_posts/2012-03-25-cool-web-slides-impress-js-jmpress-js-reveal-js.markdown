---
layout: post
title: "酷炫的web投影片：impress/jmpress.js與reveal.js"
date: 2012-03-25 13:17
comments: true
categories: [cool, impress.js, jmpress.js, jQuery, JS, prezi, reveal.js, web slide]
---
一年多前，咱們team用了一個flash-base的簡報工具－－<a href="http://www.prezi.com/" target="_blank">Prezi</a>，
向老闆報告某雲端應用的讀書會sharing。那是個多麼美好的時光，也是多麼糟糕的時光阿(遠目)<br />
<br />
Prezi的概念就是：畫布是無限大的，你可以定義每個頁面的框在畫布的哪個位置、大小；播放時候會以zoom-in/out的形式，可以帶給觀眾在單一個主題上overview與微觀的整體層次感。當初令我印象最深刻的就是某個prezi實習生做的<a href="http://prezi.com/xcit4zbat6sw/sweet-recipe-to-solving-problems/" target="_blank">Sweet recipe to solving problems</a>(真的是Epic！)。如今Prezi的知名度應該已經有相當程度的提升，也讓我跌破眼鏡的開始支援了iPad（應該是開發了flash轉CSS3？我沒iPad所以不確定）。如果還沒體驗過的話，可以直接去
<a href="http://www.prezi.com/" target="_blank">Prezi</a>&nbsp;上逛逛別人做好的，個個都是熱情奔放、創意無限！<br />
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;"><a href="http://1.bp.blogspot.com/-HFX5DC8Bf-I/T28aRi34DXI/AAAAAAAABkM/APfd36gK0RU/s1600/2012-03-25+21-14-11.png" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="224" src="http://1.bp.blogspot.com/-HFX5DC8Bf-I/T28aRi34DXI/AAAAAAAABkM/APfd36gK0RU/s320/2012-03-25+21-14-11.png" width="320" /></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;">Prezi的播放介面</td></tr>
</tbody></table>
<br />
<div style="text-align: left;">
最近，手上又有個關於jQuery的sharing topic。剛好在開始準備的前幾天，我看到了讓我眼睛一亮的玩意－－<a href="http://bartaz.github.com/impress.js">impress.js</a>、<a href="http://shama.github.com/jmpress.js">jmpress.js</a>和<a href="http://lab.hakim.se/reveal-js/">reveal.js</a>。因為剛好需要對jQuery的功能做live demo，如果能在slide上面就直接辦到，這是多麼美妙的一件事啊！當然是先用再說囉。</div>
<br />
<table align="center" cellpadding="3" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr>

<td style="text-align: center;"><a href="http://bartaz.github.com/impress.js" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="150" src="http://2.bp.blogspot.com/-CcKU5md9xbE/T28aCDgXDyI/AAAAAAAABkE/esPzJ5B-BRo/s320/2012-03-25+20-27-26.png" /></a></td>

<td style="text-align: center;"><a href="http://shama.github.com/jmpress.js" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="150" src="http://4.bp.blogspot.com/-JcFoEZWAFaA/T3B8DM7UAeI/AAAAAAAABkk/BFV4kDSv54s/s320/2012-03-26+22-20-42.png" /></a></td>

<td style="text-align: center;"><a href="http://lab.hakim.se/reveal-js/"><img border="0" height="150" src="http://2.bp.blogspot.com/-0YfuivlNJ04/T28aA7LvzwI/AAAAAAAABj8/0Qu3IObTUs0/s320/2012-03-25+20-27-55.png" style="margin-left: auto; margin-right: auto;" /></a></td></tr>
</tbody></table>
<div class="separator" style="clear: both; text-align: center;">
<span id="goog_724297899"></span><span id="goog_724297900"></span><a href="http://www.blogger.com/"></a>
</div>
<br />
它們都是以CSS3+JS為主的技術來實現web投影片播放：impress.js簡單的說就是100%向prezi致敬（官網承認的），將整個無限畫布的概念<strike><span style="color: #999999;">抄</span></strike>承襲了下來；jmpress.js則是繼續<strike><span style="color: #999999;">抄</span></strike>承襲了impress.js， 加入了jQuery/jQuery UI，強調他不只可以當作投影片，更可以拿來當成網站用；reveal.js則是比較不玩這麼fancy的東西，只提供3種轉場效果&amp;程式碼自動上色，整體播放下來的體驗會比較像PowerPoint或Keynote。比較炫的就是除了←→換頁外，還可以使用↑↓方向鍵來進入一張投影片的「地下室」（這樣講有點抽象，直接<a href="http://lab.hakim.se/reveal-js/">去玩玩看</a>就知道啦XD）<br />
<br />
<br />
於是，我當然是挑了比較酷炫的impress.js來試試看（為什麼要demo jQuery卻不用jmpress.js呢？因為我做完才發現有它的存在orz）。
<br />
最後，來個小小的比較（個人意見）：<br />
<br />
<table border="1" cellpadding="0" cellspacing="0" style="border-collapse: collapse;">
<tbody>
<tr style="background: #CCCCCC;">
  <td width="80"></td>
  <td><div style="text-align: center;">
Prezi</div>
</td>
  <td><div style="text-align: center;">
impress.js/jmpress.js</div>
</td>
  <td><div style="text-align: center;">
reveal.js</div>
</td>
 </tr>
<tr>
  <td style="background: #CCCCCC;">使用技術</td>
  <td><div style="text-align: center;">
Flash</div>
</td>
  <td colspan="2"><div style="text-align: center;">
CSS3 + JS</div>
</td>
 </tr>
<tr>
  <td style="background: #CCCCCC;">簡報特性</td>
  <td colspan="2"><div style="text-align: center;">
以zoom-in/out的形式，帶給觀眾整體感</div>
</td>
  <td>提供較多如PowerPoint簡報特性的功能，並提供「地下室」</td>
 </tr>
<tr>
  <td style="background: #CCCCCC;">操作性</td>
  <td>可隨時使用滑鼠滾輪自由放大縮小；可自由拖移畫布位置</td>
  <td>無法使用滾輪、拖移</td>
  <td>四向方向鍵的創新模式</td>
 </tr>
<tr>
  <td style="background: #CCCCCC;">跳頁方便性(跳到很遠的投影片)</td>
  <td>須用滾輪縮小後，點選該投影片方可跳至該頁</td>
  <td>在URL上的#號(hash)後面會顯示該頁面ID。可以直接在網址列上修改ID跳至想要的頁面，也可以自己加上其他投影片的連結；可以用瀏覽器的上一頁/下一頁/瀏覽歷程等操作</td>
  <td>可在頁面上自己加連結，但是一般跳頁時不會更新hash，所以重新整理之後投影片會跑掉，也不能用上一頁/下一頁</td>
 </tr>
<tr>
  <td style="background: #CCCCCC;">製作難度</td>
  <td>提供功能相當完整的設計介面，可方便地編輯整個大畫布。他主打的「<a href="http://prezi.com/learn/transformation-zebra-move-scale-rotate/">斑馬環</a>」(移動/旋轉/放大縮小工具，就是prezi的logo那個圓形怪怪的東西)也是此介面的一大特色</td>
  <td colspan="2">需有HTML基礎方能看懂其原理。目前入門的門檻相對高很多。(如：一個&lt;div
  class=”slide”&gt;&lt;/div&gt;為一張投影片)</td>
 </tr>
<tr>
  <td style="background: #CCCCCC;">擴充性</td>
  <td>被內建的主題限制而無法自訂字型顏色等基本屬性。但可以自行匯入flash(swf)、PDF、圖片等資源(上面提到的recipe範例就是插入了一個龐大的flash)</td>
  <td colspan="2">只要是在網頁上可以插入的東西都可以加進來！ (要多有彈性就多有彈性，但是相對的就沒有一個良好的擴充架構)</td>
</tr>
<tr>
  <td style="background: #CCCCCC;">社群/網路資源</td>
  <td style="text-align: center;">相當豐富</td>
  <td colspan="2" style="text-align: center;">無社群 (github算嗎XD)</td>
</tr>
<tr>
  <td style="background: #CCCCCC;">相容性</td>
  <td>Flash不相容於iOS。雖然有推出iPad版本，但所插入的flash、PDF等元件應該凶多吉少</td>
  <td colspan="2">HTML+CSS+JS是未來的web標準技術。唯對舊版瀏覽器相容性仍較差</td>
 </tr>
<tr>
  <td style="background: #CCCCCC;">3D特效</td>
  <td><div style="text-align: center;">
目前無提供</div>
</td>
  <td>可以指定傾角、xyz軸位置等，做出很酷炫的3D效果</td>
  <td>轉場時有3D特效</td>
 </tr>
<tr>
  <td style="background: #CCCCCC;">收費</td>
  <td><div style="text-align: center;">
freemium模式</div>
</td>
  <td><div style="text-align: center;">
免費</div>
</td>
  <td><div style="text-align: center;">
免費</div>
</td>
 </tr>
</tbody></table>
<br />
現在CSS跟JS的技術都有爆炸性的成長，其實還有很多更酷炫的方式來呈現簡報(如parallax scrolling的：<a href="http://layrr.com/">layrr</a>、<a href="http://www.nike.com/jumpman23/aj2012/">Nike AJ球鞋網頁</a>等等)。但是真的就流於網頁程式設計苦工了，需要評估有沒有值那個成本。

喜歡嗎？去fork一個你的Limpress.js吧XD！ (趕風潮XD)

延伸閱讀
----
tutorialzine（大推此站）：[用impress.js製作產品展示](http://tutorialzine.com/2012/02/css3-product-showcase/)
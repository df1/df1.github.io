---
layout: post
title: "Ext JS 4.1.0 Beta 3測試心得與IE8效能測試"
date: 2012-02-24 13:17
comments: true
categories: [ExtJS, IE]
---
<a href="/blog/2012/02/17/ext-4-performance-issue-in-ie-8/" target="_blank">承上篇</a>，Sencha果然在昨天台灣時間早上七八點發布了Ext JS 4.1 beta 3，於是我也從善如流(?)的把原本專案4.0.7的lib直接換成新的來測試。很麻煩的是，電腦只有IE9 (我很希望IE的F12切換瀏覽器版本功能可以連JS Engine都切換一下，造福一下developer；或是把這東西做在新的MS Expression Web SuperPreview也不錯) 所以要一直跑到同事座位借電腦測orz<br />
<br />
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;"><a href="http://2.bp.blogspot.com/-a2aV6Kgt3Z8/T0kpNoRDf6I/AAAAAAAABcw/5AnqNibBetc/s1600/IE-performance-on-4.0.7-vs-4.1.png" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="172" src="http://2.bp.blogspot.com/-a2aV6Kgt3Z8/T0kpNoRDf6I/AAAAAAAABcw/5AnqNibBetc/s320/IE-performance-on-4.0.7-vs-4.1.png" width="320" /></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;"><a href="http://www.sencha.com/blog/ext-js-4-1-developer-preview" target="_blank">之前官方預估</a>4.0.7至4.1的舊版IE效能提升
</td></tr>
</tbody></table>
<br />
以下是測試小結：<br />
<ol>
<li>4.0.7直接升級至4.1.0b3後，對原有的程式及畫面幾乎沒影響。</li>
<div class="separator" style="clear: both; text-align: center;">
<a href="http://3.bp.blogspot.com/-9nw9rAqgm8s/T07nk0v20VI/AAAAAAAABdM/f_uABMLb8G8/s1600/2012-3-1+%E4%B8%8A%E5%8D%88+10-33-53.jpg" imageanchor="1" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><br /></a></div>
<ul>
<li>但是community表示，afterrender事件已經不會被trigger，對某些人影響似乎很大。</li>
<li>對我們畫面有一個impact：舉例來說，有很多component我<b>有</b>設長寬，但是他外面container的layout是設成"fit"。在4.0.7他還是會乖乖占滿整個container；在4.1他大小就真的是我們設的長寬。不過這很好改，一下就全都改好了。<br /><span style="color: #444444; font-family: helvetica, arial, verdana, sans-serif; font-size: 12px; line-height: 18px;">(As for the layout. Height and Width are obeyed in 4.1, where there were ignored in 4.0)<br /><pre class="php" style="background-color: #f9f9f9; border: 1px gray dashed; color: #222222; line-height: 14px; padding-bottom: 0px; padding-left: 0px; padding-right: 0px; padding-top: 0px; padding: 5px; white-space: pre-wrap; word-wrap: break-word;">Ext.onReady(<span style="color: purple; font-weight: bold;">function</span>() {&nbsp;
    <span style="color: purple; font-weight: bold;">var</span> form = Ext.create(<span style="background-color: #e7e8ec; color: teal;">'Ext.form.Panel'</span>, {
        title: <span style="background-color: #e7e8ec; color: teal;">'panel'</span>,
        renderTo: Ext.getBody(),
        width: <span style="color: maroon;">600</span>,
        height: <span style="color: maroon;">400</span>,
        layout: <span style="background-color: #e7e8ec; color: teal;">'fit'</span>,
        items: [
            {
                xtype     : <span style="background-color: #e7e8ec; color: teal;">'panel'</span>,
                title: <span style="background-color: #e7e8ec; color: teal;">'subpanel'</span>,
                height: <span style="color: maroon;">100</span>,  <span style="color: grey; font-style: italic;">// ignored in 4.0, obeyed in 4.1</span>
                width: <span style="color: maroon;">100</span> <span style="color: grey; font-style: italic;">// same</span>
            }
        ]&nbsp;
    });
});</pre>
</span></li>
<li>Grid中如果用其中一欄的dataindex分群，而該欄又是template column的話會<a href="http://www.sencha.com/forum/showthread.php?184128-4.1B3-Error-when-grouping-by-a-template-column-in-a-grid" target="_blank">讓HTML大亂</a>。</li>
<li>剩下還有一些是我自訂css class做一些customization的，有些behavior會跟原本不一樣，在這就不詳述了。</li>
<li>講些正面的，之前
combo box picker&nbsp;很嚴重的<a href="http://www.sencha.com/forum/showthread.php?154412-Combo-Box-options-appears-in-Top-Left-Corner-in-IE-9&amp;s=c9cced2a1bd237e637bacd545fc916c0" target="_blank">在IE錯位到左上角問題</a>(當時是用<a href="http://www.sencha.com/forum/showthread.php?154412-Combo-Box-options-appears-in-Top-Left-Corner-in-IE-9&amp;p=692061&amp;viewfull=1#post692061" target="_blank">這個work-around</a>)、還有<a href="http://www.sencha.com/forum/showthread.php?152324-4.0.7-ComboBox-bug-with-load-mask" target="_blank">loading mask一直不消失問題</a>，在4.1已經完全解決了。另外4.1的scroll bar也由原本很多bug的自作聰明版改成瀏覽器原生，應該就不會有<a href="http://stackoverflow.com/questions/6745395/scrollbar-in-extjs-tree-panel-does-not-work" target="_blank">tree panel scroll消失的問題</a>了。</li>
</ul>
<li>在程式完全不改的情況下，IE8的效能似乎有『非常微幅』的提升。(微幅到不想幫同事裝fiddler測了；不知道有沒有更好用像YSlow的測效能工具？)</li>
<li>於是，進行了以下IE8效能調校嘗試</li>
<ul>
<li>把所有的store取消
autoload&nbsp;
(原本有設autoload的大部分是如combobox的common component等等的store)，想辦法減少占用的記憶體</li>
<ul>
<li>結果：效能大幅提升，但是離流暢操作還是有一大段距離。更令人遺憾的是，以目前的architecture操作到最後，該load的store還是會全load，到時候一樣會很慢。</li>
</ul>
<li>因為有使用Ext 4.0的dynamic loading，我儘量想辦法讓我UI的JS (主要是Ext Designer的component hierarchy)都在該用到的時候才load進來 (這是上一篇sencha support說值得嘗試的方法)</li>
<ul>
<li>結果：根本沒差=_______= (我的東西其實沒複雜到哪去，JS都那麼短，有差也感覺不出來orz)</li>
</ul>
<li>用他上次給我們的範例(裡面就是一個combo box複製很多份，然後吃一個靜態的json)來測試當資料多、元件多時對效能的影響</li>
<ul>
<li>結果：載入一個我認為可能是兇手的store之後(我們系統裡面的)，整個IE真的馬上變烏龜</li>
</ul>
</ul>
<li>在各瀏覽器的效能依舊是</li>
<ul>
<li>Chrome(非常順，無時無刻超級順，不愧是V8) &gt; Firefox(有時候會頓) = IE9
(有時候會頓) &gt;&gt; IE8 (還是根本無法接受)</li>
</ul>
</ol>
<br />
至於為啥要這麼辛苦地為一個爛browser煩惱呢？<br />
<br />
....orz<br />
<br />
<br />
題外話，今天早上google到了一篇簡體文章「&nbsp;<a href="http://blog.csdn.net/tianxiaode/article/details/6298340" style="background-color: white; color: black; font-family: 'Microsoft YaHei'; line-height: 30px; text-align: left; text-decoration: none;"><span class="">ExtJS 4 Beta 2預覽：Ext.Brew包</span></a>&nbsp;」。興致勃勃的直接看文章內附的範例程式之後覺得霧煞煞想說：這是甚麼鬼阿，於是點了<a href="http://www.sencha.com/blog/ext-js-4-beta-2-preview-the-ext-brew-package/" target="_blank">原文連結</a>。<br />
<br />
靠北，這是愚人節笑話阿，這位426是認真了嗎orz (雖然我LAG了XD)<br />
<br />
P.S. Sencha的確是煎茶的英文音譯
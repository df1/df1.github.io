---
layout: post
title: 網摘分享：jQuery到底是何方神聖？別怕，將他打回原形！
date: 2012-04-09 23:17
comments: true
categories: [JS, jQuery, 網摘]
---
（此文章參加[JavaScript忍之道][ninja]的『網摘分享』活動）

不知道當大家第一次聽到jQuery這個詞時，在心中浮現的第一個畫面是什麼？
是一個Java-base的query language？是一個java寫成的搜尋引擎？<del>還是一位超萌的小羅莉？（好像還沒人把它擬人化XD）</del>

無論你聽見它芳名時候的第一印象為何，當你真正見到它的容貌時，想必心中那種悸動到現在還是難以忘懷吧！讓我們再來回顧一下：  

`$("p.neat").addClass("ohmy").show("slow");`

如果場景是企業的主管正抉擇是否導入jQuery的當下，看到第一個字是大大的`$`時，心中立即的疑問就是『那這套solution的license要多少錢？』
這時，你就會非常自信專業地答道
『老闆，jQuery是不用錢的啊！只要在`$`括號裡面打上您想選擇的條件，傳回來的就是**jQuery物件**。選出來之後，您想要對它做啥都不成問題！』

<br/>
沒錯，你想把它抓去阿魯巴都可以。（請自己寫plugin） 
<br/> 
但問題來了，jQuery物件到底是啥？為啥它可以用`$`？為啥可以像上面那樣一直串下去？為啥它可以那麼強大？

###青菜底家啦
這時候，就要看對岸同胞的原始碼解析了－－[jQuery1.7系列一：jQuery 對象的實質][china] 


裡面將整個jQuery的最外圍架構拿出來討論。除了可以找到上面那些問題的解答之外，他也提到了jQuery作者使用的一些小trick
（browser不支援`undefined`？沒關係，啥都不要傳進去就是了…之類的）；另外也讓我們了解jQuery plugin的撰寫原理。

如果對文章中提到的`閉包（closure）`有看沒有懂，
可以參考TonyQ（Ptt soft_job版主）在javascript.tw聚會中對closure相關的變數scope常見問題說明。
影片後半段也對jQuery的原始碼做了解析，是講**繁體中文**的喔！（咦） 看影片吧！
<!--more-->
<iframe width="560" height="315" src="http://www.youtube.com/embed/KxItux9ZeA8?rel=0" frameborder="0" allowfullscreen></iframe>

##參考連結
*	[jQuery1.7系列一：jQuery 對象的實質][china]（簡） - 晨曦的朝陽
*	[jQuery官網][jq]
*	[JavaScript忍之道][ninja]
*	[JavaScript.tw][jstw]及其[FB社團][fb]（biweekly JS小聚）

[china]: http://xiaofei85390656-163-com.iteye.com/blog/1449221
[jq]: http://jquery.com/
[ninja]:http://ithelp.ithome.com.tw/js-ninja/
[jstw]: http://js-tw.blogspot.com/
[fb]: https://www.facebook.com/groups/javascript.tw/
---
layout: post
title: "使用Sencha Architect 2快速上手Ext JS 4.1"
date: 2012-04-23 23:17
comments: true                                 
published: false
categories: [ExtJS, JS, Ext Designer, Sencha Architect]
---

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/architect.png%}

<del>號外！所有美工（Designer）可以就地升級為架構師（Architect）！</del>（梗等下講）
Sencha在今天釋出了Ext JS 4.1版本。這篇文章將以新手的角度，加上最新工具的輔助，讓你立刻懂得如何踏上Ext JS學習之路，並快速開發一個Web Application的前端介面。（此文章也有PO在ITHome）

##Ext JS是啥
首先簡單介紹一下Ext JS好了。不知道大家有沒有用過[miroko](http://miroko.tw)？他是N年前我<del>跟水利系室友</del>非常愛用的免費服務，可以幫你掛BT並存到他所提供的網路硬碟空間內，對學術網路頻寬超級大，一秒可以衝到5~10Mb。（但是因為後來開始收費就跟它再會了） 它那種淡藍色UI，就是使用當時剛推出的Ext JS 1.0刻的。還是沒啥畫面嗎？[這裡有真相](http://www.freegroup.org/2009/06/free-online-storage-miroko/)。

###[先看看官方提供的範例長怎樣吧！](http://dev.sencha.com/deploy/ext-4.1.0-gpl/examples/)
{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/feed.png "官方的範例之一：Feed Viewer，阿就藍藍的，非常的『2007』" %}

簡而言之，Ext JS是[Sencha][]公司推出的一個純Java Script的Web前端框架，提供一般Web App會用到的UI元件（按鈕、表格、Tab…）讓你實作出想要的user flow；且便於繼承擴充，定義出自己客製的元件；另外也提供許多好用的JS utility及Ajax Data Source支援，跟後端CRUD做完美的配合。在外觀上，預設主題是簡單但有點過時的淡藍色，不過他的主題是以SASS/Compass實作，因此只要找對美工（<del>還看別人！？就是你！</del>），也是可以盡情揮灑的。目前它大多應用於企業端的內部Web Application based的資訊系統（至少敝公司將它視為標準orz，另外不知道為啥，在大陸跟日本的開發者社群似乎都相當發達）。我個人認為它的優點在於良好的繼承架構、便於快速開發及擴充，還有完整豐富的社群、官方支援及API（官方支援的好處就在於任何奇怪的問題只要PO個版就有解，瀏覽器相容等問題都不用自己去搞）；但是相對的，跟jQuery+jQuery UI的方便性比起來，它的缺點是架構較為固定，很難去把它的架構翻掉自己重新設計；另外最重要的，它在某些情況可能**要錢**。


{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/kitchensink.png "Ext JS 4.1 提供的Nepune主題" %}

<!--more-->

###授權
其實寫這篇文章真的有點掙扎，因為真的像是業配文orz。還是先來講講[授權][license]的部分：[Ext Core][]是Ext JS的核心，提供類似於jQuery的DOM操作等功能，是免費的且使用[MIT License][]；做個比喻：Ext Core之於Ext JS，就如同jQuery之於jQuery UI。雖然Ext JS也算是開源的，但它的授權就比較複雜。如果你也是用於open source開發，則適用[GPLv3][]；如果是商業用途且將原始碼視為公司proprietary，則適用[Sencha Commercial License][]；如果是要把它做成另外的商業化SDK（如[Ext.NET][]），Sencha也提供OEM License。而今天要講的Sencha Architect，則是Sencha推出的架構設計工具，[一套要價$399鎂][architect license]，但提供免費試用。

[Sencha]:http://www.sencha.com
[license]:http://www.sencha.com/products/extjs/license/
[Ext Core]:http://www.sencha.com/products/extcore
[MIT License]:http://www.opensource.org/licenses/mit-license.php
[GPLv3]:http://www.gnu.org/copyleft/gpl.html
[Sencha Commercial License]:http://www.sencha.com/legal/sencha-commercial-software-license-agreement/
[Ext.NET]:http://www.ext.net/
[architect license]:http://www.sencha.com/products/architect/license/


##開始使用Sencha Architect做第一個Ext JS的UI


[neptune]:http://docs.sencha.com/ext-js/4-1/extjs-build/examples/kitchensink/

  
進入正題，前幾天Sencha發表了最新的Sencha Architect 2 （梗在這，因為它以前叫Ext Designer，現在升級變Architect XD）。它是一個強大的東西，只要拉一拉、摳一摳，十分鐘就可以把UI刻好了。除了拉UI之外，它之所以會改名為Architect，是因為它可以直接在裡面寫code、做event handling、甚至定義MVC架構。（另外一大賣點是可以開發Sencha Touch當成手機App，但是本周主題是Web App，所以就不提這段XD）這篇文也不會涉獵到太深的架構部分，目標先設定在快速上手並做出一個會動的Web UI。話不多說，讓我們開始吧（羞）

**PS. 按圖片都可以放大**

###下載並安裝
[載點在此][architect]，試用前須註冊[Sencha Forum](http://www.sencha.com/forum/)的帳號。它本身是以QT及其內建Webkit寫成的跨平台程式，可以在Windows/MacOS/Linux上執行。將程式打開之後，可以看到一個很熟悉的WYSIWYG形式編輯器：左邊是工具箱、中間是畫布、右上是階層圖、右下是一欄欄的屬性。

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/wysiwyg.png "Sencha Architect跑起來的樣子"%}


###開始拉UI


{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/viewport.png "把整個Web App畫面撐開的東西是Viewport"%}


{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/region.png ""%}


{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/id.png ""%}

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/event.png ""%}

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/code.png ""%}


###佈署到local並預覽

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/settings.png "專案設定畫面"%}

##看API

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/api.png "API"%}

##Application及MVC架構
###參考連結
*	[MVC Architecture]:http://docs.sencha.com/ext-js/4-1/#!/guide/application_architecture

##整合後端開發
在瞭解他匯出的行為之後，就會發現其實很容易跟後端開發的專案進行整合。其中會遇到的一個問題就是他跑AMD動態載入JS Class時的路徑是否跟專案中的目錄架構是一樣的，這時候就要對`Ext.application`中的`appFolder`屬性做調整。[我去年的一篇文章][eclipse]是以Java EE的Web project為例進行與Ext Designer 1.2進行整合，主要的技術堆疊大略是（純回憶，僅供參考）：前後端以REST進行溝通（JAX-RS）；Servlet及JAVA部分採用Spring 3來做DI及AOP；ORM使用JPA 2；local測試環境使用[run-jetty-run][]。
[eclipse]:http://df1.github.com/blog/2012/02/16/integrate-ext-designer-with-java-web-project-in-eclipse/
[run-jetty-run]:http://code.google.com/p/run-jetty-run/

##IE8效能問題
這年頭很多人都喜歡用Firefox或Chrome進行開發，但是別忘了，你的user可沒那麼先進。更令人沮喪的是Ext JS 4.0.0~4.0.7版本在IE6~8都有嚴重的效能問題。Sencha的解釋如下：
>	Ext JS 4 features a brand new rendering pipeline that is significantly more structured and extensible than the rendering process in Ext JS 3. All Components now render the same way, and are driven by XTemplates. They also follow a common hook point regime, enabling the framework and developers to extend or hook into the render process for each Component.
>	
>	While the new rendering architecture is a big step forward, it did create slow performance in some cases. In 4.0.1 and before the order of operations in the rendering process was not as efficient as it could have been, resulting in many more DOM updates than are actually needed. In 4.0.2 we have corrected this behavior, yielding significant render speed improvements.
>	
>	We have already identified further optimizations to the rendering pipeline that will be incorporated into Ext JS 4.0.3 and beyond. Performance is very important to all of us and making the framework as fast as we know it can be will remain a top priority for the team.

Ext JS 4.1版本主要就是在解決在IE的效能問題，現在已經有改善許多。 但是，在開發期間，良心建議您偶爾還是把IE開來跑跑看，免得像我當初一樣，發現時已經距<del>引咎辭職</del>上線的時間不遠矣！


Ext.TaskManager




##參考連結
*	[Ext JS官網][extjs]
*	[Sencha Architect][architect]

[architect]:http://www.sencha.com/products/architect/
[extjs]:http://www.sencha.com/products/extjs/
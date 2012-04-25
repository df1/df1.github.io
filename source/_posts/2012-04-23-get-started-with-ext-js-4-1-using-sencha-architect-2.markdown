---
layout: post
title: "使用Sencha Architect 2快速上手Ext JS 4.1"
date: 2012-04-23 23:17
comments: true                                 
published: false
categories: [ExtJS, JS, Ext Designer, Sencha Architect]
---

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/architect.jpg%}

<del>號外！所有美工（Designer）可以就地升級為架構師（Architect）！</del>（梗等下講）
這篇文章將以新手的角度，加上最新工具的輔助，讓你立刻懂得如何開始Ext JS學習之路，來快速開發一個Web Application的前端介面。

##Ext JS是啥
首先簡單介紹一下Ext JS好了。不知道各位有沒有用過[miroko](http://miroko.tw)？他是N年前我<del>跟水利系室友</del>非常愛用的免費服務，可以幫你掛BT並存到他所提供的網路硬碟空間內，對學術網路頻寬超級大，一秒可以衝到5~10Mb。（但是因為後來開始收費就跟它再會了） 它那種淡藍色UI，就是使用當時剛推出的Ext JS 1.0刻的。還是沒啥畫面嗎？[這裡有真相](http://www.freegroup.org/2009/06/free-online-storage-miroko/)。

###開始用Ext之前，[先看看官方提供的範例吧！](http://dev.sencha.com/deploy/ext-4.1.0-gpl/examples/)

簡而言之，Ext JS是[Sencha][]公司推出的一個純Java Script的Web前端框架，提供一般Web App會用到的UI元件（按鈕、表格、Tab…）讓你實作出想要的user flow；且便於繼承擴充，定義出自己客製的元件；另外也提供許多好用的JS utility及Ajax支援，跟後端CRUD做完美的配合。在外觀上，預設主題是簡單但有點過時的淡藍色，不過他的主題是以SASS/Compass實作，因此只要找對美工（<del>還看別人！？就是你！</del>），也是可以盡情揮灑的。目前它大多應用於企業端的內部Web Application based的資訊系統（至少敝公司將它視為標準orz，另外不知道為啥，在大陸跟日本的開發者社群似乎都相當發達）。我個人認為它的優點在於良好的繼承架構、便於快速開發及擴充，還有完整豐富的社群、官方支援及API（任何奇怪的問題只要PO個版就有解，瀏覽器相容等問題都不用自己去搞）；但是相對的，跟jQuery+jQuery UI的方便性比起來，它的缺點是架構較為固定，很難去把它的架構翻掉自己重新設計；另外最重要的，它在某些情況可能**要錢**。

<!--more-->

###授權
其實寫這邊文章真的有點掙扎，因為有點像是業配文orz。還是先來講講[授權][license]的部分：[Ext Core][]是Ext JS的核心，提供類似於jQuery的DOM操作等功能，是免費的且使用[MIT License][]；做個比喻：Ext Core之於Ext JS，就如同jQuery之於jQuery UI。雖然Ext JS也算是開源的，但它的授權就比較複雜。如果你也是用於open source開發，則適用[GPLv3][]；如果是商業用途且將原始碼視為公司proprietary，則適用[Sencha Commercial License][]；如果是要把它做成另外的商業化SDK（如[Ext.NET][]），Sencha也提供OEM License。而今天要講的Sencha Architect，則是Sencha推出的架構設計工具，[一套要價$399鎂][architect license]，但提供免費試用。

[Sencha]:http://www.sencha.com
[license]:http://www.sencha.com/products/extjs/license/
[Ext Core]:http://www.sencha.com/products/extcore
[MIT License]:http://www.opensource.org/licenses/mit-license.php
[GPLv3]:http://www.gnu.org/copyleft/gpl.html
[Sencha Commercial License]:http://www.sencha.com/legal/sencha-commercial-software-license-agreement/
[Ext.NET]:http://www.ext.net/
[architect license]:http://www.sencha.com/products/architect/license/


##開始使用Sencha Architect做第一個UI
{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/capture.png "在Mac中設計Web Application，手動套用Ext 4.1的neptune主題，並用safari預覽"%}

[neptune]:http://docs.sencha.com/ext-js/4-1/extjs-build/examples/kitchensink/
  
進入主題，前幾天Sencha發表了最新的Sencha Architect 2 （以前叫Ext Designer）。他是一個強大的東西，只要拉一拉、摳一摳，十分鐘就可以把UI刻好了。




##看API

##Application及MVC架構


##整合後端開發


##IE8效能問題
>	Ext JS 4 features a brand new rendering pipeline that is significantly more structured and extensible than the rendering process in Ext JS 3. All Components now render the same way, and are driven by XTemplates. They also follow a common hook point regime, enabling the framework and developers to extend or hook into the render process for each Component.
>	
>	While the new rendering architecture is a big step forward, it did create slow performance in some cases. In 4.0.1 and before the order of operations in the rendering process was not as efficient as it could have been, resulting in many more DOM updates than are actually needed. In 4.0.2 we have corrected this behavior, yielding significant render speed improvements.
>	
>	We have already identified further optimizations to the rendering pipeline that will be incorporated into Ext JS 4.0.3 and beyond. Performance is very important to all of us and making the framework as fast as we know it can be will remain a top priority for the team.



Ext.TaskManager




##參考連結
*	[Ext JS官網][extjs]

[extjs]:http://www.sencha.com/products/extjs/
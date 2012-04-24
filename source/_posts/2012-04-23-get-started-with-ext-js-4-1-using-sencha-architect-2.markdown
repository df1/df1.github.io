---
layout: post
title: "使用Sencha Architect 2快速上手Ext JS 4.1"
date: 2012-04-23 23:17
comments: true                                 
published: false
categories: [ExtJS, JS, Ext Designer, Sencha Architect]
---
號外！所有美工（Designer）可以就地升級為架構師（Architect）！（梗等下講）

首先簡單介紹一下Ext JS好了。不知道各位有沒有用過miroko？他是N年前我<del>跟水利系室友</del>非常愛用的免費服務，可以幫你掛BT並存到他所提供的網路硬碟空間內，對學術網路頻寬超級大。（但是因為後來開始收費就跟它再會了） 它那種淡藍色UI，就是使用當時剛推出的Ext JS 1.0刻的。還是沒啥畫面嗎？[這裡有真相](http://www.freegroup.org/2009/06/free-online-storage-miroko/)。

簡而言之，Ext JS是一個純Java Script的Web前端框架，提供一般Web App會用到的UI元件（按鈕、表格、Tab…），且便於繼承擴充，定義出自己客製的元件；另外也提供許多好用的JS utility及Ajax支援，跟後端CRUD做出完美的配合。在外觀上，預設主題是簡單但有點過時的淡藍色，不過他的主題是以SASS/Compass實作，因此只要找對美工，也是可以盡情揮灑的。目前他大多應用於企業端的內部Web Application based的資訊系統（至少敝公司將它視為標準orz，另外不知道為啥，在大陸跟日本的開發者社群都相當發達）。我個人認為它的優點在於架構的可塑性、便於快速開發及擴充，還有完整豐富的社群及官方支援（任何奇怪的問題只要PO個版就有解，瀏覽器相容等問題都不用自己去搞）；但是相對的，若是在商業用途，它要錢。

其實寫這邊文章真的有點掙扎，因為感覺有點像在幫它打廣告。



該進入主題了。前幾天Ext JS的公司發表了最新的Sencha Architect 2 (以前叫Ext Designer)。他是一個強大的東西，只要拉一拉、摳一摳，十分鐘就可以把UI刻好了。

>	Ext JS 4 features a brand new rendering pipeline that is significantly more structured and extensible than the rendering process in Ext JS 3. All Components now render the same way, and are driven by XTemplates. They also follow a common hook point regime, enabling the framework and developers to extend or hook into the render process for each Component.
>	
>	While the new rendering architecture is a big step forward, it did create slow performance in some cases. In 4.0.1 and before the order of operations in the rendering process was not as efficient as it could have been, resulting in many more DOM updates than are actually needed. In 4.0.2 we have corrected this behavior, yielding significant render speed improvements.
>	
>	We have already identified further optimizations to the rendering pipeline that will be incorporated into Ext JS 4.0.3 and beyond. Performance is very important to all of us and making the framework as fast as we know it can be will remain a top priority for the team.


http://docs.sencha.com/ext-js/4-1/extjs-build/examples/kitchensink/


Ext.TaskManager

http://www.sencha.com/products/extjs/license/
http://www.sencha.com/products/architect/license/
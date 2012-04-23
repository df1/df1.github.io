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

簡而言之，Ext JS是一個Web前端框架，一般Web Application所有會用到的UI元件幾乎都有提供（按鈕、表格、Tab…），且非常方便繼承擴充；另外也提供許多好用的JS utility及Ajax支援，可以整合任何



昨天Ext JS的公司發表了最新的Sencha Architect 2 (以前叫Ext Designer)。他是一個強大的東西，只要拉一拉、摳一摳，十分鐘就可以把UI刻好了。

>	Ext JS 4 features a brand new rendering pipeline that is significantly more structured and extensible than the rendering process in Ext JS 3. All Components now render the same way, and are driven by XTemplates. They also follow a common hook point regime, enabling the framework and developers to extend or hook into the render process for each Component.
>	
>	While the new rendering architecture is a big step forward, it did create slow performance in some cases. In 4.0.1 and before the order of operations in the rendering process was not as efficient as it could have been, resulting in many more DOM updates than are actually needed. In 4.0.2 we have corrected this behavior, yielding significant render speed improvements.
>	
>	We have already identified further optimizations to the rendering pipeline that will be incorporated into Ext JS 4.0.3 and beyond. Performance is very important to all of us and making the framework as fast as we know it can be will remain a top priority for the team.


http://docs.sencha.com/ext-js/4-1/extjs-build/examples/kitchensink/


Ext.TaskManager

http://www.sencha.com/products/extjs/license/
http://www.sencha.com/products/architect/license/
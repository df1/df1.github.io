---
layout: post
title: "使用Sencha Architect 2快速上手Ext JS 4.1"
date: 2012-04-23 23:17
comments: true
categories: [ExtJS, JS, Ext Designer, Sencha Architect]
---

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/architect.png%}

<del>號外！所有美工（Designer）可以就地升級為架構師（Architect）！</del>（梗等下講）
Sencha在今天釋出了Ext JS 4.1版本。這篇文章將以新手的角度，加上最新工具的輔助，讓你立刻懂得如何踏上Ext JS學習之路，並快速開發一個Web Application的前端介面。（此文章也有PO在ITHome）

<!--more-->
##Ext JS是啥
首先簡單介紹一下Ext JS好了。不知道大家有沒有用過[miroko](http://miroko.tw)？他是N年前我<del>跟水利系室友</del>非常愛用的免費服務，可以幫你掛BT並存到他所提供的網路硬碟空間內，對學術網路頻寬超級大，一秒可以衝到5~10Mb。（但是自從開始收費就跟它再會了） 它那種淡藍色UI，就是使用當時剛推出的Ext JS 1.0刻的。還是沒啥畫面嗎？[這裡有真相](http://www.freegroup.org/2009/06/free-online-storage-miroko/)。


###進入正題前，[先看看官方提供的範例長怎樣吧！](http://dev.sencha.com/deploy/ext-4.1.0-gpl/examples/)
{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/feed.png "官方的範例之一：Feed Viewer，阿就藍藍的，非常的『2007』" %}

簡而言之，Ext JS是[Sencha][]公司推出的一個純JS的Web前端框架，提供一般Web App會用到的UI元件（按鈕、表格、Tab…）讓你實作出想要的user flow；且便於繼承擴充，定義出自己客製的元件；另外也提供許多好用的JS utility及Ajax Data Source支援，跟後端CRUD做完美的配合。在外觀上，預設主題是簡單但有點過時的淡藍色，不過他的主題是以SASS/Compass實作，因此只要找對美工（<del>還看別人！？就是你！</del>），也是可以盡情揮灑的。目前它大多應用於企業端的內部Web Application based的資訊系統（至少敝公司將它視為UI標準之一orz，另外不知道為啥，在大陸跟日本的開發者社群似乎都相當發達）。我個人認為它的優點在於良好的繼承架構、便於快速開發及擴充，還有完整豐富的社群、官方支援及API（用商業化套件的好處就在於任何奇怪、無恥的問題只要PO個版就有解，瀏覽器相容等問題都不用自己去搞，也不會叫你RTFM）；但是相對的，跟jQuery+jQuery UI的方便性比起來，它的缺點是架構較為固定，很難去把它的架構翻掉自己重新設計；另外最重要的，它在某些情況可能**要錢**。


{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/kitchensink.png "Ext JS 4.1 提供的Nepune主題" %}


###授權
其實寫這篇文章真的有點掙扎，因為真的像是業配文orz。還是先來講講[授權][license]的部分：[Ext Core][]是Ext JS的核心，提供類似於jQuery的DOM操作等功能，是免費的且使用[MIT License][]；打個比方：Ext Core之於Ext JS，就如同jQuery之於jQuery UI。雖然Ext JS也算是開源的，但它的授權就比較複雜。如果也是用於open source開發，則適用[GPLv3][]；如果是商業用途且將原始碼視為公司proprietary，則適用[Sencha Commercial License][]；如果是要把它做成另外的商業化SDK（如[Ext.NET][]），Sencha也提供OEM License。而今天要講的Sencha Architect，則是Sencha推出的架構設計工具，[一套要價$399鎂][architect license]，但提供免費試用。

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
[載點在此][architect]，試用前須註冊[Sencha Forum](http://www.sencha.com/forum/)的帳號。它本身是以QT及其內建Webkit寫成的跨平台程式，可以在Windows/MacOS/Linux上執行。將程式打開之後，可以看到一個很熟悉的WYSIWYG所見及所得編輯器：左邊是工具箱、中間是畫布、右上是階層圖、右下是一欄欄的屬性。

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/wysiwyg.png "Sencha Architect跑起來的樣子"%}


###開始拉UI
迫不及待要從左邊拉東西進來了吧？首先，身為一個web app，會需要的是一個`viewport`。它可以把整個網頁的畫面撐開，讓我們在裡面做layout。
{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/viewport.png "把整個Web App畫面撐開的東西是Viewport"%}

繼續瘋狂拉東西進來之前，還是要先對Ext JS所提供的各種layout有基本的認識。這個[Ext Layout Browser](http://dev.sencha.com/deploy/ext-4.1.0-gpl/examples/layout-browser/layout-browser.html)裡面有各種layout的DEMO及基本介紹。一般來說，我們常常在web app的最外面使用Border Layout，將畫面分成東南西北中<del>發板</del>幾塊（region）。

要設定這個viewport的layout類型，可以在右邊屬性中找到layout下拉選取，或是在畫布上的藍色齒輪跳出的快速設定popup中選取。接下來真的就可以從左邊亂拉元件了。要注意的是，若是在一個border layout的container裡面，它需要有一個`region: 'center'`	（中央）的子元件；其他東西南北則不一定要有。[拉完之後可能長這樣](http://dev.sencha.com/deploy/ext-4.1.0-gpl/examples/layout/complex.html)。

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/region.png "Border Layout的示意圖，紅色框起來的地方套用了border layout"%}

以下面的圖為例，我西邊放了一個`Tree Panel`，將它的`collapsible`（可收合）及`split`（邊緣分割線）屬性設為`true`；中間則放了一個包含三個tab的`Tab Panel`。在第一個Tab，我將它的layout設為absolute，這時候畫面上會出現格線方便我們直接拖拉調整子元件的位置。若要將表單欄位貼到最右邊，可以將`anchor`屬性設為100%。

在我們拉表單的時候，可以在畫布上的元件按右鍵使用duplicate功能快速複製；複製後可用transform將其轉為其他類別的元件（如：將combo box下拉選單欄位轉為date field日期欄位。它們都是繼承`Ext.form.field.Base`）。


###看看內建的API文件
Sencha Architect的一大優點就是它本身整合了Ext的documentation，大幅減少了設計時翻文件的痛苦。如下圖，在左邊的工具箱中點每個元件後，下方都會出現簡單說明；另外，在屬性視窗中的每個屬性旁都有一個問號，滑鼠移上去也會秀出簡單說明。若是想看完整的document，也可以點連結直接跳到線上API去看。
{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/api.png "Sencha Architect中內建的documentation功能"%}

###[看看很好很強大的線上API文件吧！](http://docs.sencha.com/ext-js/4-1/)
Ext的原始碼本身是以JS Doc形式做self-documentation的。Sencha也開發了一個工具叫JS Duck將原始碼直接變成像這樣的API網站。裡面可以看到它提供所有的功能，元件Class的繼承hierarchy，還有範例以及別人的評論。這裡面真的很值得探索！

###事件處理
若是我想讓user按按鈕之後，將左邊的tree收起來，該怎麼做？（例子很爛請包涵XD）
首先我們先將左邊的tree panel取一個ID叫`myTreePanel`。有了ID之後，在任何地方都可以使用`Ext.getCmp('元件ID')`來取得該元件，並進行操作。（題外話，當然這不是唯一方法。若是熟悉CSS selector，也可以用類似jQuery的方法來取得元件，如`query`、`up`、`down`等等。這種寫法相當適合controller使用。）

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/id.png "給咱們Tree panel一個ID"%}

接下來，在button的屬性視窗中加入一個event handler如下圖。一個按鈕所有可能觸發的event全部在下拉選單列給我們看了！很直覺地，click應該就是我們要的（通常試試看就知道是不是我們要的了）。
{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/event.png "給button加一個click的event"%}

然後就可以開始寫code了！這一行是利用剛剛設定的ID來拿到左邊的tree，並將它收合。
{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/code.png "將左邊的tree收合"%}
簡單吧！到這邊已經可以lay出複雜且會動的UI了！

###Data Model與Store
在企業的web application中，前端需要的資料大多從後端DB過來。只要是有『吃資料』的元件，都需指定一個store給它，裡面存有前端畫面需要的所有資料。在store裡面需定義該store所需要存取的欄位（可以直接在store的fields屬性中定義欄位，也可以指定一個定義好的Data Model給它。）。以combo box（下拉選單）為例，它通常需要兩個欄位：顯示文字與實際值。

依照與後端溝通的方式，Ext提供了各種不同的proxy供store使用。另外根據回傳的資料形式不同，也提供了不同的reader供proxy使用。像我最常用的應該是Ajax Proxy搭配Json Reader。舉例來說，若是我們要做一個性別的選單，而資料由後端某個URL傳回來的Json格式如下：
	{
		"total": 2,
		"data": [
			{"gender": "M", "genderText": "男性"},
			{"gender": "F", "genderText": "女性"}
		]
	}
則需在store新增兩個field：`gender`和`genderText`；在proxy的`url`打上該URL；在reader的`root`屬性設成`"data"`（請看上面的json，我們要的資料是在data裡面）。

我知道這又是個爛例子，因為性別其實hard-code就好了XD。下圖是hard-code的combo box store作法：
建立一個Json Store，在field內加兩個欄位；在data裡面hard-code我們的資料；將proxy砍掉。

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/store.jpg "Store裡的設定"%}

Combo box部分，將store指向上面定義的MyJsonStore；將`displayField`跟`valueField`分別設成我們的顯示文字與實際值欄位名；將`queryMode`設成`"local"`（若設成remote，當user在combo box敲字篩選時，會在url後面加上?query=xxx然後去問後端，方便後端做篩選處理）。

{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/combo.jpg "Combo box裡的設定"%}

###佈署到local並預覽
剛看到Sencha Architect畫面時，一定會想試試看preview跟deploy按鈕到底是在做啥。其實也沒啥，就是幫我們deploy到web server再開啟瀏覽器預覽。須先在settings設定路徑如下圖。另外建議將Ext JS Path改成4.1的`http://extjs.cachefly.net/ext-4.1.0-gpl/`。
{%img /attachments/2012-04-23-get-started-with-ext-js-4-1-using-sencha-architect-2/settings.png "專案設定畫面"%}


##Application及MVC架構
雖然這超出本文涵蓋的主題，但還是稍微談一下好了。當Web App規模大到一定程度時，想必會開始思考如何組織程式碼，讓它可讀性變高，還有方便maintain、動態載入及效能等等架構面的問題。若是有看過backbone.js、require.js、knockout.js等工具的介紹文，應該會對現在流行的架構概念有所認識。其實Ext JS也有它自己類似AMD的機制；如果要做類似backbone的hash routing，也可以透過`Ext.history`（但它還是用hidden iframe囧 要支援舊瀏覽器沒辦法）；最重要的，它的MVC架構設計也是相當優秀，值得另開專文深入討論之。若想瞭解，可以參考[這篇官方介紹][mvc]。看完之後，相信會迫不及待地從左邊工具箱拖出controller來玩玩看吧！

###好文分享
*	[Ext JS 4的Application/MVC架構概觀][mvc]
*	[Deft JS: Loosely Coupled MVC through Dependency Injection](http://www.sencha.com/blog/deftjs-loosely-coupled-mvc-through-dependency-injection) -- John Yanarella
[mvc]:http://docs.sencha.com/ext-js/4-1/#!/guide/application_architecture

下面這幾個archticture tool相關文章也非常值得看看，但跟Ext沒關係
*	[Backbone.js X RequireJS Quick Guide](http://speakerdeck.com/u/jaceju/p/backbonejs-x-requirejs-quick-guide) -- 大澤木小鐵
*	介紹Knockout.js的MVVM：[Understanding MVVM – A Guide For JavaScript Developers](http://addyosmani.com/blog/understanding-mvvm-a-guide-for-javascript-developers/) -- Addy Osmani

##整合後端開發
在瞭解他匯出的行為之後，就會發現其實很容易跟後端開發的專案進行整合。其中會遇到的一個問題就是他跑AMD動態載入JS Class時的路徑是否跟專案中的目錄架構是一樣的，這時候就要對`Ext.application`中的`appFolder`屬性做調整。[我去年的一篇文章][eclipse]是以Java EE的Web project為例，將Ext Designer 1.2整合Eclipse進行開發。印象中當時主要的技術堆疊大略是（純回憶，僅供參考）：前後端以REST進行溝通（JAX-RS）；Servlet及JAVA部分採用Spring來做DI及AOP；ORM使用JPA 2；local測試環境使用[run-jetty-run][]。
[eclipse]:http://df1.github.com/blog/2012/02/16/integrate-ext-designer-with-java-web-project-in-eclipse/
[run-jetty-run]:http://code.google.com/p/run-jetty-run/


###好文分享
*	[Node.js+mongodb+EditGrid範例](http://docs.sencha.com/ext-js/4-1/#!/guide/editable_grid)

##IE8效能問題
這年頭很多人都愛用Firefox或Chrome進行開發，但是很遺憾的，咱們user可沒那麼先進。更令人沮喪的是Ext JS 4.0至4.0.7版本在IE8以下都有嚴重的效能問題。Sencha的解釋如下：
>	Ext JS 4 features a brand new rendering pipeline that is significantly more structured and extensible than the rendering process in Ext JS 3. All Components now render the same way, and are driven by XTemplates. They also follow a common hook point regime, enabling the framework and developers to extend or hook into the render process for each Component.
>	
>	While the new rendering architecture is a big step forward, it did create slow performance in some cases. In 4.0.1 and before the order of operations in the rendering process was not as efficient as it could have been, resulting in many more DOM updates than are actually needed. In 4.0.2 we have corrected this behavior, yielding significant render speed improvements.
>	
>	We have already identified further optimizations to the rendering pipeline that will be incorporated into Ext JS 4.0.3 and beyond. Performance is very important to all of us and making the framework as fast as we know it can be will remain a top priority for the team.

因此這次公開的4.1版主要就是focus在解決在IE的效能問題，現在已經有改善許多。 但是，在開發期間，良心建議您偶爾還是把IE開來跑跑看，免得像小弟當初一樣，發現時已經距<del>引咎辭職</del>上線的日子不遠矣！




##參考連結
*	[Ext JS官網][extjs]
*	[Sencha Architect][architect]

[architect]:http://www.sencha.com/products/architect/
[extjs]:http://www.sencha.com/products/extjs/
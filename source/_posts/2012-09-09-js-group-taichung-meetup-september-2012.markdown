---
layout: post
title: "JS Group Taichung Meetup September 2012"
date: 2012-09-11 14:39
comments: true
categories: [JS, JS Group, Events]
---
這次是[JS Group](http://javascript.tw)在台中舉辦的第五次聚會。這個聚會除了每隔週在台北之外，通常選在每個月的第一個禮拜六下午會來到台中舉行。今天大家一樣是在老地方的水舞饌三樓，一起吃吃喝喝、coding、聊天。而這次的講者就是主辦的TonyQ大大。

TonyQ本身因為工作的關係，對jQuery等前端技術相當有經驗，所以大多分享還是會以jQuery為主。不過這個活動中大家討論的內容還是可以跳脫jQuery、跳脫library，廣泛地去討論所有JS或前端技術。今日主題就是網站裡很本質的要素：JS表單驗證、彈出式視窗。


![FB上的盛況XD](http://www.xapps.tw/files/node_image/52/js.png)

<!--more--> 

##甚麼是表單驗證？

以registrano報名表單為例：欄位分為必填、非必填。這就是最常見需要驗證的地方。表單驗證需要在兩個地方實作：

1. 送出前的內容：在前端驗證並提示使用者。

2. 送出後在伺服器端的資料阻擋：這裡才是最主要的驗證地點，真正的防線。

 

但是今天著重在前端表單驗證，目的是友善地導引使用者填好表單。（記得要友善導引喔，不要跳出「哈哈哈你看看你」這種意味不明的提示XD）

 

一般的表單都會有個`<form>`元素。我們可以用以下兩種作法來在submit之前做驗證：

把按鈕改成不是`action="submit"`，而是`onclick`時另外呼叫函式驗證後再真正去呼叫`form.submit()`
在submit的event做一些處理，如果失敗就終止submit。
	$('#register-form').on('submit', function(){
		var validated = validate();
		if(!validated){
			return false; //在jQuery中return false常常是終止該event
		}
	});

 

	function validate(){
		if($.trim($('person_name').val())==''){
			alert('請填寫姓名');
			$('person_name').focus();
			return false;
   		}
   		return true;
	}

 

驗證日期格式也有兩招：
1.試著把他轉成Date物件
	if(new Date($('#date-field').val()))
2.用Regular Expression
	if(/[0-9]{4}\/[0-9]{1,2}\/[0-9]{1,2}/.test($('#date-field').val()))

 

不過大家都知道，表單驗證是很複雜的事，純粹用regular expression是做不到的；
再者，有多少欄位就要寫多少行的if clause，是一件很痛苦的事情。
以下舉了一些現成的表單驗證工具，看別人怎麼簡化這個東西。

###[jQuery Validation](http://jquery.bassistance.de/validate/demo/)：老字號(2006~2007就出現了)
	<input id="name" type="text" minlength="2" required>

加上一些custom attribte後，它就會幫你檢查欄位、email驗證、URL驗證、若驗證不通過做highlight。

錯誤訊息的自訂：

	$(".selector").validate({
	   rules: {
	      name: "required",
	      email: {
	         required: true,
	         email: true
	      }
	   },
	   messages: {
	      name: "Please specify your name",
	      email: {
	         required: "We need your email address to contact you",
	         email: "Your email address must be in the format of name@domain.com"
	      }
	   }
	});

看他怎麼驗證email：source code裡面有一個非常經典的驗證email的超級長regular expression：


	/^((([a-z]|\d|[!#\$%&'\*\+\-\/=\?\^_`{\|}~]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])+(\.([a-z]|\d|[!#\$%&'\*\+\-\/=\?\^_`{\|}~]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])+)*)|((\x22)((((\x20|\x09)*(\x0d\x0a))?(\x20|\x09)+)?(([\x01-\x08\x0b\x0c\x0e-\x1f\x7f]|\x21|[\x23-\x5b]|[\x5d-\x7e]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])|(\\([\x01-\x09\x0b\x0c\x0d-\x7f]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF]))))*(((\x20|\x09)*(\x0d\x0a))?(\x20|\x09)+)?(\x22)))@((([a-z]|\d|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])|(([a-z]|\d|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])([a-z]|\d|-|\.|_|~|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])*([a-z]|\d|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])))\.)+(([a-z]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])|(([a-z]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])([a-z]|\d|-|\.|_|~|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])*([a-z]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])))$/i

 

jQuery Validation整體評價：很陽春、很好用

###[jQuery Validation Engine](https://github.com/posabsolute/jQuery-Validation-Engine)
簡單用法：

	<input value="someone@nowhere.com" class="validate[required,custom[email]]" type="text" name="email" id="email" />

 

現在時代不一樣，他也提供了data-attribute的寫法：

	<input type="email" name="email" id="email" data-validation-engine="validate[required,custom[email]]" data-errormessage-value-missing="Email is required!"  data-errormessage-custom-error="Let me give you a hint: someone@nowhere.com"    data-errormessage="This is the fall-back error message."/>

###最後提供一些User Experience上的小叮嚀：

錯誤訊息要讓user看得懂。
錯誤要一目瞭然，要避免讓user做try-and-error：改正之後才告訴user下一個錯誤。
驗證在前後端都要完整地去做。
送出之後把整個表單保留下來。
字數限制：字數超過不要阻擋使用者輸入，提示或送出前驗證即可。
最理想的驗證方式：輸入之後馬上告訴使用者對或錯、並提供auto complete。
題外話，如果時常因為辛苦填完表單因為驗證不通過被reset而感到挫折，可以試試這個瀏覽器附加元件：Form recovery (for firefox/chrome)XD

###小結

常常會有十個以上的方法來解同一個問題。實務上，還是需要看需求及團隊skillset來調整實作方法。另外，表單驗證其實不限於有`<form>`的形式(如：FB社團加入成員功能，是由一個輸入框+按鈕構成的)

表單設計好書推薦：[「Web表單設計:點石成金的藝術」](http://www.pcstore.com.tw/69book/M07276721.htm)

 

  
 
##彈出式視窗

彈出式視窗說穿了就是在有限的畫面內浮出一個區間：其他的不重要啦，讓專業的來！

* [jQuery](http://leandrovieira.com/projects/jquery/lightbox/) lightbox：最常見的選擇
* [Block UI](http://www.malsup.com/jquery/block/)
* jQuery Alert：做簡單的提示或確認視窗
 

這些彈出式視窗的技術原理都是利用很大的overlay遮在body上面，有透明度(`opacity:0.6;`)，固定位置(`position:fixed;`)。

但是，popup本身不是在overlay裡面(因為這樣child也會有透明度)；

而是使用很大的`z-index`讓他浮上來(所以網頁裡面元素的`z-index`請儘量設在100以內，不然可能會讓mask蓋不住它)。

 

特例：flash常常蓋不住怎麼辦？

flash屬性的`WMode`要改成`transparent`。

 

###`window.alert`與`window.open`的迷思

若使用JS下一般的alert，會讓整個JS會停下來等你。用上述popup及假alert是沒辦法做到這種synced的效果的。

`window.open`會被瀏覽器封鎖彈出視窗，所以儘量不要用。但是如果是伴隨著click event，一般瀏覽器預設不會阻擋。不過還是「能不用就不用」。

如果是開同一個domain的URL，可以藉由指定target name來取得控制。

	window.test = window.open('about:blank','test');

`window.open`時候會回傳一個window物件的reference。有window就會有document，有document就會有body，有body就可以改它裡面的東西。也就是說母視窗可以改子視窗。

反過來，小孩也可以看到父親：`window.opener`。所以小孩覺得自己被改了很不爽，也可以改他老爸！
(要小心跟`window.parent`搞混。`window.parent`拿到的是frame或iframe的parent window。不過這部分規格似乎有變動，連W3C目前都還是用`window.open`當範例)

 

還有一個特異功能不太有人知道，看起來很炫但是千萬不要亂用：用`window.opener.$`去拿它老爸的jQuery來用！如此一來，$的scope是在外面。如果裡面小孩真的要用，需要把小孩自己的`document`傳進去：

	window.opener.$(document).find('body')[0];

有種情境適合這樣做：發文章的預覽功能

雖然看起來子母視窗可以互通有無是很炫的事情，但是他們記憶體也可以互通有無。

所有的瀏覽器(包含IE6)都可以這樣做，不過policy還是同網域才可以用`window.opener`。`window.opener.$(document).find('body')[0];`

有種情境適合這樣做：發文章的預覽功能

雖然看起來子母視窗可以互通有無是很炫的事情，但是他們記憶體也可以互通有無。

所有的瀏覽器(包含IE6)都可以這樣做，不過policy還是同網域才可以用`window.opener`。

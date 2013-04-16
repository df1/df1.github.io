---
layout: post
title: "Code Snippet for Dumping Facebook Album"
date: 2013-04-05 21:14
comments: true
categories: ["js","facebook"]
---

最近終於有一點點動力來寫上次日本行的遊記，但是苦於免費圖床難找難用，又不想用facebook網誌功能來寫，所以一直富堅至今XD
後來熊熊想到，其實我還是可以用以經上傳好的FB相簿，然後把權限公開來當圖床使用，還有免費的CDN，真是賺翻了XDD 
<del>（未來有一天就突然消失就囂張不起來了XD  FB表示：怪我囉？）</del>


總之我要做的事就是dump出所有相簿裡的照片URL還有我打好的comment，於是在chrome按`F12`敲了以下snippet：

	var lastSrc = '';
	var dumpArr = [];
	var handler = function () {
	    var img = $$('.spotlight')[0];
	    if (dumpArr.length > 0 && img.src == dumpArr[0].src) {
	        $$('.fbPhotosPhotoCaption')[0].removeEventListener('DOMSubtreeModified', handler);
	        return;
	    }
	    if (img != null && img.src != lastSrc) {
	        setTimeout(function () {
	            lastSrc = img.src;
	            dumpArr.push({
	                src: img.src,
	                comment: ($$('.hasCaption').length > 0 ? '' : $$('.hasCaption')[0].innerHTML)
	            });
	            console.log(dumpArr[dumpArr.length - 1]);
	            $$('.snowliftPager.next')[0].click();
	        }, 500);
	    }
	};

	$$('.fbPhotosPhotoCaption')[0].addEventListener('DOMSubtreeModified', handler);

只要進到秀照片的theater模式（就是四周都會變黑的模式）就可以跑囉！
欸...亂寫的需要就用用看吧，有空再來解釋XD (靠)
---
layout: post
title: "Error Handling in Aspect of UX"
date: 2013-04-16 22:53
comments: true
categories: ["java","ux","exception handling"]
---
最近接了一個project，主要工作是重新設計一個web-based的『百年系統』。
對企業來說，下這種re-engineering決定是一個難題，但這種需求卻很常見。
支持這決策的關鍵考量可能有幾項：

*	舊系統code base難以維護，或是年久、失傳等歷史因素
*	舊系統架構已經無法滿足新的商業需求
*	舊系統Operation Support的Effort過於龐大
*	族繁不及備載XD

如果是談軟體工程等架構面的問題，應該發個100篇文章也講不完吧XD
所以今天只來講講最後一項的Operation。

<!-- more -->
##設計想法

Case：今天user遇到一些問題，發現該動的功能不能動，或是不知道要怎麼操作，於是求助OS Team。
所以如果要降低Operation case的量，最先想到的可能就是Exception Handling與fail-over機制。
我認為既然case來源是user，就需要從user experience的角度來考量設計Exception Handling機制。

##想得到的幾項設計＆大略實作的方式（待補）

### 1. 在程式出錯時，要讓user知道發生什麼事，以方便向OS Team報案
*	UX考量：
	*	出錯時前端要有對應訊息，不能讓整個網頁就hang在那邊
	*	錯誤訊息一定要讓user看得懂，不能是一些"Null Pointer Exception"、"Internal Server Error"之類會讓人霧煞煞的字眼。
	*	要讓user知道該聯絡誰
	*	如果是內部系統，可以考慮將stack trace放在一個縮起來的field set （不要直接秀在畫面上），user可以將它展開並複製給OS人員，方便後續處理。
*	後端設計：
*	前端設計：

### 2. Partial-Reliable的系統：就算一些minor功能crash掉，也不影響正常操作流程
*	UX考量：
	*	如題，系統可能會有些外來的不穩因素（比如說連別人家的web service取得資料時出錯）
	*	應跳出警告訊息，告知哪些部分出錯
*	後端設計：
*	前端設計：

### 3. 資料量大時的因應
*	UX考量：
	*	在企業或工程系統常有大量資料需傳至前端的情況（user下的query條件太寬，但是user偏偏就是要那麼寬，且不要分批/分頁)
	*	讓user知道這樣query下去要等多久
	*	讓user知道，如果他電腦不夠強大，前端可能當掉(喂！)
*	後端設計：
*	前端設計：

看能不能再想到一些XD
有空再補上圖＆一些practice！
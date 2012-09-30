---
layout: post
title: "Ext 4.1b3的bug：在grid中使用template column分群時"
date: 2012-03-03 13:17
comments: true
categories: ExtJS
---
更新4.1b3之後，發現在某些grid中會出現HTML亂掉的情形如下圖。
{% img http://3.bp.blogspot.com/-YBqydfk22z0/T1HVilgqT9I/AAAAAAAABek/tQ7XrpoEv-4/s1600/ext.gif %}

建立獨立test case之後整理出bug detail如下： 

1. 建立一grid，設定具有dataindex的簡單template column如下    
    {
    	xtype: 'templatecolumn',
    	tpl: '<div data-qtip="{name}">{abbr}</div>',
    	dataIndex: 'abbr',
    	text: 'abbr'
    }
2. 以該欄grouping之後，會出現上述之亂碼情形。 
3. 若將dataindex移除，則不會有此情形，但將失去sorting等功能。

[已向sencha回報](http://www.sencha.com/forum/showthread.php?184128-4.1B3-Error-when-grouping-by-a-template-column-in-a-grid)

{% img http://3.bp.blogspot.com/-L3VLm5q-uS4/T1HVTVdalfI/AAAAAAAABec/kQZ8KwGcn-8/s400/2012-03-03+14-14-56.png 400 %}
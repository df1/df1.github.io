---
layout: post
title: "Ext JS 4.0.7 (4.1b2) IE8 Performance Issue"
date: 2012-02-17 13:17
comments: true
categories: [Ext Designer, ExtJS, IE, English Post]
---
<span>Our project is an Ext 4 application built with Ext Designer 1.2.2, with the 4.0.7 library. Inevitably, we faced the performance issue in IE8, while firefox and chrome work just fine and smooth. (the bad news is our company is IE8-dominating)&nbsp;</span><br />
<span>We've tried out the latest ExtJS 4.1 beta 2, beside dozens of layout distortions, we still find no performance improvement.&nbsp;</span><br />
<br />
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;"><a href="http://1.bp.blogspot.com/-cf1TbR1PNa8/T0kov0y9u8I/AAAAAAAABco/pNDXBrqSeBQ/s1600/2012-02-26+2-23-42.png" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="244" src="http://1.bp.blogspot.com/-cf1TbR1PNa8/T0kov0y9u8I/AAAAAAAABco/pNDXBrqSeBQ/s320/2012-02-26+2-23-42.png" width="320" /></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;">oh and the support period is gonna expire</td></tr>
</tbody></table>
<br />
<span>Here are the questions I've asked Sencha for support:</span><br />
<br />
<span>1. Does the beta 2 really cover any slight or significant performance improvement? How was the benchmark and the community feedback about this?&nbsp;</span><br />
<br />
<span>2. Is it still far from 4.1 GA? Could we expect more improvements in the future beta/GA releases, or that's almost all?&nbsp;</span><br />
<br />
<span>3. I use the Ext 4 dynamic loading. However for our current program, it almost loads every /store/*.js, /view/*.js and /view/ui/*.js upon initializing the main application (except the ones for pop-up windows and other run-time-created things). Regarding IE8 performance optimization, will it help if we try to eliminate the not-yet-used components as best as we can? (I wonder who makes the entire IE8 incredibly slow) Or there's any other related threads or suggestions that would help?&nbsp;</span>
<br />
<span>Here's the first response, within 2 hrs! So prompt!</span><br />
<blockquote class="tr_bq custom-blockquote" style="border: gray dotted; padding: 10px;">
<span>Thank you for the report. Hopefully we can resolve this issue.&nbsp;</span><br />
<br />
<span>1) We are constantly trying to improve the performance of 4.1 with every release. There should be a new BETA release very soon, so hopefully this may help. IE is always a challenge.&nbsp;</span><br />
<span>2) 4.1 GA is scheduled for mid-late March depending on the results from the prior releases. As mentioned, speed improvements are always a priority.&nbsp;</span><br />
<span>3) As you mention, anything you can do to delay, or eliminate the loading of unused items will be a plus for rendering.&nbsp;</span><br />
<br />
<span>The issue of what is the cause of slow rendering can be a number of things.&nbsp;</span><br />
<span>We had a case the other day where a customer was having slow rendering issues in IE7/8 and it turned out to be customer code and custom CSS.&nbsp;</span><br />
<br />
<span>To provide an accurate answer, we would need to see a small working example that display the problem that you see.&nbsp;</span><br />
<span>One thing that you may try, is to create generic form that has numerous controls (including populate combos, array driven) to see if you have the same problem.&nbsp;</span><br />
<br />
<span>I have attached <a href="http://support.extjs.com/download.php/reply/36915/t7210.zip" target="_blank">an example</a> that you can use as a template. Please see how this renders on IE8, Please make sure to update the path to Ext in the html file.&nbsp;</span><br />
<br />
<span>If you have any further questions, please let us know.&nbsp;</span></blockquote><br />
<span>I'll try to cope with that anyway</span><br />
<span><br /></span><br />
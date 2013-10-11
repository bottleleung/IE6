IE6
===

这是我为解决IE6及各大浏览器兼容性而编写的一系列demo

首先，整个project分为以下一些文件夹：

1、3pixelsBug表示的是解决IE6下3像素Bug：

    Explain：IE6下如果浮动元素与非浮动元素相连，就会出现两者间隔3像素这个Bug，可以直接设置margin-left或margin-right为负数就
可以解决。如果存在haslayout属性不为true的情况，可以先激发haslayout属性再设置margin。但这样却不能兼容chrome和firefox等主流浏
览器，因为浮动会让元素偏离原来文本流，导致会影响其他元素的宽高度计算。而float既能激发haslayout也能兼容chrome、firefox等，所
以直接把非浮动元素设置为浮动就可以解决这个问题了。

2、doubleMargin表示的是解决IE6下双边距Bug：

    Explain：IE6下如果同时满足以下条件：（1）块级元素（2）同时设置float: left、margin-left或float: right、margin-right时，
会导致margin变成原来的两倍，这时候只需要添加display: inline样式就可以解决了。至于存在设置了display: inline后还可以设置width
和height的所谓“冲突”问题，就不必纠结了，加这个样式纯粹是用来兼容IE6而已。

3、positionFix表示的是如何在IE6下实现position: fixed

    Explain：IE6不支持position: fixed，可以设置*position: absolute，然后再设置*top和*left就可以了。（*表示只有IE6、7才能识
别）

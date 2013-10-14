IE6
===

这是我为解决IE6及各大浏览器兼容性而编写的一系列demo
----------------------------------------------------
首先，整个project分为以下一些文件夹：

### 1、3pixelsBug表示的是解决IE6下3像素Bug：

    Explain：IE6下如果浮动元素与非浮动元素相连，就会出现两者间隔3像素这个Bug，可以直接设置margin-left或  
    margin-right为负数就可以解决。如果存在haslayout属性不为true的情况，可以先激发haslayout属性再设置margin。
    但这样却不能兼容chrome和firefox等主流浏览器，因为浮动会让元素偏离原来文本流，导致会影响其他元素的宽高度计算。
    而float既能激发haslayout也能兼容chrome、firefox等，所以直接把非浮动元素设置为浮动就可以解决这个问题了。

### 2、doubleMargin表示的是解决IE6下双边距Bug：

    Explain：IE6下如果同时满足以下条件：（1）块级元素（2）同时设置float: left、margin-left或float: right、
    margin-right时，会导致margin变成原来的两倍，这时候只需要添加display: inline样式就可以解决了。至于存在设
    置了display: inline后还可以设置width和height的所谓“冲突”问题，就不必纠结了，加这个样式纯粹是用来兼容IE6
    而已。

### 3、positionFix表示的是如何在IE6下实现position: fixed

    Explain：IE6不支持position: fixed，可以设置*position: absolute然后再设置*top和*left就可以了。（*表示
    只有IE6、7才能识别）至于为什么不通过CSS的expression来设置呢？个人认为从网页性能的角度来考虑，能CSS解决的问
    题就尽量不通过脚本来解决，所以这里“逼不得已”采用了CSS Hack。

### 4、opacity表示如何实现各浏览器下设置具有背景度的透明块：

    Explain:设置透明在过往一般采用CSS opacity的属性，但这种方法会使应用该样式元素的后代元素都继承这种效果，
    所以现在改成用CSS3的新属性rgba来设置透明度。有开发人员通过切图的方式实现这种透明效果，个人认为不太科学，
    因为图片会减慢网页的加载速度，虽说CSS Hack能不用尽量不用，但在此却很有必要。当你试把条件注释中的代码放到
    原样式中，你会发现IE9下透明层更“透明”了，但IE10下却不会，为什么呢？因为IE9同时支持自身alpha滤镜和CSS3
    的rgba，就等同“两次透明”了，而IE10已经不支持alpha了，但IE6、7、8却不支持rgba，只支持自身的alpha，所以
    可以通过这种方式实现这种效果。

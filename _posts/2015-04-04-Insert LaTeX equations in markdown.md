---
layout: post
title: "Insert LaTeX equations in markdown "
categories:
- Technology
tags:
- LaTeX
- markdown


---
Markdown自由书写的特性很好，唯独遇到数学公式时稍稍有些麻烦，
本文的方法使用html的语法，调用一些公式生成API [1]，在线生成Latex数学公式，免去将公式保存为图片的麻烦。弊端是： 公式太多时，可能会造成刷新比一般的网页慢一些。

###方法一：使用Google Chart的服务器

	<img src="http://chart.googleapis.com/chart?cht=tx&chl= 在此插入Latex公式" style="border:none;">

一个例子，

	<img src="http://chart.googleapis.com/chart?cht=tx&chl=\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" style="border:none;">

公式显示结果为：

<img src="http://chart.googleapis.com/chart?cht=tx&chl=\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" style="border:none;">

Google Chart服务器的响应速度还可以，但据说可能复杂一些的Latex公式可能无法解析（参考[2]）。

###方法二：使用forkosh服务器

forkosh上提供了关于Latex公式的一份简短而很有用的帮助，参考[1]和[3].

使用forkosh插入公式的方法是

	<img src="http://www.forkosh.com/mathtex.cgi? 在此处插入Latex公式">

给个例子：

	<img src="http://www.forkosh.com/mathtex.cgi? \Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}">

显示结果为：

<img src="http://www.forkosh.com/mathtex.cgi? \Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}">


因为网页插入公式的原理是调用“某某网站的服务器”动态生成的，所有保证公式正常显示的前提是该网址能一直存在着为我们做些小小的服务。forkosh我是用了快2年了，一直很好，推荐！

###方法三：使用MathJax引擎

大家都看过Stackoverflow上的公式吧，漂亮，其生成的不是图片。这就要用到MathJax引擎，在Markdown中添加MathJax引擎也很简单，

	<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

然后，再使用Tex写公式。$$公式$$表示行间公式，本来Tex中使用\(公式\)表示行内公式，但因为Markdown中\是转义字符，所以在Markdown中输入行内公式使用\\(公式\\)，如下代码：

	$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$
	\\(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\\)

在公式上还可以使用鼠标右键操作。

###参考
[1] [http://www.forkosh.com/mathtextutorial.html](http://www.forkosh.com/mathtextutorial.html)

[2] [http://www.ruanyifeng.com/blog/2011/07/formula_online_generator.html](http://www.ruanyifeng.com/blog/2011/07/formula_online_generator.html)

[3] [http://www.forkosh.com/mathtex.html](http://www.forkosh.com/mathtex.html)

---
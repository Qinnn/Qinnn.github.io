---
layout: post
title: "Insert LaTeX equations in markdown "
categories:
- Technology
tags:
- LaTeX
- Markdown
---
Markdown自由书写的特性很好，唯独遇到数学公式时稍稍有些麻烦，
本文的方法使用html的语法，调用一些公式生成API [1]，在线生成$$\LaTeX$$数学公式，免去将公式保存为图片的麻烦。弊端是： 公式太多时，可能会造成刷新比一般的网页慢一些。

## 方法一：使用Google Chart的服务器

	<img src="http://chart.googleapis.com/chart?cht=tx&chl= 在此插入Latex公式" style="border:none;">

一个例子，

	<img src="http://chart.googleapis.com/chart?cht=tx&chl=
	\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" style="border:none;">

公式显示结果为：


<img src="http://chart.googleapis.com/chart?cht=tx&chl=\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" style="border:none;">


Google Chart服务器的响应速度还可以，但据说可能复杂一些的$$\LaTeX$$公式可能无法解析（参考[2]）。

## 方法二：使用forkosh服务器

forkosh上提供了关于$$\LaTeX$$公式的一份简短而很有用的帮助，参考[1]和[3].

使用forkosh插入公式的方法是

	<img src="http://www.forkosh.com/mathtex.cgi? 在此处插入Latex公式">

给个例子：

	<img src="http://www.forkosh.com/mathtex.cgi? \Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}">

显示结果为：

<img src="http://www.forkosh.com/mathtex.cgi? \Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}">


因为网页插入公式的原理是调用“某某网站的服务器”动态生成的，所有保证公式正常显示的前提是该网址能一直存在着为我们做些小小的服务。

## 方法三：使用MathJax引擎

在网页中使用$$\LaTeX$$最流行的解决方案应该是MathJax。这是一个基于JavaScript的$$\LaTeX$$渲染引擎，它将网页中的$$\LaTeX$$公式转变成多个不同字体的文字或图片的组合。

在Github的Page中使用数学公式，也就是在Jekyll中使用数学公式，MathJax似乎是唯一的选择。

唯一担心的是，$$\LaTeX$$中的一些符号，比如下划线会与Markdown中的下划线冲突，但似乎实用过程中又没遇到什么问题。

### 第一步 将_config.yml中的markdown修改为

	markdown: kramdown

本地使用jekyll时可能需要额外安装kramdown

	gem install kramdown

kramdown是一个Markdown解析器，它能够正确解释公式内部的符号，不会与Markdown语法冲突，比如不会将`^`符号变成`<sup></sup>`标签。

### 第二步 在文件头中添加引用和设置代码

也就是`_include/header.html`(有的可能应该是`_layouts/default.html`)中插入如下内容：

	<script type="text/x-mathjax-config">
	MathJax.Hub.Config({
                  tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}
                          });
	</script>
	<script type="text/javascript"
		src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
	</script>

### 第三步 在Markdown中使用$$\LaTeX$$数学公式

行内公式：`$$E=mc^2$$ is a inline formula`,效果为：$$E=mc^2$$ is a inline formula.

行间公式：

	\begin{aligned} 
	\dot{x} &= \sigma(y-x) \\ 
	\dot{y} &= \rho x - y - xz \\ 
	\dot{z} &= -\beta z + xy 
	\end{aligned} 


效果为：

$$
\huge
\begin{aligned} 
\dot{x} &= \sigma(y-x) \\ 
\dot{y} &= \rho x - y - xz \\ 
\dot{z} &= -\beta z + xy \end{aligned} 
$$

有人可能会遇到公式显示太小的情况，这时可以用$$\LaTeX$$的命令`\large`如果还嫌小可以用`\Large`:

	$$
	\begin{aligned} 
	\dot{x} &= \sigma(y-x) \\ 
	\dot{y} &= \rho x - y - xz \\ 
	\dot{z} &= -\beta z + xy 
	\end{aligned} 
	$$
	
## 参考


[1] [http://www.forkosh.com/mathtextutorial.html](http://www.forkosh.com/mathtextutorial.html)

[2] [http://www.ruanyifeng.com/blog/2011/07/formula_online_generator.html](http://www.ruanyifeng.com/blog/2011/07/formula_online_generator.html)

[3] [http://www.forkosh.com/mathtex.html](http://www.forkosh.com/mathtex.html)

[4] [http://www.pkuwwt.tk/linux/2013-12-03-jekyll-using-mathjax/](http://www.pkuwwt.tk/linux/2013-12-03-jekyll-using-mathjax/)

---
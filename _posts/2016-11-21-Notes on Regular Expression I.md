---
layout: post
title: Notes on Regular Expression I
categories:
- Technology
tags:
- Regular Expression

---

# 定义 #

正则表达式是由普通字符（例如字符 a 到 z）以及特殊字符（称为"元字符"）组成的文字模式。模式描述在搜索文本时要匹配的一个或多个字符串。正则表达式作为一个模板，将某个字符模式与所搜索的字符串进行匹配。

# 字符 #

* 字符
    * 可打印
        * 大小写字母
        * 数字
        * 标点符号
        * 其它（？）
    * 非打印
        * `\cx` `\c`为CONTROL,  `x` 的值必须为 A-Z 或 a-z 之一。否则，将 `\c` 视为一个原义的 'c' 字符
        * `\f` 匹配一个换页符
        * `\n` 匹配一个换行符
        * `\r` 匹配一个回车符
        * `\s` 匹配任何空白字符
        * `\S` 匹配任何非空白字符
        * `\d` 匹配一个数字字符, 等价于 `[0-9]`
        * `\D` 匹配一个非数字字符。等价于 `[^0-9]`
        * `\w`匹配包括下划线的任何单词字符, 等价于`[A-Za-z0-9_]`
        * `\W` 匹配任何非单词字符, 等价于`[^A-Za-z0-9_]`
        * `\t` 匹配一个制表符
        * `\v` 匹配一个垂直制表符
        * `\xn` 匹配 n，其中 n 为十六进制转义值。十六进制转义值必须为确定的两个数字长。例如，`\x41` 匹配 "A"。`\x04` 则等价于 '\x04' & "1"。正则表达式中可以使用 ASCII 编码。
        * `\num` 匹配 num，其中 num 是一个正整数。对所获取的匹配的引用。例如，`(.)\1` 匹配两个连续的相同字符
        * `\un` 匹配 n，其中 n 是一个用四个十六进制数字表示的 Unicode 字符。例如，` \u00A9` 匹配版权符号
* 特殊字符 (元字符要求在试图匹配它们时特别对待。若要匹配这些特殊字符，必须首先使字符"转义"，即，将反斜杠字符 (`\`) 放在它们前面)
    * `$` 匹配输入字符串的结尾位置
    * `*`  匹配前面的子表达式零次或多次
    * `+` 匹配前面的子表达式一次或多次
    * `?` 匹配前面的子表达式零次或一次
    * `.` 匹配除换行符 \n 之外的任何单字符
    * `^` 匹配输入字符串的开始位置，除非在方括号表达式中使用，此时它表示不接受该字符集合
    * `{` 标记限定符表达式的开始
    * `|` 指明两项之间的一个选择
    * `[` 标记一个中括号表达式的开始
        * `[xyz]` 字符集合。匹配所包含的任意一个字符
        * `[^xyz]` 负值字符集合。匹配未包含的任意字符
        * `[a-z]` 字符范围。匹配指定范围内的任意字符
        * `[^a-z]` 负值字符范围。匹配任何不在指定范围内的任意字符
    * `()` 标记一个子表达式的开始和结束位置。子表达式可以获取供以后使用
        * `(pattern)` 匹配 `pattern` 并获取这一匹配。所获取的匹配可以从产生的 Matches 集合得到
        * `(?:pattern)` 匹配 `pattern` 但不获取匹配结果，也就是说这是一个非获取匹配，不进行存储供以后使用
        * `(?=pattern)` 正向预查，在任何匹配 `pattern` 的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如，`Windows (?=95|98|NT|2000)` 能匹配 "Windows 2000" 中的 "Windows" ，但不能匹配 "Windows 3.1" 中的 "Windows"。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始。
        * `(?!pattern)` 负向预查，在任何不匹配 `pattern` 的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如 `Windows (?!95|98|NT|2000)` 能匹配 "Windows 3.1" 中的 "Windows"，但不能匹配 "Windows 2000" 中的 "Windows"。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始。
 
*  限定符
    * `*`  匹配前面的子表达式零次或多次
    * `+` 匹配前面的子表达式一次或多次
    * `?` 匹配前面的子表达式零次或一次
    * `{n}` n 是一个非负整数。匹配确定的 n 次
    * `{n,}` n 是一个非负整数。至少匹配n 次
    * `{n,m}` m 和 n 均为非负整数，其中n <= m。最少匹配 n 次且最多匹配 m 次

* 定位符  (不能将限定符与定位点一起使用)
	* `^` 匹配输入字符串开始的位置
	* `$` 匹配输入字符串结尾的位置
	* `\b` 匹配一个字边界，即字与空格间的位置
	* `\B` 非字边界匹配

# 运算符优先级 #
 正则表达式从左到右进行计算，并遵循优先级顺序，优先级如下：
 
 1. `\` 转义符
 1. `(), (?:), (?=), []` 圆括号，方括号
 1. `*, +, ?, {n}, {n,m}` 限定符
 1. `^, $ , \任何元字符，任何字符` 定位点和序列
 1. `|` 或
 















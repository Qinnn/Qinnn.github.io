---
layout: post
title: Notes on Regular Expression II
categories:
- Technology
tags:
- Regular Expression

---

# 匹配规则 #

## 基本模式匹配 ##

* `^once` 匹配以'once'开头的字符串
* `buckets$` 匹配以'bucket' 结尾的字符串
* `^buckets$` 只匹配字符串'buckets' (如果一个模式不包括`^`和`$`，那么它与任何包含该模式的字符串匹配)

## 字符簇 ##

* `[AaEeIiOoUu]` 匹配括号中列举出的任意一个字符
* `[a-z]`, `[A-Z]`, `[a-zA-Z]`, `[0-9]`, 匹配括号中列举出的任意一个字符

*其中一个中括号只能匹配一个字符*

## 确定重复出现 ##

* `[a-zA-Z_]` 匹配所有的字母和下划线
* `[a-zA-Z]{3}` 匹配三个字母的单词
* `^a$` 匹配单词'a'
* `^a{2,4}` 匹配'aa', 'aaa', 'aaa'
* `^[1-9][0-9]*$` 匹配所有正整数
* `\-{0,1}[0-9]{1,}$` 匹配所有整数
* `^[-]?[0-9]+\.?[0-9]+$` 匹配所有浮点数


# 常用示例 #

* `/\b([a-z]+) \1\b/gi` 一个单词连续出现的位置，(`\g` 表示全局搜索， `\i` 表示不区分大小写； 对一个正则表达式模式或部分模式两边添加圆括号将导致相关匹配存储到一个临时缓冲区中，所捕获的每个子匹配都按照在正则表达式模式中从左到右出现的顺序存储。缓冲区编号从 1 开始，最多可存储 99 个捕获的子表达式。每个缓冲区都可以使用 `\n` 访问，其中 n 为一个标识特定缓冲区的一位或两位十进制数。
可以使用非捕获元字符 `?:`、`?=` 或 `?!` 来重写捕获，忽略对相关匹配的保存。)
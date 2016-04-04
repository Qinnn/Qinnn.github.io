---
layout: post
title: About appropriate net-surfing (fanqiang)
categories: 
- Technology
date: 2016-04-04 19:13:58 +08:00
tags: 
-onedrive
-dropbox
-goagent
-vpn
---

<img src="https://rtkcmq.dm2302.livefilestore.com/y3mWZD0RndlIDIPAFiBkGJGjnUqMJ4COLEDAjjjRW3yF0g_yz12DkKKM0LCYbLndUw7SGwuaJ8KM7jSqAPzGxS4Q6UfySsiXGyIBmf1FseB5Vmb373slbOwwdnkn9K8X5VhR56coPi_mZ4n0Cc-PJrhFwnCBn8NKWkRx0VCYPMyFXE?width=300&height=200&cropmode=none" width="300" height="200" />


本文介绍一些科学上网的方法。

###云服务###

[Onedrive](https://www.onedrive.live.com) 是微软提供的云服务，同样非常优秀可靠，且免费空间能达到30Gb, 而且提供照片嵌入服务，可作为图床， 然后office文档还能在线预览。 这个只是被DNS污染了，致使网页打不开，还比较容易救回来，方法是在 C:\Windows\System32\drivers\etc\host 中添加如下内容：

	134.170.108.26 onedrive.live.com
	134.170.108.152 skyapi.onedrive.live.com

如果遇到权限问题可以先把host文件拖到桌面，添加好后再拖到原位置。完成后就可以打开上面的网页了。

[Dropbox](https://www.dropbox.com) 是非常著名的云服务提供商，但是后来不知道什么原因被墙了，现在其网页需要翻墙才能打开了，本地的文件夹同步需要用一个DNS代理的软件，软件可在此处下载:

<iframe src="https://onedrive.live.com/embed?cid=0769DCB84E94551A&resid=769DCB84E94551A%2169073&authkey=AKKNH5bF18joexc" width="98" height="120" frameborder="0" scrolling="no"></iframe>

当然云服务还有 [Google Drive]([https://www.google.com/drive/](https://www.google.com/drive/)), 毫无疑问也要先翻墙。

###翻墙###

####Goagent + Chrome + SwitchyOmega####
网上可以搜到一大把的配置教程， 这里就不具体说了， 但是有一个经常出现的问题就是同样的配置windows上面有很多goodip而OS X 上却一个都没有，到现在也没有找到原因。

###AWS EC2 + PPTP VPN####
现在（201604）亚马逊的云服务 AWS / EC2 首年免费， 在上面创建一个ubuntu实例，然后安装 pptp 创建VPN， 具体方法网上也很容易搜索到，比如[这个]([http://blog.banban.me/blog/2014/06/09/li-yong-awsmian-fei-zhang-hu-da-jian-vpn/](http://blog.banban.me/blog/2014/06/09/li-yong-awsmian-fei-zhang-hu-da-jian-vpn/)) 和[这个]([http://zhao.jinhai.de/post/1810.html](http://zhao.jinhai.de/post/1810.html))

####各路付费的VPN####

如[云梯](), [云翔]()等，但是这类服务可能网速不稳定，或者服务无法保证，交了钱过段时间他们被查了或者别的什么原因，完全联系不到他们，且这个交易完全没有担保。 本人曾购买过红杏的代理服务，刚付款几天就出问题，然后拖了好久都没有恢复，也没有退款。

####当然最有效的还是肉身翻墙了####

---

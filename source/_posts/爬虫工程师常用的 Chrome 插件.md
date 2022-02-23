---
title: 爬虫工程师常用的 Chrome 插件
date: 2020-03-30 19:58:15
abbrlink: a46b4fd7
index_img: https://static.zkqiang.cn/images/20190729094905.jpg-cover
tags: [Python, 爬虫]
categories:
- 转载
---

>做多了爬虫都知道，写一个爬虫大部分时间不是在代码上，而是在分析网页上，所有有一套好用的工具可以极大节省劳动力，这里把平时积累的一些 Chrome 插件分享出来，均来自本人和同事推荐，并不定时更新，欢迎点赞和收藏。  
>下面大标题指向的是谷歌应用商店，访问需要特殊方法，也可以进入本仓库的 `extensions` 目录中下载。

## [XPath Helper](https://chrome.google.com/webstore/detail/xpath-helper/hgimnogjllphhhkhlmebbmlgjoejdpjl)

![XPath Helper](https://static.zkqiang.cn/images/20190729094906.png-slim)

相比较 Chrome 自身的 html 搜索，这款插件好用之处是可以显示匹配结果，在插件里写出正确的 XPath 语句后再复制到代码里即可。

## [Toggle JavaScript](https://chrome.google.com/webstore/detail/toggle-javascript/cidlcjdalomndpeagkjpnefhljffbnlo)

![Toggle JavaScript](https://static.zkqiang.cn/images/20190729094907.png-slim)

一键拦截网页所有的 JS，可以快速区分出哪些是异步加载的数据，绝对是爬虫必备神器。

## [FeHelper](https://chrome.google.com/webstore/detail/web%E5%89%8D%E7%AB%AF%E5%8A%A9%E6%89%8Bfehelper/pkgccpejnmalmdinmhkkfafefagiiiad)

![FeHelper](https://static.zkqiang.cn/images/20190729094903.png-slim)

这款插件的强大之处不想多说，看上面的截图就行了，其中一些数据转换的功能，在分析请求时会经常用到。

## [JSON-Handle](https://chrome.google.com/webstore/detail/json-handle/iahnhfdhidomcpggpaimmmahffihkfnj)

![JSON-Handle](https://static.zkqiang.cn/images/20190729095522.png-slim)

这是由知乎 @流沙 推荐的 JSON 格式化插件，虽然上面推荐的已经带有 JSON 功能，但这款插件带有局部选取、对象类型、数组长度等小功能，我试用了几天很实用，适合有额外需求的时候。

## [User-Agent Switcher](https://chrome.google.com/webstore/detail/user-agent-switcher-for-c/djflhoibgkdhkhhcedjiklpkjnoahfmg)

![User-Agent Switcher](https://static.zkqiang.cn/images/20190729094904.png-slim)

快速修改 `UserAgent` 的插件，当需要请求移动端页面时，或者需要传特殊的 UA 时，不要忘记它。

## [X-Forwarded-For Header](https://chrome.google.com/webstore/detail/x-forwarded-for-header/hkghghbnihliadkabmlcmcgmffllglin)

![X-Forwarded-For Header](https://static.zkqiang.cn/images/20190729094902.png-slim)

有时候网站过滤 IP 是通过请求 Headers 中的 `X-Forwarded-For` 字段，通过这个插件就可以修改此字段，用来快速进行判断。

## [SwitchyOmega](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif)

![SwitchyOmega](https://static.zkqiang.cn/images/20190729094908.png-slim)

快速切换 HTTP / Socks 代理的插件，还能根据匹配地址自动切换。另一个技巧是配合 Charles、Burp Suite 这类抓包工具，这些工具使用时需要设置本地代理，可以提前设置好用时就切换。

## [Wappalyzer](https://chrome.google.com/webstore/detail/wappalyzer/gppongmhjkpfnbhagpmjfkannfbllamg)

![Wappalyzer](https://static.zkqiang.cn/images/20190811175102.png-slim)

可以解析当前前端页面所使用的框架及服务支持，这样可以针对 Web 框架使用特殊的爬取方式。

## [Web Scraper](https://chrome.google.com/webstore/detail/web-scraper/jnhgnonknehpejjnehehllkliplmbmhn)

![Web Scraper](https://static.zkqiang.cn/images/20190811175103.png-slim)

又一个神器，如果只是简单的爬取数据，不需要部署和更复杂的操作，可以使用这款插件，内置在 Chrome 控制台，直接操作 Chrome 浏览器进行爬取，不需要写一行代码，支持多种导出格式。

## [EditThisCookie](https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg)

![EditThisCookie](https://static.zkqiang.cn/images/20190831161529.png-slim)

爬虫遇到权限页面时，难免要对 Cookie 反复调试，这款插件可以对当前站点进行 Cookie 编辑，支持增删改查、导入导出、一键清空、搜索等功能。

## 打包下载

如果无法进入谷歌商店，可关注微信公众号：**面向人生编程** (可扫本页底部二维码)，回复"**插件**"获取打包下载。


> **转载声明**
>
> **作者**：张凯强
> **原文链接**：https://zkqiang.cn/posts/a46b4fd7/
> **作者简介**： 后端开发 / 游戏爱好者 / 巴萨球迷
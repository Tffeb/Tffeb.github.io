---
layout: post
title: js性能优化
categories: Javascript
description: js性能优化
keywords: Javascript
---

#### web项目性能优化方案

1. 通过webpack配置开发与生产不同的打包入口（可以使用chainWebpack）
2. 通过externals加载外部CDN资源
3. 首页内容定制，解决spa页面空白时间过长的问题，通过htmlWebpackPlugin，这种一般是使用了CDN资源，需要对资源请求进行控制来减少加载时长
4. 路由懒加载
5. 优化堆栈，优化程序执行时间
6. 项目上线，可以通过zip压缩来传输

##### 参考文章

Web篇之JS性能优化
[https://www.cnblogs.com/tianshu/p/10555921.html](https://www.cnblogs.com/tianshu/p/10555921.html){:target="_blank"}

Javascript常见性能优化
[https://www.cnblogs.com/sunshq/p/9232442.html](https://www.cnblogs.com/sunshq/p/9232442.html){:target="_blank"}

JavaScript性能优化 DOM编程
[https://www.cnblogs.com/strick/p/6769634.html](https://www.cnblogs.com/strick/p/6769634.html){:target="_blank"}


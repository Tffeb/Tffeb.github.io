---
layout: post
title: BOM日常
categories: Javascript
description: BOM日常
keywords: Javascript, ES6
---

### 前言

在开发中经常会遇到些许冷门的一些对BOM操作，下面记录下自己遇到的一些操作

#### 页面复制功能

这里写一个简单的api
----------------------------
```js
const copy = text => {
    // 创建dom节点
    const oInput = document.createElement('input');
    oInput.value = text;
    document.body.appendChild(oInput);
    // 选择对象
    oInput.select();
    // 执行浏览器复制命令
    document.execCommand('Copy')
    oInput.style.display = 'none';
    document.body.removeChild(oInput);
}
```
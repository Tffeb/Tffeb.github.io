---
layout: post
title: 获取部分主流浏览器类型
categories: Javascript
description: 获取部分主流浏览器类型
keywords: Javascript, ES6
---

### 前言

平时开发时难免会遇到一些浏览器兼容问题，以下是获取部分浏览器类型的总结
----------------------------------

```js
const getDeviceName = () => {
    let browserType = '未知浏览器';
    if (ifUserAgentExit('Chrome') && ifUserAgentExit('Safari')) {
        if (ifUserAgentExit('OPR')) {
            browserType = 'Opera浏览器';
        } else if (ifUserAgentExit('360EE')) {
            browserType = '360极速浏览器';
        } else if (ifUserAgentExit('360SE')) {
            browserType = '360安全浏览器';
        } else if (ifUserAgentExit('Edge')) {
            browserType = 'Microsoft Edge浏览器';
        } else {
            browserType = 'Chrome浏览器';
        }
    } else if (ifUserAgentExit('Firefox')) {
        browserType = 'Firefox浏览器';
    } else if (ifUserAgentExit('Mac')) {
        browserType = 'Safari浏览器';
    } else if ((ifUserAgentExit('compatible') && ifUserAgentExit('msie')) || (ifUserAgentExit('trident') && ifUserAgentExit('rv:11.0'))) { //IE11及以下
        browserType = 'IE浏览器';
    }
    return browserType;
}
const ifUserAgentExit = str => {
    let userAgent = navigator.userAgent;
    return userAgent.indexOf(str) > -1 ? true:false;
}
```
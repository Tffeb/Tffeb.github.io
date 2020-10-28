---
layout: post
title: Javascript小工具集锦
categories: Javascript
description: 这里是日常会用的一些小型api
keywords: Javascript, ES6
---

### 前言

开发中难免会遇到一些处理数据的问题，下面是本人记录的一些日常api
----------------------


#### 数字转为千分位字符

```js
/**
 * @param {Number} num
 * @param {Number} point 保留几位小数，默认2位
 */
const parseToThousandth = (num, point = 2) => {
    let [sInt, sFloat] = (Number.isInteger(num) ? `${num}` : num.toFixed(point)).split('.');
    sInt = sInt.replace(/\d(?=(\d{3})+$)/g, '$&,');
    return sFloat ? `${sInt}.${sFloat}` : `${sInt}`;
};
```

#### 多层数组扁平化

```js
const flatten = (arr) => {
    return arr.reduce((result, item) => {
        return result.concat(Array.isArray(item) ? flatten(item) : item);
    }, []);
};
```

#### 下划线转换驼峰#驼峰转换下划线

```js
const toHump = (str) => {
    return str.replace(/_(\w)/g, (all, letter) => letter.toUpperCase());
};

const toLine = (str) => {
    return str.replace(/([A-Z])/g, '_$1')
        .toLowerCase();
};
```



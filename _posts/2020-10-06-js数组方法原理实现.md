---
layout: post
title: js数组方法的简单实现
categories: Javascript
description: js数组方法的简单实现
keywords: Javascript
---


### 前言

开发中经常会遇到对数据的操作，这难免会有用到数组的方法，闲来无事,整理一下es6各大数组方法的原理实现（自己实现的，可能跟源码有偏差）

#### forEach的实现

```js
Array.prototype.myforEach = function (callback) {
    for (let i = 0; i < this.length; i++) {
        callback(this[i])
    }
}
```
#### map的实现

```js
Array.prototype.mymap = function (callback) {
    const result = []
    this.myforEach(item => {
        result.push(callback(item))
    })
    return result
}
```

#### filter的实现

```js
Array.prototype.myfilter = function (callback) {
    const result = []
    this.myforEach(item => {
        if (callback(item)) {
            result.push(item)
        }
    })
    return result
}
```

#### find的实现

```js
Array.prototype.myfind = function (callback) {
    let result = undefined
    this.myforEach(item => {
        if (callback(item)) {
            result = item
        }
    })
    return result
}
```

#### every的实现

```js
Array.prototype.myevery = function (callback) {
    let status = true
    this.myforEach(item => {
        if (!callback(item)) {
            status = false
        }
    })
    return status
}
```

#### some的实现

```js
Array.prototype.mysome = function (callback) {
    let status = false
    this.myforEach(item => {
        if (callback(item)) {
            status = true
        }
    })
    return status
}
```

```js
// 初始化实例
const arr = [1, 2, 3, 4]
// 测试map
// console.log(arr.mymap(item => item + 1))
// 测试filter
// console.log(arr.myfilter(item => [1, 2, 4].includes(item)))
// 测试find
// console.log(arr.myfind(item => item === 5))
// 测试every
// console.log(arr.myevery(item => item === 4))
// 测试some
console.log(arr.mysome(item => item === 4))
```
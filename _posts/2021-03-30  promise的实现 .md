---
layout: post
title: 'promise的实现'
date: 2021-03-30

tag:
  - js
---


#### 实现原理

Promise也是回调函数，只不过是把回调封装在了内部，使用上一直通过then方法的链式调用，使得多层的回调嵌套看起来变成了同一层的，书写上以及理解上会更直观和简洁一些。

一、基础版本
```js
// 实现
class Promise{
    callbacks = [];
    constructor(fn) {
        fn(this._resolve.bind(this));
    }
    then(onFulfilled) {
        this.callbacks.push(onFulfilled);
        return this;  // 可进行链式调用
    }
    _resove(value) {
        this.callbacks.forEach(fn => fn(value))
    }
}

// 应用
let p = new Promise(resolve => {
    setTimeout(() => {
        resolve('done');
    },5000)
}).then(res => {
    console.log(res,'res');
})
```


二、增加状态
```js
//实现+链式调用+延迟机制+状态
class Promise {
    callbacks = [];
    state = 'pending';//增加状态
    value = null;//保存结果
    constructor(fn) {
        fn(this._resolve.bind(this));
    }
    then(onFulfilled) {
        if (this.state === 'pending') {//在resolve之前，跟之前逻辑一样，添加到callbacks中
            this.callbacks.push(onFulfilled);
        } else {//在resolve之后，直接执行回调，返回结果了
            onFulfilled(this.value);
        }
        return this;
    }
    _resolve(value) {
        this.state = 'fulfilled';//改变状态
        this.value = value;//保存结果
        this.callbacks.forEach(fn => fn(value));
    }
}
```

> 原型链实现

```js
function Promise(exector) {
    let _this = this;
    let status = "pending", value = undefined, reason = undefined;
    function resolve(value) {
        if (status === "pending") {
            _this.value = value;
            _this.status = "resolve";
        }
    }
    function reject(value) {
        if (status == "pending") {
            _this.value = value;
            _this.status = "reject"
        }
    }
    try {
        exector(resolve, reject)
    } catch (e) {
        reject(e)
    }
}
Promise.prototype.then = function (resolve, reject) {
    let _this = this;
    if (this.status === "resolve") {
        resolve(_this.value)
    }
    if (this.status == "reject") {
        reject(_this.reason)
    }
}

let promise = new Promise((reject, resolve) => {
    resolve("return resolve")
});
promise.then(data => {

}, err => { })
```
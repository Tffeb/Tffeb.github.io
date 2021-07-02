---
layout: post
title: js将平坦对象转为对象
categories: Javascript
description: js将平坦对象转为对象
keywords: Javascript, ES6
---

#### 需求

给定一个平坦字典对象,其键是点分隔的。

例如,{'A':1,'B.A':2,'B.B':3,'CC.D.E':4,'CC.D.F':5}。

实现一个将其转换为嵌套字典对象的函数。

在上述情况下,嵌套版本如下:

{
    A: 1,
    B: {
        A: 2,
        B: 3
    },
    CC: {
        D: {
            E: 4,
            F: 5
        }
    }
}

#### 思路

1. 先遍历平坦对象拿到key
2. 处理key,将key切割为对象属性数组,反转属性,深度遍历,然后进行对象逐层包裹,形成对象
3. 将每一个key所形成的对象进行合并,合并时需进行深度遍历,有相同的属性,就进行覆盖,不同的属性就进行添加
4. 使用递归进行深度遍历,逐层合并

#### js实现
```js
    // 转化对象
    const transferObj = obj => {
        let values = {};
        for (const key in obj) {
            if (key.indexOf('.') > -1) {
                let temp = {}
                // 将属性字符串拆分翻转一下深度遍历
                key.split('.').reverse().forEach((item, index) => {
                    if (index === 0) {
                        temp[item] = obj[key]
                    } else {
                        let objValue = {}
                        objValue[item] = temp
                        temp = objValue
                    }
                })
                // 将每一个属性进行深度合并
                values = objMerge(values, temp)
            } else {
                values[key] = obj[key]
            }
        }
        return values
    }
    // 深度合并
    const objMerge = (...obj) => {
        let res = {};
        // 对象合并
        const combine = opt => {
            for (const key in opt) {
                if (opt.hasOwnProperty(key)) {
                    //下面是深拷贝与浅拷贝的区别，用到了递归的思想
                    if (opt[key].constructor == Object) {
                        res[key] = objMerge(res[key], opt[key]);
                    } else {
                        res[key] = opt[key];
                    }
                }
            }
        }
        // ...obj 将形参解构形成数组对象
        for (let i = 0; i < obj.length; i++) {
            combine(obj[i]);
        }
        return res;
    }
    // 测试
    const example = { 'a': 1, 'b.c': 2, 'b.c.f': 3, 'b.c.r': 4 }
    console.log(transferObj(example))  // {a: 1,b:{c: {f: 3, r: 4}}}
```



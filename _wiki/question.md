---
layout: post
title: 知识在于不断积累，查漏补缺实乃王道！
permalink: /question/
---

### Javascript基础

1. JavaScript 规定了几种语言类型

基础类型：Number, String, Boolean, Null, Undefined, Symbol

引用类型：Object, Array, Function

2. Javascript 对象的底层数据结构是什么

JavaScript 对象的底层数据结构可以视为散列表或字典，用于存储和访问键值对。这种数据结构的选择是为了实现快速的属性查找和访问操作。平均情况下的时间复杂度为 O(1)。

3. Symbol类型在实际开发中的应用、可手动实现一个简单的Symbol

```js
let id = 0;

function MySymbol(des) {
    this.id = des + id++
}

MySymbol.prototype.toString = function() {
    return this.id;
}

const s1 = MySymbol('symbol_');
const s2 = MySymbol('symbol_');

console.log(s1.toString()) // symbol_0
console.log(s2.toString()) // symbol_1
```

4. JavaScript中的变量在内存中的具体存储形式

`基本类型`它会直接在栈内存中分配空间来存储这个值。

`引用类型`的值是对象的引用，实际的对象存储在堆内存中，而变量中存储的是指向对象的引用地址。这意味着在栈内存中存储的是指向堆内存中实际对象的指针，而不是对象本身。

5. 基本类型对应的内置对象，以及他们之间的装箱拆箱操作

- Number 对应的内置对象是 Number
- String 对应的内置对象是 String
- Boolean 对应的内置对象是 Boolean
- Symbol 对应的内置对象是 Symbol
- null 和 undefined 没有对应的内置对象

```js
const num = 42;
const numObj = new Number(num); // 装箱操作
```

```js
const numObj = new Number(42);
const num = numObj.valueOf(); // 拆箱操作
```

6. null和undefined的区别

它们既不相等也不严格相等（== 或 ===）。因为它们是不同的数据类型，undefined 是一个类型，而 null 是一个特殊的对象值。


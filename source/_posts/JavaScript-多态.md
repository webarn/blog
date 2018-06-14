---
title: JavaScript-多态
date: 2018-06-13 09:20:34
tags: 
  - 设计模式
categories:
  - 设计模式
---

### JavaScript-多态

> 多态背后的思想就是将'做什么'和'谁去做以及怎样去做'分离开来, 也就是将'不变的事物'与'可能改变的事物'分离开来. 把不变的部分隔离出来,把可变的部分封装起来,这给与了我们扩展程序的能力,程序看起来是可生长的, 也是符合开放-封闭原则, 相对于修改代码来说,仅仅增加代码就能完成同样的功能,这显然优雅和安全得多.

<!-- more -->

> 代码示例:

```js
var makeSoud = function(fn) {
  fn.sound();
};
var One = function() {};
One.prototype.sound = function() {
  console.log('one');
};
var Two = function() {};
Two.prototype.sound = function() {
  console.log('Two');
};

makeSoud(new One());
makeSoud(new Two());
```

> 同一个实现接口，使用不同的实例而执行不同的操作。

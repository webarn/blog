---
title: JavaScript代码规范
date: 2018-06-13 16:06:23
tags: 
  - 规范
categories:
  - 规范
---

#### 缩进:

1.  使用 2 个空格做为一个缩进层级或 1 个 tab 字符，不允许使用 4 个空格 或 2 个 tab 字符。

2.  `switch` 下的 `case` 和 `default` 必须增加一个缩进层级

<!-- more -->

    ```js
    switch (num) {
      case '1':
        // do...
        break;

      case '2':
        // do...
        break;

      default:
      // do...
    }
    ```

---

#### 空格:

1.  二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。

    ```js
    var a = !arr.length;
    a++;
    a = b + c;
    ```

2.  用作代码块起始的左花括号 `{` 前必须有一个空格。
3.  `if / else / for / while / function / switch / do / try / catch` 关键字后，必须有一个空格。

    ```javascript
    if (condition) {
      //
    }

    while (condition) {}

    function funcName() {}
    ```

4.  函数声明、具名函数表达式、函数调用中，函数名和 `(` 之间不允许有空格。

    ```js
    function funcName() {}

    var funcName = function funcName() {};

    funcName();
    ```

5.  在对象创建时，属性中的 `:` 之后必须有空格，`:` 之前不允许有空格。

    ```js
    var obj = {
      a: 1,
      b: 2,
      c: 3
    };
    ```

6.  `,` 和 `;` 前不允许有空格。

    ```js
    callFunc(a, b);
    var arr = [1, 2, 3, 4];
    ```

7.  单行声明的数组与对象，如果包含元素，`[]` 内紧贴括号部分不允许包含空格, `{}` 内紧贴括号部分需间隔 1 个空格。

    ```js
    var arr1 = [];
    var arr2 = [1, 2, 3];
    var obj1 = {};
    var obj2 = { name: 'obj' };
    ```

8.  行尾不得有多余的空格。

---

#### 换行:

1.  每个独立语句结束后必须换行。

2.  每行不得超过 120 个字符。(超长的不可分割的代码允许例外，比如复杂的正则表达式。长字符串不在例外之列。)

3.  `在函数声明、函数表达式、函数调用、对象创建、数组创建、for 语句`等场景中，不允许在 `,` 或 `;` 前换行。


    ```js
    var obj = {
        a: 1,
        b: 2,
        c: 3
    };
    ```

---

#### 语句:

1.  在 `if / else / for / do / while` 语句中，即使只有一行，也不得省略块 `{...}`。

    ```js
    if (condition) {
      callFunc();
    }
    ```

2.  函数定义结束不允许添加分号。如果是函数表达式，分号是不允许省略的。

    ```js
    // good
    function funcName() {}

    // bad
    function funcName() {}

    // 如果是函数表达式，分号是不允许省略的
    var funcName = function() {};
    ```

---

#### 命名:

1.  变量/函数/参数 使用驼峰命名方法.

2.  `class` 类 /构造函数首字母必须大写.

3.  [建议]`this` 赋值: `const self = this;`

---

#### 注释:

1.  单行注释: 必须独占一行。`//` 后跟一个空格，缩进与下一行被注释说明的代码一致.
2.  建议文档化注释: 为了便于代码阅读和自文档化，使用 JSDoc 注释.

    ```js
    /**
     * 加法
     * @param {number} a - 参数a
     * @param {number} b - 参数b
     * @param {number} c - 参数c
     */
    function add(a, b, c) {
      return a + b + c;
    }
    ```

---

#### 变量:

1.  变量在使用前必须通过 `var` 定义 (建议如搭载 Babel 必须使用 es6 语法)。

2.  每个 `var/let/const` 只能声明一个变量。

---

#### 条件:

1.  使用类型严格的 `===`。仅当判断 `null` 或 `undefined` 时，允许使用 `==` `null。`

---

#### 循环:

1.  [建议]要在循环体中包含函数表达式，事先将函数提取到循环体外。(循环体中的函数表达式，运行过程中会生成循环次数个函数对象。)

    ```js
    // bad
    for (var i = 0, len = elements.length; i < len; i++) {
      var element = elements[i];
      addListener(element, 'click', function() {});
    }

    // good
    function clicker() {}
    for (var i = 0, len = elements.length; i < len; i++) {
      var element = elements[i];
      addListener(element, 'click', clicker);
    }
    ```

---

#### 字符串:

1.  字符串开头和结束使用单引号 `'`。(1. 输入单引号不需要按住 shift，方便输入。2. 实际使用中，字符串经常用来拼接 HTML。为方便 HTML 中包含双引号而不需要转义写法。)

---

#### 对象:

1.  使用对象字面量 `{}` 创建新 `Object`

    ```js
    // good
    var obj = {};

    // bad
    var obj = new Object();
    ```

2.  不允许修改和扩展任何原生对象和宿主对象的原型。

    ```js
    String.prototype.trim = function() {};
    ```

3.  [建议]属性访问时，尽量使用。

---

#### 数组:

1.  使用数组字面量 `[]` 创建新数组，除非想要创建的是指定长度的数组。

---

#### 函数:

1.  [建议] 一个函数的长度控制在 50 行以内;
2.  [建议] 一个函数的参数控制在 6 个以内。
3.  [建议] 通过 options 参数传递非数据输入型参数。

---

#### npm 包使用:

1.  [建议]使用 `yarn` (安装速度较快,简洁,安全)
2.  安装依赖包明确其运行环境

    - `--save-dev || -D` : 是对生产环境所需依赖的声明(开发应用中使用的框架，库, jq，react，vue 都需要放到这里面 )
    - `--save || -S` : 是对开发环境所需依赖的声明(构建工具，测试工具, webpack,gulp,babel,mock)

---

#### GitLab 使用:

1.  提交:

        - 实现每个功能模块提交一次,每天最少提交一次;
        - commit 说明该次提交功能;

2.  合并:
    - 如出现冲突, 沟通后确认后再合并.

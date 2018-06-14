---
title: CSS代码规范
date: 2018-06-13 16:08:47
tags:
  - 规范
categories:
  - 规范
---

#### 缩进:

1.  使用 2 个空格做为一个缩进层级或 1 个 tab 字符，不允许使用 4 个空格 或 2 个 tab 字符。

---

#### 空格:

1.  选择器 与 `{` 之间必须包含空格。
2.  属性名 与之后的 `:` 之间不允许包含空格， `:` 与 属性值 之间必须包含空格。
3.  每行不得超过 120 个字符，除非单行不可分割(url/src)。

<!-- more -->

---

#### 选择器:

1.  当一个 样式 包含多个 class 时，每个选择器声明必须独占一行。

    ```css
    .post,
    .page,
    .comment {
      font-size: 20px;
    }
    ```

2.  \>、+ 选择器的两边各保留一个空格。

    ```css
    main > nav {
      padding: 10px;
    }

    label + input {
      margin-left: 5px;
    }

    input:checked ~ button {
      background-color: #69c;
    }
    ```

---

#### 属性:

1.  属性定义必须另起一行。

    ```css
    .selector {
      margin: 0;
      padding: 0;
    }
    ```

2.  属性定义后必须以分号结尾。

---

#### 通用:

1.  避免使用小于 12px 的字体

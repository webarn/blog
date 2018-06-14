---
title: HTML代码规范
date: 2018-06-13 16:07:42
tags:
  - 规范
categories:
  - 规范
---

#### 缩进:

1.  使用 2 个空格做为一个缩进层级或 1 个 tab 字符，不允许使用 4 个空格 或 2 个 tab 字符。

---

#### 命名:

1.  `class` 必须单词全字母小写，单词间以 `-` 分隔。

2.  元素 `id` 必须保证页面唯一。

3.  同一页面，应避免使用相同的 name 与 id。

<!-- more -->

---

#### 标签:

1.  标签名必须使用小写字母。

2.  对于无需自闭合的标签，不允许自闭合。

    ```html
    <!-- good -->
    <input type="text" name="title">

    <!-- bad -->
    <input type="text" name="title" />
    ```

3.  标签使用必须符合标签嵌套规则。

    > 比如 div 不得置于 p 中，tbody 必须置于 table 中。

4.  HTML 标签的使用应该遵循标签的语义。

    - p - 段落
    - h1,h2,h3,h4,h5,h6 - 层级标题
    - strong,em - 强调
    - code - 代码标识
    - ul - 无序列表
    - ol - 有序列表
    - dl,dt,dd - 定义列表

5.  在 CSS 可以实现相同需求的情况下不得使用表格进行布局。

6.  标签的使用应尽量简洁，减少不必要的标签。

---

#### 属性

1.  属性名必须使用小写字母。

    ```html
    <table data="0">...</table>
    ```

2.  属性值必须用双引号包围。

3.  布尔类型的属性，建议不添加属性值。

    ```html
    <input type="text" disabled>
    ```

4.  [建议] 自定义属性建议以 `xxx-` 为前缀，推荐使用 `data-`

    ```html
    <div data-num="4"></div>
    ```

---

#### 通用:

1.  使用 HTML5 的 doctype 来启用标准模式，建议使用大写的 `DOCTYPE。`

    ```html
    <!DOCTYPE html>
    ```

2.  [建议] 启用 IE Edge 模式。

    ```html
    <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    ```

3.  在 html 标签上设置正确的 lang 属性。

    ```html
    <html lang="zh-CN">
    ```

4.  指定字符编码

    ```html
    <meta charset="UTF-8">
    ```

5.  [建议] 在 head 中引入页面需要的所有 CSS 资源。

6.  JavaScript 应当放在页面末尾，或采用异步加载。

7.  尽量不要用行内样式.

8.  有下载需求的图片采用 img 标签实现，无下载需求的图片采用 CSS 背景图实现。

9.  尽量避免使用定位布局和浮动布局.

10. 项目开始时,要使用 css 样式初始化.

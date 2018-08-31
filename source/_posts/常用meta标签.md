---
title: 常用meta标签
date: 2018-08-31 15:03:44
tags:
  - HTML
categories:
  - web前端
---

### PC 端

```html
<!-- 设置文档的字符编码 -->
<meta charset="utf-8">
<!-- 优先使用最新IE -->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
<meta name="viewport" content="width=device-width, initial-scale=1.0,maximum-scale=1.0, user-scalable=no" />
<!-- 禁用自动检测和格式化可能的电话号码/邮箱 -->
<meta name="format-detection" content="telephone=no, email=no">
<!-- 禁用翻译提示 -->
<meta name="google" content="notranslate" />
<!-- 选择渲染引擎 -->
<meta name="renderer" content="webkit|ie-comp|ie-stand" />
<!-- 避免百度转码声明 -->
<meta http-equiv="Cache-Control" content="no-siteapp" />
```

### imoble

```html
<meta charset="utf-8">
<!-- 优先使用最新IE -->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
<meta name="viewport" content="width=device-width, initial-scale=1.0,maximum-scale=1.0, user-scalable=no, viewport-fit=cover"
/>
<!-- 禁用自动检测和格式化可能的电话号码/邮箱 -->
<meta name="format-detection " content="telephone=no, email=no ">
<!-- 选择渲染引擎 -->
<meta name="renderer " content="webkit|ie-comp|ie-stand " />
<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait">
<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait”>
<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">
<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true”>
<!-- 禁用的 UC 浏览器的功能，“当此页面中有较多文本时缩放字体” -->
<meta name="wap-font-scale" content="no" />
```

```html
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
<meta name="format-detection" content="telephone=no, email=no">
<meta name="renderer" content="webkit|ie-comp|ie-stand" />
<meta name="screen-orientation" content="portrait">
<meta name="x5-orientation" content="portrait">
<meta name="full-screen" content="yes">
<meta name="x5-fullscreen" content="true">
<meta name="wap-font-scale" content="no" />
```

---
title: postMessage不同页面参数传递
date: 2018-06-21 09:54:55
tags: 
  - JavaScript 
categories:
  - JavaScript
---

> index-1

```html
<body>
  <h2>index1</h2>
  <p id="p"></p>
  <a href="./index-2.html">index-2</a>
</body>
<iframe style="display: none" id="one" src="./index-2.html" frameborder="0"></iframe>
<script>
  let one = document.getElementById('one');
  let p = document.getElementById('p');
  one.onload = function () {
    one.contentWindow.postMessage('index-1已加载完毕!', '*');
    window.addEventListener('message', function (e) {
      console.log(e.data);
      p.innerHTML = e.data;
    });
  };

</script>
```

<!-- more -->

> index-2

```html
<body>
  <h2>index2</h2>
  <a href="./index-1.html">index-1</a>
</body>
<script>
  let msg = '页面2的数据';
  window.addEventListener('message', function (e) {
    // 接收index-1数据
    console.log(e.data);
    // 回发数据
    e.source.postMessage(msg, '*');
  }, false);
</script>
```

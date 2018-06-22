---
title: 独立封装jQuery滑动验证
date: 2018-06-22 09:28:52
tags:
  - JavaScript
categories:
  - JavaScript
---

> 基于 jQuery 封装  闲暇  滑动  验证插件
>  首先引入 jQuery, $('el').drag();

<!-- more -->

### html

```html
<!DOCTYPE html>
<html lang="zh-CN">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
</head>
<style>
  .box {
    width: 600px;
    height: 300px;
    border: 1px dashed slategray;
    margin: 100px auto;
  }

  #rall {
    width: 80%;
    height: 50px;
    background: sandybrown;
    margin: 50px auto;
    border-radius: 50px;
    position: relative;
  }

  #hand {
    width: 50px;
    height: 50px;
    background: skyblue;
    border-radius: 50px;
    position: absolute;
    left: 0;
    top: 0;
  }
</style>

<body>
  <div class="box"></div>
</body>

</html>
```

### js

```js
(function($) {
  $.fn.drag = function(options) {
    // 创建元素
    const element = '<div id="rall"><div id="hand"></div></div>';
    // 把元素添加到dom
    this.append(element);
    // 查找创建的元素
    const rall = this.find('#rall');
    const hand = this.find('#hand');
    // 获取可移动的最大宽度
    const maxWidth = rall.width() - hand.width();
    // 鼠标按下鼠标的位置
    let x;
    // 拖动误差
    let err = 5;

    // 鼠标按下事件
    hand.mousedown(function(event) {
      let e = event || window.event;
      x = e.pageX - parseInt(hand.css('left'), 10);

      // 拖动事件处理
      $(document).mousemove(function(event) {
        console.log(1);
        let e = event || window.event;
        // 获取鼠标拖动位置
        let _x = e.pageX - x;
        // 如果鼠标拖动位置大于0 && 小于可拖动位置的最大值
        if (_x > 0 && _x <= maxWidth) {
          hand.css({ left: _x });
        } else if (_x > maxWidth) {
          // 防止拖动过快(拖动位置大于最大值后,获取滑块的位置)
          let ing = parseInt(hand.css('left'), 10);
          if (_x < maxWidth - err || ing < maxWidth - err) {
            hand.css({ left: 0 });
          } else {
            alert('success');
          }
          // 清除
          dragClear();
        }
      });

      // 鼠标抬起
      $(document).mouseup(function() {
        // 获取抬起位置
        let _x = e.pageX - x;
        // 如果抬起位置小于最大值,则验证失败,返回初始位置
        if (_x < maxWidth - err) {
          hand.css({ left: 0 });
        }
        // 清除事件
        dragClear();
      });
    });

    // 事件清除
    function dragClear() {
      $(document).unbind();
    }
  };
})(jQuery);

$('.box').drag();
```

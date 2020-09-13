### 项目描述

利用jQuery，animate动画实现鼠标mouseenter经过手风琴



### 页面布局

1.king大盒子里面包含ul>li*7
2.每个小li包含一个a，a里面有2张图片，.small小图 .big大图，
3.小图定位在大图上面

##### 代码演示：

```
<div class="king">
        <ul>
            <li class="current">
                <a href="#">
                    <img src="images/m1.jpg" alt="" class="small">
                    <img src="images/m.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/l1.jpg" alt="" class="small">
                    <img src="images/l.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/c1.jpg" alt="" class="small">
                    <img src="images/c.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/w1.jpg" alt="" class="small">
                    <img src="images/w.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/z1.jpg" alt="" class="small">
                    <img src="images/z.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/h1.jpg" alt="" class="small">
                    <img src="images/h.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/t1.jpg" alt="" class="small">
                    <img src="images/t.png" alt="" class="big">
                </a>
            </li>
        </ul>

    </div>
```

### 效果分析

##### 鼠标经过小li有2步操作

- 当前小li 宽度变为 224px， 同时里面的小图片淡出，大图片淡入；
- 其余兄弟小li宽度变为69px， 小图片淡入， 大图片淡出 ；

代码演示：

```
 <!-- 引入jQuery动画库 -->
    <script src="js/jquery.min.js"></script>

    <script type="text/javascript">
        $(function() {
            // 鼠标经过某个小li 有两步操作：
            $(".king li").mouseenter(function() {
                // 1.当前小li 宽度变为 224px， 同时里面的小图片淡出，大图片淡入
                // this后 当前li
                // 动画前面加stop,避免多次动画
                // .find 后代 .fadeOut 淡出 .siblings 兄弟  .fadeIn 淡入
                $(this).stop().animate({
                    width: 224           
                }).find(".small").stop().fadeOut().siblings(".big").stop().fadeIn();
                // 2.其余兄弟小li宽度变为69px， 小图片淡入， 大图片淡出
                $(this).siblings("li").stop().animate({
                    width: 69
                }).find(".small").stop().fadeIn().siblings(".big").stop().fadeOut();
            })
        });
    </script>
```


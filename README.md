### 博客园代码
这里主要内容是对我的博客页面的重构,包括页面头部、底部及侧边栏
#### 页面头部 headr.html
添加github和移动端视窗，在手机上体验更友好
```html
<a class="git-link" href="https://github.com/Jesse121/cnblogs" target="_blank">
    <img src="http://images.cnitblog.com/blog2015/294743/201503/241715567241255.png" alt="Fork me on GitHub">
</a>
<script>
    $(function(){
        //添加github
        $('#blogTitle').append($('.git-link'));

        //添加移动端视窗
        $('head title').before('<meta name="viewport" content="width=device-width, initial-scale=1">');
    });
</script>
``` 
#### 页面底部 footer.html
目前页面底部只要是添加了一个返回顶部的小火箭和百度统计代码
```html
<!-- 返回顶部小火箭 start-->
    <div id="rocket-to-top">
          <div class="level-2"></div>
         <div class="level-3"></div>
    </div>
    <script type="text/javascript">
        $(function() {
            var e = $("#rocket-to-top"),
            i = true;
            $(window).scroll(function() {
                var t = $(document).scrollTop();
                t == 0 ? e.css("background-position") == "0px 0px" ? e.fadeOut("slow") : i && (i = !1, $(".level-2").css("opacity", 1), e.delay(100).animate({
                    marginTop: "-1000px"
                },
                "normal",
                function() {
                    e.css({
                        "margin-top": "-125px",
                        display: "none"
                    }),
                    i = !0
                })) : e.fadeIn("slow")
            }),
            e.hover(function() {
                $(".level-2").css("display","block").stop().animate({
                    opacity: 1
                });
            },
            function() {
                $(".level-2").css("display","none").stop().animate({
                    opacity: 0
                });
            }),
            $(".level-3").click(function() {
                function t() {
                    var t = e.css("background-position");
                    if (e.css("display") == "none" || i == false) {
                        clearInterval(n),
                        e.css("background-position", "0px 0px");
                        return
                    }
                    switch (t){
                    case "0px 0px":
                        e.css("background-position", "-298px 0px");
                        break;
                    case "-298px 0px":
                        e.css("background-position", "-447px 0px");
                        break;
                    case "-447px 0px":
                        e.css("background-position", "-596px 0px");
                        break;
                    case "-596px 0px":
                        e.css("background-position", "-745px 0px");
                        break;
                    case "-745px 0px":
                        e.css("background-position", "-298px 0px");
                    }
                }
                if (!i) return;
                n = setInterval(t, 50),
                $("html,body").animate({scrollTop: 0},"slow");
            });
        });
    </script>
<!-- /返回顶部小火箭 end-->
<!-- 站长统计 start -->
    <script type="text/javascript">
    var cnzz_protocol = (("https:" == document.location.protocol) ? " https://" : " http://");
    document.write(unescape("%3Cspan id='cnzz_stat_icon_1259209666'%3E%3C/span%3E%3Cscript src='" + cnzz_protocol + "s11.cnzz.com/z_stat.php%3Fid%3D1259209666' type='text/javascript'%3E%3C/script%3E"));
    $('#footer').append($("#cnzz_stat_icon_1259209666"));
    </script>
<!-- 站长统计 end -->
```
#### 侧变栏 sidebar.html
侧边栏添加了个性头像和显示访问量的代码
```html
<div class="portrait">
    <img src="http://pic.cnblogs.com/avatar/801336/20150821180632.png" alt="头像">
</div>
<div class="visitor">
    访问量：
    <a href="#">
        <img border="0" src="http://cc.amazingcounters.com/counter.php?i=3203230&c=9610003" alt="AmazingCounters.com">
    </a>
</div>
```
#### 样式文件
剩下的内容则都是通过改变样式达到自己想要的效果，这里样式文件就不直接展示出来了
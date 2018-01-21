1.这是一个网页性能优化案例，针对此网页进行了一系列方案的优化。此项目需要达到的一系列指标:
Part 1: 优化 index.html 的 PageSpeed Insights 得分
利用github page搭建自己的静态网页，在加载过程中利用PageSpeed Insights工具进行打分，移动端和电脑端超过90分为通过
Part 2: 优化 pizza.html 的 FPS（每秒帧数），编辑 views/js/main.js 来优化 views/pizza.html，直到这个网页的 FPS 达到或超过 60fps
Part 3: 在5ms时间内实现pizza图片大小的转变


2.在实现此过程中运用到的知识点:
* [web 性能优化](https://developers.google.com/web/fundamentals/performance/ "web 性能")
* [分析关键渲染路径](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "分析关键渲染路径")
* [优化关键渲染路径](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "优化关键渲染路径！")
* [避免 CSS 渲染阻塞](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "css渲染阻塞")
* [优化 JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [通过 Navigation Timing 进行检测](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api")。在前两个课程中我们没有学习 Navigation Timing API，但它对于自动分析页面性能是一个非常有用的工具。我强烈推荐你阅读它。
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">下载量越少，性能越好</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">减少文本的大小</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">优化图片</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP缓存</a>


3.在优化过程中采用到的措施：
(1).原代码：  <link href="//fonts.googleapis.com/css?family=Open+Sans:400,700" rel="stylesheet"> // 谷歌字体的应用
  将其变化成异步加载使用:
<script type="text/javascript">
        //异步加载Google fonts的css文件以优化页面访问速度
        WebFontConfig = {
            google: { families: [ 'Open+Sans:400,700' ] }
        };
        (function() {
            var wf = document.createElement('script');
            wf.src = ('https:' == document.location.protocol ? 'https' : 'http') +
            '://ajax.googleapis.com/ajax/libs/webfont/1.5.18/webfont.js (ht(防止屏蔽)tp:/(防止屏蔽)/ajax.googleapis.com(防止屏蔽)/ajax/libs/webf(防止屏蔽)ont/1.5.18/webfont.js)';
            wf.type = 'text/javascript';
            wf.async = 'true';
            var s = document.getElementsByTagName('script')[0];
            s.parentNode.insertBefore(wf, s);
        })();
    </script>
(2).将css压缩，使用css Minifier
(3).减少绘制背景pizza的数量
(4).去除不必要的计算pizza宽度的步骤

4.检测此应用的步骤：
1.利用PageSpeed Insights 检测此网站，得分为90分以上为通过
2.查看该网页帧率是否达到60fps每秒，console对话框中有显示
3.变化pizaa的大小，查看耗时是否在5ms以内，console对话框中有显示

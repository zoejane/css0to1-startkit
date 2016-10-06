# Chapter1 - 踏出第一步

## Template避免重复工作
### 准备代码样板
> 绝大多数情况下我们都需要一个代码样板来帮我们快速开始，避免重复的工作。  
> 作为一个前端开发者，你应该维护好一份适合自己的代码样板，使得日后自己的每个项目都可以以此来初始化。

### Template内容
#### 基本
- 设置 doctype
  - ```<!doctype html>```
- 设置页面编码
  - ```<meta charset="utf-8">```
- 引入初始化 css
  - ```<link rel="stylesheet" href="css/main.css">```

#### 进阶
- 指定使用 HTML5 语法
  - ```<!doctype html>```
  - HTML5. Use tags like ```<article>```, ```<section>```, etc.
  - See: [http://www.sitepoint.com/web-foundations/doctypes/](https://www.sitepoint.com/web-foundations/doctypes/)
- 要求 IE 遵守现代浏览器的渲染标准
  - ```<meta http-equiv="x-ua-compatible" content="ie=edge">```
  - Ask IE to behave like a modern browser
  - See: https://www.modern.ie/en-us/performance/how-to-use-x-ua-compatible
- 锁死页面在移动设备显示宽度
  - ```<meta name="viewport" content="width=device-width,initial-scale=1">```
  - Disables zooming on mobile devices.
- 引入了 normalize.css, 在默认的HTML元素样式上提供了跨浏览器的高度一致性
  - ```<link rel="stylesheet" href="css/normalize.css">```
  - Stylesheet that minimizes browser differences.
  - See: http://necolas.github.io/normalize.css/
    - [英文：What is the difference between Normalize.css and Reset CSS](http://stackoverflow.com/questions/6887336/what-is-the-difference-between-normalize-css-and-reset-css)
    - [中文：来，让我们谈一谈 Normalize.css](http://jerryzou.com/posts/aboutNormalizeCss/)
  - Normalize.css是一种CSS reset的替代方案。经过@necolas和@jon_neal花了几百个小时来努力研究不同浏览器的默认样式的差异，这个项目终于变成了现在这样。
    - 两位大牛花了这么多时间做出来的成果，我们可以非常方便的使用。这就是编程很棒的地方，学会站在巨人的肩膀上，你会觉得走得更顺利和轻松。谢谢这些开放和热爱分享的大牛们。
  
 ## Live 页面编辑(可选项)
 - codepen.io
 - BrowserSync
   - 无法运行应该是环境配置的问题 https://github.com/BrowserSync/browser-sync/issues/1007
 - [F5 Web 编辑器](http://getf5.com/)
 
 ## 设置固定背景
 - > [MDN](https://developer.mozilla.org/en-US/) 和 [Can I Use](http://caniuse.com/) 这两个网站在前端开发中非常重要，在使用 CSS3 属性的时候一定要养成查阅的习惯, 确认你的目标浏览器有支持。
 - ```background-attachment: fixed;``` 使背景图不随页面的滚动而滚动
 - ```background-size: cover;``` 使背景图始终填满整个屏幕
 - ```background-position: center;``` 使背景图居中
 - 更多关于背景的知识: [Backgrounds In CSS: Everything You Need To Know](https://www.smashingmagazine.com/2009/09/backgrounds-in-css-everything-you-need-to-know/)
 
## 居中外包围框
- > 我们之后支持响应式布局只需要调整外包围框的宽度即可改变内部所有元素的宽度，非常方便。
- ``` <div class="container">```
- ```width: 960px;```设置外包围框的宽度。
- ```margin: 0 auto;``` 让浏览器自动计算左右 margin，使外包围框居中。
  - 这个居中技巧只限于有设置宽度的容器。

## 头部容器
### 在容器中居中
- [块级元素](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Block-level_elements)
  - p, div, h1, h2, table, ol 等等
  - 浏览器会在块级元素前后增加断行。这些元素的默认宽度会填满父容器。
  - ```<img src="whales.png" class="centered-image"/>```
  - 
  ```
  .centered-image {
  display: block;
  width: 25%;
  margin: 0 auto;
}```
    - ```display: block;``` 把行元素变成块元素
    - ```margin: 0 auto;``` 居中块元素
      - 元素一定要有 width 属性
  - This is an image, with display set to 'block' in CSS. Centered by setting left/right margin to auto.
  - 如果你想要居中一个行元素（比如图片），但不影响同个容器里面的其他元素，那你可以选择把它设定为块元素来居中。
- [行元素](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Inline_elemente)
  - span, img, a, button, input 等等
  - 在文字流里面显示，浏览器不会添加断行。默认宽度刚好适应内容。
  - ```
  <div class="centered-container">
  <!-- All inline elements are centered in this container. -->
  <h1>Moby Dick</h1>
  <img src="whales.png"/>
</div>
```
  - ```.centered-container {
  text-align: center;
}```
    - ```text-align: center;``` 通过容器来居中行元素
  - 使用 text-align 居中必须经过一个元素的父元素来居中，这会影响在这个容器里所有的元素。 在前面这个例子你可以看到不只是图片居中了, h1 和 p 里面的文字也被居中了。

### 向上移出头部容器
### 实现头部容器
#### 1. 布局
- 设定头部容器的背景
```background-image: url(../img/banner.jpg);```
- 居中头像和 h1 标题。把头像的 img 元素设定为块元素
#### 2.字体风格
- 引用 [Google Fonts](https://www.google.com/fonts#UsePlace:use/Collection:Open+Sans) 提供的 Open Sans 字体
```
<link href='http://fonts.googleapis.com/css?family=Open+Sans:400,300' rel='stylesheet' type='text/css'>
```
- 调整 字体 属性
```
font-weight: 300;
font-size: 50px;
font-family: 'Open Sans','helvetica',arial,sans-serif;
text-shadow: 0 1px rgba(0,0,0,0.3);
```
#### 3. 头像修饰
- ```box-shadow: 0 0px 2px 1px rgba(0,0,0,0.2);``` 给头像加阴影
- ```border-radius: 999px```把头像变成圆形

### 调整元素间距
- ```.container {
  background-color: #D8D8D8;
  padding: 1px;
}```
  - ```padding: 1px;``` 禁止 .container 折叠间距
  - 在 ```.container``` 上面加上的 ```padding: 1px;``` 有点神奇。假如我们没有加上这个 ```padding: 1px;```，你会发现容器本身的 margin-top 会和第一个子元素的 margin-top 折叠在一起。在容器和 top 这个字符之间的空白其实是 子元素的 margin-top。同样的，父元素的 margin-bottom 会和最后一个子元素的 margin-bottom 也折叠一起了。
  - 有关 margin 折叠的细节和用法可以看 [Collapsing Margins](http://www.sitepoint.com/web-foundations/collapsing-margins/)
- ```.container p {
  margin-top: 50px;
  margin-bottom: 50px;
}```
  - ```margin-top: 50px;``` 和 ```margin-bottom: 50px;``` 设定间距

## 怎样排序 CSS 属性
具体的属性排序可以按照以下的规则：

- 定位属性: position, float, z-index, clear
- 盒模型相关属性: padding, margin, display, width, height, border
字体相关
- CSS2 视觉相关属性 (background)
- CSS3 属性 (border-radius, box-shadow)

详情请看 [CSS property order - @mdo](http://markdotto.com/2011/11/29/css-property-order/)



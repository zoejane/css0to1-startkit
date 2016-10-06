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


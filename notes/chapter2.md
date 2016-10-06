# Chapter2 - 实现导航和页面内容

## 设置全局字体风格
```
body {
  font-family: 'Open Sans','helvetica',arial,sans-serif;
  font-weight: 300;
  color: #62686f;
}

h1, h2, h3, h4, h5, h6 {
  color: #333;
  font-weight: 300;
}
```

## 导航布局的实现思路
接下来我们要做出这个效果：
- 4 个链接在同一行显示；
- 4 个链接的内容居中显示。

挺简单的。套用第一节课介绍的居中方法，我们可以这么做：
- 把每个链接变成 inline 元素
- 把容器设定为 text-align: center

## HTML 语义
## 根据职能选择元素
在编写 HTML 的时候我们需要先了解模块在页面中的职能（即语义），然后依据各个模块的职能来选择合适的元素：

- 导航模块应该使用 nav
- 文章模块就应该使用 article
- 头部模块应该使用 header
- 无编号列表模块应该使用 ul

## 举例
在编写主导航的时候我们应该这么分析：

- 主导航这个容器应该用 nav
- 容器里面有个列表，用 ul
- 每个链接放在个别的条目 li 里面

注意，虽然设计里链接的文字都是全大写的，我们编写的 HTML 它们应该是用常规的写法。这是因为 “全大写” 是样式范畴，而非文本语义的范畴。

## 分析利弊
我们需要:

- 消除列表本身的默认间隔
- 消除列表条目的默认风格
- 把列表条目编程行元素

为什么要这么蛋疼？遵照 HTML 语义有什么好处呢？

- 分离内容和页面的表现方法。   
假如我们要把导航改成垂直的菜单，不需要去修改 HTML 把 span 变成 div
- 看到一个 nav 就知道是导航，不需要去看它的风格。方便和别的前端工程师协作。

总结我们上面说说的，在实现页面中的一个模块的时候我们可以分成以下几个步骤：

- 了解模块在页面中的职能（语义）；
- 编写 HTML 代码；
- 观察模块的布局特点；
- 编写 CSS 代码。

### HTML5 语义标签的浏览器支持
[Can I Use: Semantic Elements](http://caniuse.com/#search=semantic)  
IE8 虽然不支持，但我们引用的 normalize.css [解决了这个问题](https://github.com/necolas/normalize.css/blob/2bdda84272650aedfb45d8abe11a6d177933a803/normalize.css#L33-L60)。  
Dive Into HTML5 有[语义 HTML 深入的介绍](http://diveintohtml5.info/semantics.html)。

## 实现主导航
### 去除列表的风格
- ```ul.nostyle {
  list-style: none;
  padding: 0;
  margin: 0;
}```
  - ```list-style: none; ```把列表装饰去掉
  - ```padding: 0; margin: 0;``` 把浏览器默认的间隔清除
- ```ul.inline-items li {
  display: inline;
}```
  - li 默认是块元素。需要元素在同行显示的话记得把它们变成行元素: ```display: inline```

### 实现主导航
我们把比较繁琐的的设计风格写好了，布局就看你的啦！

```
.main-nav {
  background-color: #333;
}

.main-nav ul li {
  margin: 15px 10px;
}

.main-nav ul li a {
  color: #fff;
  font-size: 0.9rem;
  font-weight: 300;
  text-transform: uppercase;
  text-decoration: none;
}

.main-nav ul li a:hover {
  text-decoration: underline;
}
```
- inline 元素只能设置其左右内边距和外边距，而不能设置其高度和上下内外边距。和垂直高度有关的 padding, margin, height 都无效。
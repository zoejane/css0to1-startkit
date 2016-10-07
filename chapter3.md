# Chapter3 - 实现页面内容 - Part 2

今天的课程我们继续来练习用 float 布局。我们会学到

- Block Formatting Context 的用处
- 用 border-box 简化 CSS 布局

这个课程里面的练习我们会给较少的提示。间距的微调和例行风格调整（比如去除 ul 的风格）请你自己记得去做！

## 实现 Education and Experience
这个布局的思路很简单：
- 让图片浮动；
- 图片和文字之间设定间隔。

用 float 实现左右布局是个很常见的设计模型。不过这里有个排版的坑要注意一下。
- 如果我们有个向左的浮动元素，在其右有足够的空间，那么接下来的内容会全部在飘动元素的右边。
- 但如果内容超过了飘动元素的高度，这些内容就会包围住该飘动元素。

### float 布局避免内容包围飘动元素
```
<div class="container">
  <!-- This image floats to the left -->
  <img class="float-left" src="whale.jpg"/>

  <!-- The article should not wrap around the floated image -->
  <article class="content">
    <p>Call me Ishmael....</p>

    <p>There now is your insular city of the Manhattoes...</p>
  </article>

</div>
```
```
.float-left {
  float: left;
}

.content {
  overflow: hidden;
}
```
- ```float: left``` 向左飘动的元素
- ```.content { overflow: hidden } ```避免这个容器里面的文字包围容器外面的浮动元素。

#### 关于overflow:hidden
[overflow @CSS-TRICKS](https://css-tricks.com/almanac/properties/o/overflow/)
![](https://css-tricks.com/wp-content/csstricks-uploads/css-overflow-hidden.png)

- 看到 overflow: hidden 你应该会想到我们之前用这个属性来让容器包围飘动元素。这个属性影响了容器计算高度的算法。

- overflow: hidden 对容器还有一个重要的改变，那就是把该容器变成了一个新的 block formatting context （简称 bfc）。如果一个容器有自己的 bfc，它就不会被外面的浮动元素覆盖。
  - 如果 .content 没有自己的 bfc (overflow: visible), 你可以看到 .content 的内容虽然会避开浮动图片，但这个容器本身是被覆盖的。
  - 如果 .content 有自己的 bfc，容器为了不被飘动图片覆盖，宽度缩小了。

关于 bfc 的衍生阅读：

- [CSS 101: Block Formatting Contexts](http://yuiblog.com/blog/2010/05/19/css-101-block-formatting-contexts/)
- [How does the CSS Block Formatting Context work?](http://stackoverflow.com/a/6199172)

### 练习 - Education and Experience

- 设定图片的宽度为 180px
- 用 float 布局
- 为文字内容加上一个包围容器，创建新的 bfc  
在 HTML 里面去加上更多的文字内容，确认这些文字不会围绕飘动元素。
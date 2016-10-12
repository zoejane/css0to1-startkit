# Chapter 5 - 响应页面的实现

## 响应页面的实现

### 设置页面缩放方式
- 不希望页面被缩放使得文字变小
- 设置viewport 的 initial-scale 属性为 1 来禁止缩放
- ```<meta name="viewport" content="width=device-width, initial-scale=1">```

### 调整外围容器宽度
使用一个外围容器有两个好处：

- 容器里块元素的宽度默认是外围容器的宽度
- 调整外围容器就会调整所有内部元素的宽度

所以，只要为移动端调整外围容器的宽度，
我们就可以有初步的 ”响应“。

#### CSS 技巧 - 使用 Media Query
media query 可以限制 CSS 的有效条件，
如 “只有当屏幕宽度在100px到200px之间才生效”、“只在手机横屏时生效” 等等。
通过 media query我们可以实现为不同的页面宽度应用不同样式。
media query 是响应式布局的基础。

```
<div class="change-color">
  green when the screen is less than 500px.
</div>
```
```
.change-color {
  background: red;
}

@media (max-width : 500px) {
  .change-color {
    background: green;
  }
}
```

(max-width : 500px)
	- 这些 CSS 只适用于 500px 以下的屏幕宽度

```
@media only screen (max-width : 500px) {

}
```
这里添加的条件 only screen 限制这些CSS只对屏幕生效。
打印页面的时候这些风格不会生效。

没有 media query 的 CSS 默认对所有媒体形式生效。如果你需要支持屏幕和打印，你可以在引用 CSS 文件的时候加上 media 属性。
```
<link rel="stylesheet" href="css/main.css" media="screen">
<link rel="stylesheet" href="css/print.css" media="print">
```

IE9 才开始有支持。IE6-8 需要引用这个 JavaScript 的 polyfill：[Respond.js](https://github.com/scottjehl/Respond)

## 练习 - 调整容器大小
960px 以下的屏幕设定外围容器的宽度为 100%

## 为那些尺寸做响应？
不要针对任何设备的尺寸来做响应。我们可以参照 bootstrap 设定的四种尺寸：

```
/* Large Devices, Wide Screens */
@media only screen and (max-width : 1200px) {

}

/* Medium Devices, Desktops */
@media only screen and (max-width : 992px) {

}

/* Small Devices, Tablets */
@media only screen and (max-width : 768px) {

}

/* Extra Small Devices, Phones */
@media only screen and (max-width : 480px) {

}
```

在做设计的时候就要为这些宽度范围考虑好，布局如何、有哪些元素不重要可以隐藏等等。

## Chrome 模拟设备尺寸
在 Device 你可以选择预置的设备，快速切换分辨率和屏幕有关参数。此外还可以设置分辨率比率，来模拟 Retina 或者更高级屏幕下的效果，这样可以测试你的响应式图片是否被正确替换等。它甚至提供了网络测试，来测试低网速情况下你的页面加载情况。慢网速的测试，往往需要用抓包工具（Charles 等）来模拟，现在用 Chrome 也可以模拟了。

除此之外，Chrome 的手机模拟器还提供了非常非常多的实用功能，比如模拟 touch 事件、捏等手势操作、地理位置、加速计、Retina 等等，详情请见 [官方文档](https://developer.chrome.com/devtools/docs/device-mode)，英文不好的朋友可以看我的 [翻译版本](https://github.com/yujiangshui/CN-Chrome-DevTools/blob/device-mode/md/Use-Tools/device-mode.md)

### 练习 - 修改标题字体
- 标题的字体是 font-size: 32px
- 导航的每个链接都改成 block

## 修改 What I Do
- .info-section padding 减少为 10px
- li.whatido__skill margin-bottom 增加为 40px

## Mobile-first vs Desktop-first

很多人在做响应式设计喜欢以移动端为出发点，再用 min-width 的 media query 为平板和左面的布局打补丁。min-width 指定的 CSS 只有在某个窗口宽度以上才会生效，和我们这个课程用的 media-query 恰恰相反。

Mobile-first 的实现思路由简单到复杂，做起来可能比较直观。可以看看这篇博文的介绍：[How To Write Mobile-First CSS](http://www.zell-weekeat.com/how-to-write-mobile-first-css/)

## 总结

使用 media query 只是响应式实现的第一步。移动端的特殊环境不只是屏幕小，还有延迟长，带宽小的问题。

其他针对移动端优化的贴心小技巧可以读这篇文：
[Creating a Mobile-First Responsive Web Design](http://www.html5rocks.com/en/mobile/responsivedesign/)
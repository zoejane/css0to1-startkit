# Chapter4 - 实现页面内容 - Part 3

## 实现 Get In Touch

有了前面的练习，这个布局应该很容易就实现了。请你自己做。

[Aligning a float:left div to center? @StackOverflow](http://stackoverflow.com/questions/5523632/aligning-a-floatleft-div-to-center)

use ```display:inline-block;``` instead of float

you can't centre floats, but inline-blocks centre as if they were text
- so on the outer overall container of your "row" - you would set ```text-align: center;``` 
- then for each image/caption container (it's those which would be ```inline-block;```) you can re-align the text to left if you require

## 实现 Leave A Message
- 输入栏和 submit 按钮居中
- Name, Email, Message 这些标签在表单容器外面，向右靠齐

和之前一样，我们把没啥技术含量的修饰性风格准备好了:
```
.contact input,
.contact textarea {
  border: 1px solid #ccc;
  border-radius: 4px;
}

.contact button {
  border: none;
  border-radius: 9999px;

  background: #ffd524;

  cursor: pointer;
  text-shadow: 0 1px 1px rgba(0,0,0,0.2);
  color: #fff;
  box-shadow: 0 3px 0 #daae1d;
}
```

请布局表单：

- 表单的宽度为容器的 40%
- 输入栏的 padding 为 8px

## 使用绝对定位
输入栏标签的布局是使用绝对定位 (position: absolute) 的一个经典场景。绝对定位的的适用情况大概是

- 有一个主要组件，在文件流里面正常布局；
- 这个组件有一个附属组件 (它的小伙伴)；
- 这个附属组件的位置相对于主要组件的位置。

以我们这个表单举例，输入栏是正常布局，而标签的位置在输入栏的左边，用绝对定位移过去。

### 把子元素移到外面，和容器的边靠齐
```
<div class="box">
  align top
  <div class="align-top">
    I am absolutely positioned
  </div>
</div>

<div class="box">
  align left
  <div class="align-left">
    I am absolutely positioned
  </div>
</div>

<div class="box">
  align right
  <div class="align-right">
    I am absolutely positioned
  </div>
</div>

<div class="box">
  align bottom
  <div class="align-bottom">
    I am absolutely positioned
  </div>
</div>
```
```
.box {
  position: relative;
}

.align-bottom {
  position: absolute;
  top: 100%;
  width: 100%;
}

.align-left {
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
}

.align-right {
  position: absolute;
  top: 0;
  left: 100%;
  width: 100%;
}

.align-top {
  position: absolute;
  bottom: 100%;
  width: 100%;
}
```
- ```.box { position: relative; }```
父容器的定位不能是默认的 'static'
- ```top: 100%, left: 100%```
这里的百分比（%）是相对于父容器高和宽的百分比
- ```width: 100%```
指定元素的宽度为父容器的宽度

### 练习 - 把输入栏标签移到左边去

- 做绝对定位时记得把父元素设置为 position: relative
- 标签和输入栏内容应该对齐

### 总结

前面几堂课我们学了 CSS 布局的一些基础：

- block 和 inline-block 的区别
- float 布局的方法和坑
- absolute 定位的用法

回顾这个布局，你会发现除了图片和外围容器，我们没有写死任何容器的宽高。基本上页面上的元素都会自动适应它们的容器宽度。这些实现的细节会让响应式设计的实现相对容易！
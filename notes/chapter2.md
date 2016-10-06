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
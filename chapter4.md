# Chapter4 - 实现页面内容 - Part 3

## 实现 Get In Touch

有了前面的练习，这个布局应该很容易就实现了。请你自己做。

[Aligning a float:left div to center? @StackOverflow](http://stackoverflow.com/questions/5523632/aligning-a-floatleft-div-to-center)

use ```display:inline-block;``` instead of float

you can't centre floats, but inline-blocks centre as if they were text
- so on the outer overall container of your "row" - you would set ```text-align: center;``` 
- then for each image/caption container (it's those which would be ```inline-block;```) you can re-align the text to left if you require
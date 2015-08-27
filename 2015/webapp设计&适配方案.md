# webapp设计&适配方案

#### 概述

智能手机越来越多，手机参数也各种不一，导致移动端webapp 布局适配成了大问题。

``` html
iPhone 4  320 * 480   2倍屏
iPhone 5  320 * 568   2倍屏
iPhone 6  375 * 667   2倍屏
iPhone 6P 414 * 736   3倍屏
Samsung S4 360 * 640  3倍屏
```

可以预见 未来还有很多不同尺寸的手机等着适配~

#### 现有解决方案

> 固定宽：
> 
> 320宽度为标准去做适配，超过320的大小还是以320的规格去展示
> 
> 流式布局：
> 
> 百分比定义宽度，高度不是百分比（用绝对单位来固定尺寸）
> 
> 响应式：
> 
> 为N个屏幕写一套适配代码。

问题：

固定宽度：  大屏幕下2边留白，还有超大屏幕下页面非常小。

流式布局： 不能完美实现设计师布局  一些大屏幕下会很难看。

响应式： 维护成本高，改动成本高。不利于维护。

#### rem

> rem（font size of the root element）是指相对于根元素的字体大小的单位。

`设置HTML的font-size，然后利用rem来进行元素宽高布局，一些不变元素还可以使用px来布局`

通过改变`HTML`的`font-size `来动态调整页面元素的大小。

关于设定HTML font-size的问题：

1. 可以用media query 来设定常用的尺寸的 font-size
2. js动态计算HTML的font-size （设置一个跟屏幕宽度成正比的font-size）


除了使用rem作为单位来布局以外，还需要一些适配规则：

	文字流式，空间弹性，图片等比缩放。

#### 一些概念：

- 单位英寸像素数（Pixel Per Inch，PPI）：现实世界的一英寸内像素数，决定了屏幕的显示质量
- 设备像素比率（Device Pixel Ratio，DPR）：物理像素与逻辑像素（px）的对应关系
- 分辨率（Resolution）：屏幕区域的宽高所占像素数




#### 文字不同平台下显示问题

文字部分会有一些跟元素布局不一样的问题存在，通常不用rem来设定文字大小。

rem会一直变，而某些情况下 你会希望 iPhone5 iPhone6 上某些段落文字大小一致，所以需要用px来设定。

1. 通过media query来设定某些节点的文字大小。



1. 部分场景下（标题） 希望跟随屏幕宽增大而增大，可以使用rem来作为单位。


一些文字解决方案：

> 由于DPR的原因，24px 在 DPR为2、DPR为3的屏幕上显示是不一样的。
> 
> 所以我们做一个media query 很多不同DPR设定大小，一般这样能解决 设计师要求任何屏幕上字体大小都要统一，这个要求。

#### 1像素问题：

如何在移动端实现真实1px线，一直都是问题（retina屏幕）。

``` 
<meta name="viewport" content="initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no">
```

通常我们的meta标签都会这样写，但这样的设定下 1px线永远无法实现。

手机淘宝JS动态更改：

``` javascript
var metaEl = doc.createElement('meta');
var scale = isRetina ? 0.5:1;
metaEl.setAttribute('name', 'viewport');
metaEl.setAttribute('content', 'initial-scale=' + scale + ', maximum-scale=' + scale + ', minimum-scale=' + scale + ', user-scalable=no');
if (docEl.firstElementChild) {
    document.documentElement.firstElementChild.appendChild(metaEl);
} else {
    var wrap = doc.createElement('div');
    wrap.appendChild(metaEl);
    documen.write(wrap.innerHTML);
}
```
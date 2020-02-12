![](http://lcjim-img.oss-cn-beijing.aliyuncs.com/2020-02-12-201904.jpg)

# 设置 body 为全高

```css
body {
  height: 100vh; /* 不用考虑父元素高度，直接设置就能生效 */
  margin: 0;
}
```

这是一个快速的、在不涉及任何其他元素的情况下，设置 body 为全高（full height）的方式。我通常会在低风险的演示 demo 上这么做，但是这还是有问题的，因为随着浏览器地址栏的出现和消失，页面可能会发生跳动，或者说页面可能不会像我想象中的那样展示。

你可能想到使用 `body { height: 100% }` 来解决问题，但这也有一个 问题。body 是 `<html>` 的子元素，而 **`<html>` 的高度默认是由内容撑开的**。

如果你需要设置 body 为全高，也需要同时设置 <html> 才行：
```css
html, body { 
  height: 100%;
}
```

> 这是作者要讲的 第一个问题—— 100vh 没有将手机端的地址栏计算在内，导致地址栏出现时，相对于 100vh 元素定位在底部的元素会因为地址栏的出现，被推出到视口之外。这个问题的解决办法是改用 html, body {  height: 100%; }  声明解决。

# 屏幕底部的固定定位

屏幕底部的固定定位，应该使用 position: fixed 来实现，而不是 position: absolute 定位。

![](https://user-gold-cdn.xitu.io/2020/2/12/170373e7a65e9525?imageslim)


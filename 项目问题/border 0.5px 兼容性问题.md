## border 0.5px 兼容性问题

> 问题背景：开发的时候明明给div设置了border 0.5px，但是在手机上看跟1px一样粗细。

[完整代码](https://codepen.io/zhunh/pen/QWqBqEN)

### DPI和PPI的概念

DPI：Dots Per Inch，每英寸的点数。

PPI：Pixels Per Inch，每英寸能容纳的像素个数，用来描述屏幕的像素密度。一块屏幕在出厂的时候，长宽和PPI都是固定的，因此PPI是一个物理单位。

### 物理分辨率

分辨率描述的是屏幕的像素尺寸。以iphone6为例：

屏幕尺寸：宽2.3英寸，高4.1英寸，对角线4.7英寸

分辨率1334*750

由以上数据，在x方向（宽方向）可以计算得出像素密度PPI = 750 / 2.3  = 326 

### 理解像素密度PPI

同理在y方向（高方向）也可以计算得出iphone6的像素密度PPI = 1334 / 4.1 =  326

PPI = 326，即该屏幕每英寸能容纳326颗像素。就是说326 * 326px 的正方形 在iphone6 上展示出来的尺寸将会是1*1英寸。

### devicePixelRatio

Window.devicePixelRatio返回当前显示设备的物理像素与CSS像素分辨率之比。它会告诉浏览器应使用多少屏幕实际像素来绘制单个CSS像素。

计算公式：devicePixelRatio = 物理像素 / 设备独立像素(device-independent pixels (dips))

获取设备dpr：

```js
Window.devicePixelRatio
```

例如，devicePixelRatio = 2，代表在这个设备上需要用 2 (1 * 2) 个物理像素去表示一个设备独立像素。 

### 逻辑分辨率

现在来看逻辑分辨率，iphone6 的devicePixelRatio = 2，即1逻辑像素需要2物理像素渲染，据此可以计算出iphone6的逻辑分辨率：

高：物理像素 / dpr = 1334 / 2 = 667px

宽：物理像素 / dpr = 750 / 2 = 375px

所以逻辑分辨率为 375*667px。

获取设备逻辑分辨率大小：

```js
// 获取逻辑分辨率宽
window.screen.width
// 高
Window.screen.height
```




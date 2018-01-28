要点：
- canvas和svg的区别以及各自的应用场景
- canvas的宽高设置（html css js）css下是等比缩放
- 

## canvas初探

#### canvas的宽高
canvas元素的默认宽高是`300*150`，单位为px。页面上的canvas元素的宽高尽量使用**内联样式或通过js来设置**。如果通过css来设置canvas元素的宽高的话，canvas元素会默认以`300*150`的宽高比等比缩放，影响视觉效果。

#### canvas对象
首先，我们要获取到页面上的`canvas对象`。
```
var canvas = document.getElementById("canvas");
```

然后获取到这个`canvas对象`的上下文环境，语法为：
```
canvas.getContext(contextType, contextAttributes);
```
其中，`contextType`为上下文环境的类型，主要分:
- 2d：代表一个二维渲染上下文
- webgl（或"experimental-webgl"）：代表一个三维渲染上下文
- webgl2（或"experimental-webgl2"）：代表一个三维渲染上下文；这种情况下只能在浏览器实现 WebGL 版本2 (OpenGL ES 3.0)。

`contextAttributes`参数是可选的，该参数提供接受布尔值，如下:
- Alpha：如果它的值是 true，它提供了一个alpha缓冲区到画布上。默认true
- depth：如果它的值是true，会得到一个绘图的缓冲区，其中包含至少16位的深度缓冲。默认true
- stencil：如果它的值是true，会得到一个绘图的缓冲区，其中包含至少8位的模板缓存。默认false
- antialias：如果它的值是true，会得到一个绘图缓冲区，执行抗锯齿。默认true
- premultipliedAlpha：如果它的值是true，会得到一个绘图缓冲区，其中包含的颜色与预乘alpha。默认true
- preserveDrawingBuffer：如果它的值是true，缓冲区将不会被清零，直到被清除或由作者改写将保留它们的值。默认false

该参数在此不作讨论。

通常我们在创建了一个canvas对象之后，第一步就是获取其上下文环境，绘制操作在上下文环境中完成。

### 绘制路径
canvas的API预置了很多绘制路径的方法：

方法名 | 用途
---|---
fill() | 填充路径
stroke() | 描边
arc() | 创建圆弧
rect() | 创建矩形
fillRect() | 绘制矩形路径区域
strokeRect() | 绘制矩形路径描边
clearRect() | 在给定的矩形内清除指定的像素
arcTo() | 创建两切线之间的弧/曲线
beginPath() | 起始一条路径，或重置当前路径
moveTo() | 把路径移动到画布中的指定点，不创建线条
lineTo() | 添加一个新点，然后在画布中创建从该点到最后指定点的线条
closePath() | 创建从当前点回到起始点的路径（关闭路径）
clip() | 从原始画布剪切任意形状和尺寸的区域
quadraticCurveTo() | 创建二次方贝塞尔曲线
bezierCurveTo() | 创建三次方贝塞尔曲线
isPointInPath() | 如果指定的点位于当前路径中，则返回 true，否则返回 false

#### arc()
arc() 方法创建弧/曲线（用于创建圆或部分圆）。
```
context.arc(x,y,r,sAngle,eAngle,counterclockwise);
```
- x:圆的中心的 x 坐标。
- y:圆的中心的 y 坐标。
- r:圆的半径
- sAngle:起始角，以弧度计。（弧的圆形的三点钟位置是 0 度）。
- eAngle:结束角，以弧度计。
- counterclockwise:可选。规定应该逆时针还是顺时针绘图。False = 顺时针，true = 逆时针。

如上所述
```
var canvas = document.getElementById("canvas");
var context = canvas.getContext("2d");
var cw = canvas.width = 400;
var ch = canvas.height = 400;

context.beginPath();
context.arc(100, 100, 50, 0, Math.PI * 1, false);
context.closePath();
context.fillStyle = 'rgba(255, 255, 255, 1)';
context.fill();
```
上面的代码即画了一个半圆。其中，`counterclockwise`设置为顺时针，也就是从起点顺时针画了一个半圆，即一个下弦半圆。

值得注意的一点是：上面的例子我们使用的是fill()，如果我们使用的是stroke()的话，将会只绘制一条半弧线。在没有关闭路径的情况下，fill()会默认绘制一条从结束点至起始点的路径，然后填充该区域，而stroke()则不会。

#### moveTo()、lineTo()
moveTo()和lineTo()的使用如下：
- moveTo(x,y)：把路径移动到画布中的指定点，不创建线条
- lineTo(x,y)：添加一个新点，然后在画布中创建从该点到最后指定点的线条

需要注意的是:
- 如果没有 moveTo 那么第一次 lineTo 的就视为 moveTo
- 每次lineTo后如果没有moveTo，那么下次lineTo的开始点为前一次lineTo的结束点。

这两个方法通常用来绘制直线
```
var canvas = document.getElementById("canvas");
var context = canvas.getContext("2d");
var cw = canvas.width = 400;
var ch = canvas.height = 400;

context.beginPath();
context.lineTo(200, 200);
context.lineTo(200, 100);
context.lineTo(100,50);
context.strokeStyle = '#fff';
context.stroke();
```
样式 | 描述
---|---
lineCap | 设置或返回线条的结束端点样式
lineJoin | 设置或返回两条线相交时，所创建的拐角类型
lineWidth | 设置或返回当前的线条宽度
miterLimit | 设置或返回最大斜接长度

#### 样式
属性 | 描述
---|---
fillStyle | 设置或返回用于填充绘画的颜色、渐变或模式
strokeStyle | 设置或返回用于笔触的颜色、渐变或模式
shadowColor | 设置或返回用于阴影的颜色
shadowBlur | 设置或返回用于阴影的模糊级别
shadowOffsetX | 设置或返回阴影距形状的水平距离
shadowOffsetY | 设置或返回阴影距形状的垂直距离
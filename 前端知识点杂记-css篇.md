### 前端之css篇
1. chrome对中文字体的渲染最小支持到12px，英文则没有限制。如果要设置更小的字体，可以使用webkit的私有属性-webkit-text-size-adjust:none来设置。设置该属性之后网页在缩放时会按照设置的字体显示而不进行缩放，影响用户体验，所以不建议设置为全局属性。建议使用-webkit-transform:scale(缩小比例)对文字区域局部设置。

2. 不定宽元素水平居中
- 对元素设置display:table;，告诉浏览器元素的最小宽度，再设置margin: 0 auto;使元素居中。
- 对元素设置display: flex; justify-content: center; justify-content用于检索弹性盒模型元素在横向上的对齐方式。

3. 在使用中前端框架（如bootstrap等）的栅格系统时要注意将其包裹在定义的行（container）内。

4. 如果要使某元素漂浮，最好让位置在它前面的兄弟元素漂浮，否则可能达不到漂浮效果。

5. 页面图片拼接时要对img设置display:block，图片空隙就会消失。

6. 对于可能存在命名冲突的class，在编写其样式时，尽量使用层级选择（即通过选择其父元素下的子元素）来避免命名冲突，以防止样式覆盖的发生。

7. 对于网页的字体设置一般来为：
   移动端项目：
```
font-family:Tahoma,Arial,Roboto,”Droid Sans”,”Helvetica Neue”,”Droid Sans Fallback”,”Heiti SC”,sans-self;
```
PC端项目：
```
font-family:Tahoma,Arial,”Helvetica Neue“,”Hiragino Sans GB”,Simsun,sans-self;
```
移动和PC端项目：
```
font-family:Tahoma,Arial,Roboto,”Droid Sans”,”Helvetica Neue”,”Droid Sans Fallback”,”Heiti SC”,”Hiragino Sans GB”,Simsun,sans-self;
```

8. 在书写元素的css属性的时候，尽量按照{定位，盒模型，对元素的渲染}来写。

9. 最好为body添加一个行高，这样子元素能继承总的行高而不必为每个元素单独设置。

10. .css的黑魔法，让任何元素垂直居中
```
html,body{
    height: 100%;
    margin: 0;
}
body{
    -webkit-align-items: center;
    -ms-flex-align: center;
    align-items: center;
    display: -webkit-flex;
    display: flex;
}
```
利用了flex弹性盒模型的属性

11. 避免页面因出现滚动条而闪动的问题，对页面居中元素的父元素设置`margin-left:calc(100vm-100%);`或者`padding-left:calc(100vm-100%);`在屏幕比较小的情况下要做响应式处理。

12. 元素水平居中的方法：
- 对元素设置宽度，使用`margin: 0 auto;`
- 对该元素的父元素设置`position:relative`,对该元素设置`position:absolute;left:50%;,margin-left:-宽度px;`
- 对父元素设置`text-align:center`

13. 清除浮动建议少使用`overflow：hidden; zoom:1;`因为会产生太多的局限性

14. 关于页面中清除浮动的方法：
- 对元素`display:inline-block`该方法可以使换行被解析，从而达到清除浮动的目的；
- 给父级也加浮动（这种情况当父级`margin:0 auto;`时不居中
- 3.在浮动元素下加`<div class="clear"></div>`(不建议使用此方法，会产生不必要的空元素影响页面解析)
- 在浮动元素下加`<br clear="all”>`
- 给浮动元素的父级加`{zoom：1}`
- 给浮动元素的父级加`{overflow：auto}`

15. 一般情况下，css中要避免使用滤镜。因为浏览器在加载图片时它会终止内容的呈现并且冻结浏览器。每当一个元素时它都要运算一次（不仅仅是<img>），这样就增加了额外的内存开支，影响到页面的加载速度。如果要在IE7以下的版本对图片使用半透明效果，建议使用png8格式的图片。

16. css表达式是动态设置css属性的强大(但危险)的方法，书写css时尽量避免使用css表达式，表达式在页面呈现、大小改变时会自动求值，页面滚动甚至用户鼠标移动过的时候也会求值，这会加大内存开支，影响加载速度。

17. 像素概念区别
###### 物理像素：
即设备像素，设备能控制显示的最小单位，可以理解成这些像素就是显示器上的一个一个的点。

###### CSS像素：
web编程的一个概念，独立于设备的用于逻辑上衡量像素的单位，也就是在制作网页时通常所说的像素单位，一个抽象的实际不存在的单位。

###### 设备独立像素：
也叫密度无关像素，可以认为是计算机坐标系统中的一个点，这个点代表一个可以由程序使用并控制的虚拟像素，然后再由系统转换为物理像素。简单的来说就是独立于设备只是用于逻辑上衡量像素的单位。

**可以通过javascript中的window.devicePixelRatio来获取设备中的像素比值。
一个物理像素并不一定对应一个设备独立像素，他们之间有一个比值，这就是Retina屏幕为什么显示的样子跟你定义的宽高不一致的原因。**

18. css单位  
**dppx**:每像素有多少点  
**dpi**:每英尺有多少点
- 普通屏幕通常包含96dpi，一般将2倍于此的屏幕称之为高分屏，即大于等于192dpi的屏幕，比如Mac视网膜屏就达到了192dpi（即2dppx），打印时一般会需要更大的dpi；
- 1dppx = 96dpi
- 1dpi ≈ 0.39dpcm
- 1dpcm ≈ 2.54dpi
- 1in = 2.54cm = 25.4 mm = 101.6q = 72pt = 6pc = 96px

19. viewport属性：
- width、height控制视窗的大小；
- initial-scalech初始缩放比例；
- maximum-scale允许用户缩放的最大比例；
- minimum-scale允许用户缩放的最小比例；
- user-scalable是否允许用户手动缩放。

20. 在浏览器中，内联元素(inline-block)默认会有4px的间隔，以下方法解决：
- 元素设置浮动脱离流式布局，这种方法可能会影响元素本身的定位
- 利用元素的盒模型，设置`margin:-4px`解决，尽量不要改变盒模型
- 对元素的父元素设置`font-size:0`清除所有空格，再对元素设置`font-size`，建议使用本方法。
- 
21. 模态框底层允许活动，可以在这张层设置`point-events:none`使得鼠标可以穿透遮罩层，模态框需设置成auto。
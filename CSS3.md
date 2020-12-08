CSS3是CSS2.1的升级版，它是对CSS的一个扩展。

#### 1.兼容

CSS3不是属于浏览器或同一浏览器的不同版本都支持，所以需要兼容处理。

1. 主流浏览器内核

   - Trident：IE内核

   - WebKit：Chrome和Safari内核

   - Gecko：FireFox内核

   - Blink（是WebKit的一个分支）：Chrome和Opera内核

     **目前国内的浏览器大多都是双核的（IE内核 + Chrome内核）**

2. 厂商前缀

   - IE：-ms-
   - Chrome&Safari:  -webkit-
   - FireFox: -moz-
   - Opera:  -o-

#### 2.新特性

1. [选择器](#3选择器)
2. 阴影
3. 形状转换（2D <-> 3D）
4. [变形](#变形)
5. [动画（过渡动画、帧动画）](#动画)
6. [边框](#边框)
7. [背景](#背景)
8. 反射
9. [文字](#文本)
10. [颜色（rgba/hsl/hsla）](#颜色)
11. 滤镜（filter）
12. [弹性布局](#弹性布局)
13. [多列布局](#多列布局)
14. [盒模型](#盒模型)
15. [Web字体](#Web字体)
16. [媒体查询](#媒体查询)

#### 选择器

1. 属性选择器

   ```
   <style>
   	p[class], p[class=content]{ // p标签上class属性的和class=content的设置字体颜色
   		color: #f00;
   	}
   	p[class^=content]{ // p标签上以class=content的开头的属性设置字体颜色
   		color: #f00;
   	}
   	p[class$=content]{ // p标签上以class=content的结尾的属性设置字体颜色
   		color: #f00;
   	}
   	p[class*=content]{ // p标签上以class属性中包含content的设置字体颜色
   		color: #f00;
   	}
   </style>
   ```

2. 结构性伪类

   ```
   <style>
   	/* 1.:root 匹配html标签，和body选择器效果一样 */
   	:root{
   		background-color: #fdc7ff;
   	}
   	/* 2.子元素选择: 匹配父元素中连续的子元素 */
   	:first-child: 第1个子元素
   	:last-child: 最后1个子元素
   	:nth-child(n): 第n个子元素 2n表示2的倍数 2/4/6，3n+1表示3的倍数+1 4/7/11
   	:nth-last-child(n): 倒数第n个子元素
   	/* 3. :nth-of-type类，用于匹配父元素中兄弟子元素，可以用于子元素非连续的情况 
   		:nth-of-type(n)
   		:nth-last-of-type(n)
   	*/
   	p:nth-of-type(3){ // 找的是p标签中第3个兄弟p标签，如果第3个不是p标签，将跳过，继续向下查找，直到找到为止。
   		color: #4e9033;
   	}
   	p:nth-last-of-type(3){ // 找的是p标签中倒数第3个兄弟p标签，如果第3个不是p标签，将跳过，继续向下查找，直到找到为止。
   		color: #4e9033;
   	}
   	/* 4. 其它 
   		:only-child 父元素中仅有一个子元素
   		:only-of-type 父元素中仅有一个兄弟元素,选择父元素唯一的子元素
   		:empty 没有子元素，包含文本元素
   	*/
   </style>
   ```

3. 目标伪类

   ```
   <style>
   	:target{
   		color: red;
   	}
   </style>
   ```

4. UI元素状态伪类

   ```
   <style>
   	input:disabled{
   		background-color: #ff0;
   	}
   	input:enabled{
   		background-color: #ff0;
   	}
   	input:checked{ /* :checked 只在Opera中有效 */
   		background-color: #ff0;
   	}
   	select::selection{ /* :selection 只在Opera中有效，高亮显示被选中的文本 */
   		background-color: #ff0;
   	}
   </style>
   ```

5. 否定伪类

   ```
   <style>
   	:not(p){ /* 非p标签 */
   		background-color: #ff0;
   	}
   </style>
   ```

6. 通用兄弟元素选择器

   ```
   <style>
   	.div1~.div2{ /* 兄弟元素 */
   		background-color: #ff0;
   	}
   </style>
   ```

#### 文本

1. 文本阴影

   `text-shadow`: 水平偏移距离 垂直偏移距离 [模糊距离] [阴影的尺寸] [颜色] [inset];

2. 文本自动换行

   `word-wrap: normal(默认，浏览器默认处理) | break-word(在长单词内部换行)` 

3. 单词拆分

   `word-break: normal | break-all | keep-all(只能在半角或连字符处换行)`

4. 文本溢出

   单行文本溢出：`text-overflow: hidden | nowrap | ellipsis`

   ​	处理文字溢出样式：

   ​		`width: px/%/em/rem;`

   ​		`white-space: nowrap;`

   ​		`text-overflow: ellipsis;`

   ​		`overflow: hidden;`

   多行文本溢出: 

   ​	`width: px/%/em/rem;`

   ​	`display: -webkit-box;`

   ​	`-webkit-box-orient: vertical;`

   ​	`-webkit-line-clamp: 行数;`

   ​	`overflow: hidden;`

#### 边框

1. 圆角

   `border-radius: 10px;`四个角都是10px

   `border-radius: 10px 20px;` 第一个参数是左上和右下，第二个参数是右上和左下

   `border-radius: 10px 20px 10px;` 第一个参数是左上，第二个参数是右上和左下，第三个参数是右下

   `border-radius: 10px 20px 10px 10px;` 分别对应的是左上、右上、右下、左下

   四个方位的词：top-left/top-right/bottom-left/bottom-right

2. 阴影（IE9以上支持）

   `text-shadow: 水平偏移距离 垂直偏移距离 [模糊距离] [阴影的尺寸] [颜色] [inser|outset]`

3. 图片（IE11.0以上版本支持）

   `border-image: 图片路径 向内偏移距离 宽度 图像趋于超出边框距离 重复效果;`

   重复效果：repeat/round/stretch

#### 背景

1. 多重背景

   `background: 背景色 背景图片 平铺方式 位置, 背景色 背景图片 平铺方式 位置;`

   `background-image: url();` 图片路径

   `background-position: 0 0;` 位置

   `background-repeat: no-repeat;` 平铺方式

2. `background-size: length(固定长度)|percentage(百分比值)|cover|contain;`

3. `background-origin: 指定背景图像的位置区域;`

   `background-origin: padding-box(相对于内边距框定位)|border-box(相对于边框盒定位)|content-box(相对于内容框定位);`

4. `background-clip: 设定背景的绘制区域;`

   `background-clip: border-box|padding-box|content-box;`

5. 渐变

#### 颜色

1. `rgba(r, g, b, a);`

   r: 红色                     取值范围：0-255/0-100%

   g: 绿色					取值范围：0-255/0-100%

   b: 蓝色					取值范围：0-255/0-100%

   a: 不透明度			取值范围：0-1的一个小数

2. HSL

   `background-color: hsl(h, s, l);`			

   h: 色调					取值范围：0-360

   s: 饱和度				 取值范围：0-100%

   l: 亮度					 取值范围：0-100%

3. HSLA

   `background-color: hsla(h, s, l, a);`

   h: 色调					取值范围：0-360

   s: 饱和度				 取值范围：0-100%

   l: 亮度					 取值范围：0-100%

   a: 不透明度			取值范围：0-1的一个小数

#### 透明度

调整元素的不透明度，大多数情况下用于做元素的遮罩效果。取值范围：0-1的一个小数

IE8及8以下版本不支持opacity，处理兼容的方式需再添加一行代码来处理。

​	filter: alpha(opacity=数值)       数值范围：0-100

#### 渐变

渐变主要用来设置背景或制作三维图。

1. 线性渐变

   `background: liner-gradient(方向或角度, 颜色1 百分比, 颜色2 百分比, ...);`

   方向：

   ​		to left: 从右向左渐变

   ​		to right: 从左向右渐变

   ​		to top: 从下向上渐变

   ​		to bottom: 从上向下渐变

   ​		to top left: 从右下角向左上角渐变

   ​		to top right: 从左下角向右上角渐变

   ​		to bottom left: 从右上角向左下角渐变

   ​		to bottom right: 从左上角向右下角渐变

   角度：

   ​		比如45度角，应该表示为：45deg

   颜色取值：

   ​		1) 表示颜色的单词

   ​		2）16进制颜色

   ​		3）表示颜色的函数（rgb()/rgba()/hsl()/hsla()...）

2. 径向渐变(沿半径方向渐变)

   `background: radial-gradient(形状 渐变大小，位置，颜色1，...，颜色n);`

   形状：

   ​		ellipse: 椭圆径向渐变(默认)

   ​		circle: 圆径向渐变

   渐变大小：

   ​		farthest-corner: 渐变的半径长度为从圆心到离圆心最远的角(默认)

   ​		closest-side: 渐变的半径长度为从圆心到离圆心最近的边

   ​		closest-corner: 渐变的半径长度为从圆心到离圆心最近的角

   ​		farthest-side: 渐变的半径长度为从圆心到离圆心离最远的边

   ```
   <style>
   	.box{
   		width: 300px;
   		height: 300px;
   		background: radial-gradient(circle closest-corner at 25% 75%, red, green);
   	}
   </style>
   ```

   位置：

   ​		center: 设置圆心在中心位置

   ​		top: 设置圆心在顶部位置

   ​		bottom: 设置圆心在底部位置

   ​		at 圆心横坐标 圆心纵坐标：设定圆心的位置

3. 文字渐变

   `background-image: 线性渐变或径向渐变;`

   `-webkit-background-clip: text;`

   `-webkit-text-fill-color: transparent;`

#### 盒模型

允许以某种方式定义某些元素，以适应指定的区域。

`box-sizing: content-box/border-box;`

#### 变形

`transform: translate(200px);` 只带一个参数表示 x方向位移值为200px，y方向为0

语法：`transform: none|*transform-functions*;`

| 值                                                           | 描述                                    |
| :----------------------------------------------------------- | :-------------------------------------- |
| none                                                         | 定义不进行转换。                        |
| matrix(*n*,*n*,*n*,*n*,*n*,*n*)                              | 定义 2D 转换，使用六个值的矩阵。        |
| matrix3d(*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*) | 定义 3D 转换，使用 16 个值的 4x4 矩阵。 |
| translate(*x*,*y*)                                           | 定义 2D 转换。沿x和y轴移动元素。        |
| translate3d(*x*,*y*,*z*)                                     | 定义 3D 转换。                          |
| translateX(*x*)                                              | 定义转换，只是用 X 轴的值。             |
| translateY(*y*)                                              | 定义转换，只是用 Y 轴的值。             |
| translateZ(*z*)                                              | 定义 3D 转换，只是用 Z 轴的值。         |
| scale(*x*[,*y*]?)                                            | 定义 2D 缩放转换。                      |
| scale3d(*x*,*y*,*z*)                                         | 定义 3D 缩放转换。                      |
| scaleX(*x*)                                                  | 通过设置 X 轴的值来定义缩放转换。       |
| scaleY(*y*)                                                  | 通过设置 Y 轴的值来定义缩放转换。       |
| scaleZ(*z*)                                                  | 通过设置 Z 轴的值来定义 3D 缩放转换。   |
| rotate(*angle*)                                              | 定义 2D 旋转，在参数中规定角度。        |
| rotate3d(*x*,*y*,*z*,*angle*)                                | 定义 3D 旋转。                          |
| rotateX(*angle*)                                             | 定义沿着 X 轴的 3D 旋转。               |
| rotateY(*angle*)                                             | 定义沿着 Y 轴的 3D 旋转。               |
| rotateZ(*angle*)                                             | 定义沿着 Z 轴的 3D 旋转。               |
| skew(*x-angle*,*y-angle*)                                    | 定义沿着 X 和 Y 轴的 2D 倾斜转换。      |
| skewX(*angle*)                                               | 定义沿着 X 轴的 2D 倾斜转换。           |
| skewY(*angle*)                                               | 定义沿着 Y 轴的 2D 倾斜转换。           |
| perspective(*n*)                                             | 为 3D 转换元素定义透视视图。            |

1. matrix(a, b, c, d, e, f) 定义2D变形，使用了6个值的矩阵，表示如下：

​	a	c	e

​	b	d	f

​	0	0	1

​	matrix用一个3行3列的矩阵表示，a和b列表示x轴，c和d列表示y轴，e和f列表示z轴

​	a和b表示缩放（如果没有缩放，值设为1）

​	b和c表示扭曲（如果没有扭曲，值设为0）

​	e和f表示位移（如果没有位移，值设为0）

​	如果旋转角度为θ，它会影响到a,b,c,d的值：

​			a = cosθ

​			b = sinθ

​			c = -cosθ

​			d = cosθ

​	如果扭曲skew(θ1, θ2)，会影响到b和c的值

​			b = tanθ1

​			c = tanθ2

2. `transform-origin: x-axis y-axis z-axis;` 调整元素的基点

​	属性值：

​			x-axis：定义视图被置于X轴的何处。可能的值：left / center / right / length / %。

​			y-axis：定义视图被置于Y轴的何处。可能的值：top / center / bottom / length / %。

​			z-axis：定义视图被置于Z轴的何处。可能的值：length。

3. perspective

   让子元素获得透视效果。但是该属性要加在父元素的样式中。

   `perspective: length|none;`

   主流浏览器都不支持，谷歌要加-webkit-，或在长度后面加单位。

4. transform-style

   在 3D 空间中呈现被嵌套的元素（必须与transform属性一同使用）

   `transform-style: flat|preserve-3d;`


#### 动画

##### 1.过渡动画

1)常规用法

​		`transition-property:`

​		`transition-deration:`

​		`transition-timing-function:`

​		`transition-delay:`

2）间接（复合）用法：

`transition:property-name-list|all duration timing-function delay;`

a) 可以使用的属性有：

​	i) 颜色：

​			color  background-color   border-color  outline-color

​	ii) 位置：

​			background-position  left  right  top  bottom

​	iii) 长度：

​			max-height  min-height  max-width  min-width  height   width  border-width  margin  padding  

​			outline-width   outline-offset  font-size  line-height  text-indent  vertical-align  border-spacing

​			letter-spacing  letter-spacing  word-spacing

​	iv) 数字：

​			opacity  visibility  z-index  font-weight  zom

​	v) 组合：

​			text-shadow  transform  box-shadow  clip

​	vi) 其它：

​			gradient

b) duration: 动画持续时间，一般以秒(s)或毫秒(ms)为单位

c) timing-function: 动画函数

​		i) linear: 匀速

​		ii) ease: 变速(先慢后快，最后再慢)

​		iii) ease-in: 变速(由慢到快)

​		iv) ease-out: 变速(由快到慢)

​		v) ease-in-out: 变速(慢速开始，慢速结束)

​		vi) cubic-bezier(n, n, n, n): 自行设定变速，n的值在0-1之间

d)  delay: 动画延时时间，一般以秒(s)或毫秒(ms)为单位

##### 2.关键帧动画

​	步骤：

​		1）设置关键帧

​			a）如果只有两个关键帧：

​				@keyframes 动画名 {

​						0%: {样式表}

​						100%: {样式表}

​				}

​				或：

​				@keyframes 动画名 {

​						from: {样式表}

​						to: {样式表}

​				}

​			b）如果是多个关键帧：

​				@keyframes 动画名 {

​						0%: {样式表}

​						25%: {样式表}

​						...

​						100%: {样式表}

​				}

​				注意： 这里的百分比一般是升序值，可以试试0%-100%之间的任意值，也可以是倒序。

​	2）实施动画

​			a）常规用法：

​				`animation-name:` 来自于@keyframes定义的动画名

​				`animation-duration:` 动画持续时间，一般以秒(s)或毫秒(ms)为单位(默认为0)

​				`animation-timing-function:`动画函数

​						i) linear: 匀速

​						ii) ease: 变速(先慢后快，最后再慢)

​						iii) ease-in: 变速(由慢到快)

​						iv) ease-out: 变速(由快到慢)

​						v) ease-in-out: 变速(慢速开始，慢速结束)

​						vi) cubic-bezier(n, n, n, n): 自行设定变速，n的值在0-1之间

​				`animation-delay:`动画延时时间，一般以秒(s)或毫秒(ms)为单位

​				`animation-iteration-count:`动画循环播放的次数

​						i) number: 按设定次数循环播放(默认次数为1次)

​						ii) infinite: 一直循环播放

​				`animation-direction:`动画播放完后是否反向播放

​						i) normal: 不反向(默认值)

​						ii) alternate: 反向

​				`animation-play-state:`动画播放或停止播放

​						i) paused: 停止播放

​						ii) running: 播放(默认值)

​			b）简洁用法：

​				`animation: name duration timing-function delay iteration-count direction;`

#### 多列(分栏)布局

`column-count: number|auto;` 规定元素应该被分隔的列数（栏数）。

`column-gap: length|normal;` 设置栏间距。

`column-rule`  设置栏间分隔线

​	column-rule-style:

​			none  定义没有规则

​			hidden  定义隐藏规则

​			dotted  定义点状规则

​			dashed  定义虚线规则

​			solid  定义实线规则

​			double  定义双线规则

​			groove  3D 沟槽效果

​			ridge  3D脊状效果

​			insert  3D左上角阴影效果

​			outset  3D右下角阴影效果

​		注意：

​				3D线型在分栏中没有3D效果，当实线处理了。

​	column-rule-width: 设置线宽

​	column-rule-color: 设置分隔线颜色

​	简洁（复合）写法：

​			`column-rule: width style color;`

`column-width: length|auto;` 设置栏宽

columns: 规定设置  column-width 和 column-count 的简写方式。

#### 弹性布局

CSS 弹性盒（Flexible Box 或 flexbox），是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式。

目的：是提供一种更加有效的方式来堆一个容器中的子元素进行排列、对齐和分配空白空间。

属性：

1. flex-direction 指定子元素在父容器中的位置（应用于父元素）

   语法：

   ​		flex-direction: row | row-reverse | column | column-reverse

   参数：

   ​		row:  横向从左到右排列(左对齐)，默认的排列方式。

   ​		row-reverse：反转横向排列（右对齐，从后往前排，最后一排在最前面）。

   ​		column: 纵向排列。

   ​		column-reverse: 反转纵向排列，从后往前排，最后一项排在最上面。

2. justify-content（应用于父元素）

   把弹性项沿着弹性容器的主轴线对齐

   语法：

   ​		justify-content: flex-start | flex-end | center | space-between | space-around

   参数：

   ​		flex-start：紧凑方式左对齐

   ​		flex-end：紧凑方式右对齐

   ​		center：紧凑方式居中对齐

   ​		space-between：除了第一个和最后一个子元素外，其它子元素等分空白区域

   ​		space-around：所有子元素等分空白区域

3. align-items（应用于父元素）

   子元素在侧轴（纵轴）方向上的对齐方式。此属性作用于父容器。

   语法：

   ​		align-items: flex-start | flex-end | center | baseline | stretch

   参数：

   ​		flex-start：沿纵轴顶端对齐

   ​		flex-end：沿纵轴底端对齐

   ​		center：沿纵轴垂直居中对齐

   ​		baseline：沿纵轴基线对齐

   ​		stretch：纵轴拉伸对齐

4. flex-grow（应用于子元素）

   子元素的放大比例，默认为0，即如果存在剩余空间，也不放大。

   语法：

   ​		flex-grow: number;

5. flex（应用于子元素）

   用于指定弹性子元素如何分配空间。

   语法：

   ​		flex: auto | initial | none | inherit | [flex-grow] || [flex-shrink] || [flex-basis]

   参数：

   ​		auto：等价于1 1 auto。

   ​		initial：等价于0 1 auto。

   ​		none：等价于 0 0 auto。

   ​		inherit：从父元素继承。

   Tips：

   ​		flex可以带1-3个参数。

   ​		1）带1个参数

   ​				a）无单位，这个数值会被当作flex-grow（放大）的值。

   ​				b）带单位，这个数值会被当作flex-basis（基本宽度）的值。

   ​				c）auto(自动宽度) | initial(初始宽度) | none(无)

   ​		2）带2个参数

   ​				第1个参数必须是一个无单位的数值，它会被当作flex-grow的值。

   ​				第2个参数：

   ​						a）无单位，这个数值会被当作flex-shrink（收缩比率）的值。

   ​						b）带单位，这个数值会被当作flex-basis（基本宽度）的值。

   ​		3）带3个参数

   ​				第1个参数必须是一个无单位的数值，它会被当作flex-grow的值。

   ​				第2个参数必须是一个无单位的数值，它会被当作flex-shrink（收缩比率）的值。

   ​				第3个参数必须是一个有效的宽度值（带单位），它会被当作flex-basis（基本宽度）的值。

#### 响应式布局

1. 概念

   Responsive Design，在实现不同屏幕分辨率的终端上浏览网页的不通展示方式。通过响应式设计能使网站在手机和平板电脑上有更好的浏览阅读体验。

2. 响应式布局和自适应布局的区别（面试问题）

   响应式布局只开发一套代码，通过检测视口的分辨率，针对不同客户端在客户端做代码处理，来展现不同的布局和内容。

   自适应需要开发多套界面，通过检测视口的分辨率，来判断当前访问的设备是PC端、平板、手机等，从而请求服务层，返回不同的页面。

   响应式布局等同于流动网格布局，而自适应等同于使用固定分割点来进行布局。

   自适应布局给出了更多的设计空间，只用考虑几种不同的状态就可以了；而响应式布局要考虑上百种状态，虽然有些状态差异较小，但也要考虑到。

3. 开发实现方法

   1. 媒体查询
   2. 百分比布局
   3. rem布局（相对于根节点(根元素)html中的字号布局）
   4. 视口单位布局(vw/vh)

4. 响应式设计步骤

   1. 设置meta标签

   2. 通过媒体查询来设置样式

   3. 设置多种视图的宽度

      i）宽度需要使用百分比/ rem /vw$vh等

      ii）处理图片缩放

      iii）其他属性处理

      ​	 如pre/iframe/video等，都要缩放其大小，table，建议不要增加padding属性，低分辨率下要使用内容居中操作。

#### 媒体查询

步骤：

1. 设置meta标签

   `<meta content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no, viewport-fit=cover" name="viewport">`

   说明：

   ​		以上标签的内容只能被移动设备识别

   ​		viewport： 视口（移动端）

   ​		width=device-width：宽度等于当前设备的宽度

   ​		initial-scale=1： 初始缩放比例（默认为1.0）

   ​		minimum-scale=1：允许用户缩放到的最小比例（默认为1.0）

   ​		maximum-scale=1：允许用户缩放到的最大比例（默认为1.0）

   ​		user-scalable=no：用户是否可以手动缩放（默认为no）

2. 设置IE渲染方式默认为最高版本

   `<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">`

   说明：

   ​		以上代码表示如果浏览器有chrome插件，将以chrome提供的V8引擎渲染页面；如果没有，将以IE的最高版本渲染页面。

3. 引入兼容的JS文件

   ```
   <!-- [if it IE 9]>
   	<script src="https://oss.maxcdn.cm/libs/html5shiv/3.7.0/html5shiv.js"></script>
   	<script src="https://oss.maxcdn.cm/libs/responed/responed.min.js"></script>
   <![endif]>
   ```

   说明：

   ​		因为IE8及IE8以下版本既不支持html5，也不支持CSS3 Media，所以我们需要加载JS文件来处理这个兼容。上面的代码是一个注释语句，也就是说，IE及以上的版本不会编译这几行代码。

4. 进入CSS3提供的媒体查询

   ```
   <link rel="stylesheet" href="css/480.css" meta="screen and (max-width: 480px)" >
   <link rel="stylesheet" href="css/800.css" meta="screen and (min-width: 480px) and (max-width: 800px)" >
   ```

   设备：

   ​		all：所有设备

   ​		screen：PC端显示器

   ​		print：打印机或打印预览图

   ​		handheld：便携设备

   ​		TV：电视

   ​		speech：音频合成器

   ​		Braille：盲人点触设备

   ​		embossed：盲人打印机

   ​		projection：摄影设备

   ​		tty：固定密度字母栅格设备

   ​		only：用来排除不支持媒体查询的浏览器

#### Web字体

开发者引入外部字体。

语法：

```
@font-face {
	font-family: 字体名;
	src: url("字体文件") format("字体文件格式以处理浏览器兼容"), url(字体文件.woff) format();
}
```

说明：

​		可以同时引入多个字体文件，字体一样，文件的扩展名一样，目的是为了处理浏览器兼容。

iconfont图标字体

由阿里巴巴提供的一种字体图标
## CSS基础

css:层叠样式表，用来美化网页。做到结构(HTML)和表现(CSS)分离

#### 1.基本语法

​	选择器 {

​			属性: 属性值;

​	}

#### 2.引用方式

- 行间样式

  直接在标签上书写样式

- 内部样式

  在文件的内部书写样式

  <style>
      样式内容
  </style>

- 外部样式

  先创建一个.css文件，再用link标签引入这个文件

- 导入外部样式

  先创建一个.css文件，在style标签中用@import导入这个样式文件

区别：

​		行间样式只作用于当前标签，内部样式作用于当前文件，外部样式可以被多个HTML文件引用。

​		在实际项目开发中，最好使用外部样式。

​		外部样式分为link引入 和 import 引入两种方式，其区别为：

​			1. link引用css文件时，是在页面载入的同时加载；无兼容问题；支持使用javascript控制DOM修改样式

​			2. @import是网页完全载入以后加载；css2.1提出的，低版本浏览器不兼容；不支持js控制DOM修改样式

#### 3.选择器

##### 3.1分类

- `* `匹配html中所有元素 (注意：`*`的性能差，因为他要匹配所有元素，所以在开发时，不建议使用)

- 标签选择器：用来匹配对应的标签

- 类选择器：用来选择class命名的标签

- ID选择器：用来选择id命名的标签

- 派出选择器：根据上下文来确定选择标签

  ```
  ul li{
  	color: red;
  }
  ```

- 伪类选择器

  伪类：专门用来表示元素的一种特殊状态。

  `:before / :after / :first-letter / :first-line`  前面可以是1个冒号也可以是双冒号

  `::selection / ::placeholder / ::backdrop`  前面只能是双冒号

  常用伪类选择器：

  1. a标签的伪类： `:link/:visited/:hover/:active`
  2. `:focus`   获得焦点
  3. `:first-child/:last-child/:nth-chlid(number)`

- 属性选择器

  1. `[属性名]:包含有指定属性名的元素` (常用)

     ```
     <style>
     	div.content[title]{
     		font-weight: bold;
     	}
     </style>
     ```

  2. `[属性名=值:属性名的值为指定值的元素]` (常用)

     ```
     <style>
     	input[name=user]{
     		background-color:#eee;
     	}
     </style>
     ```

  3. `[属性名~=值]:属性名的值包含指定值的元素`

     ```
     <style>
     	div[class~=box]{
     		background-color:#eee;
     	}
     </style>
     ```

  4. `[属性名^=值]:属性名的值以指定值的开头的元素`

     ```
     <style>
     	div[class^=box]{
     		background-color:#eee;
     	}
     </style>
     ```

  5. `[属性名$=值]:属性名的值以指定值的结尾的元素`

     ```
     <style>
     	div[class$=box]{
     		background-color:#eee;
     	}
     </style>
     ```

- 关系选择器

  根据元素与元素之间所处关系来选择元素。

  1. `空格` 后代选择器

     ```
     <style>
     	div span{ /* div下所有span标签的文字颜色设置 */
     		color:red;
     	}
     </style>
     ```

  2. `>`  只选择儿子元素

     ```
     <style>
     	div>span{ /* div下第一层span标签的文字颜色设置 */
     		color:red;
     	}
     </style>
     ```

  3. `+`  兄弟选择

     ```
     <style>
     	ul li+li+li{ /* ul下的第一个li的兄弟的兄弟 */
     		color:red;
     		list-style-type: none;
     	}
     </style>
     ```

##### 3.2选择器分组

让多个选择器（元素）具有相同的样式，一般用于设置公共样式。

```
span, img, i{
	display: inline-block;
}
```

##### 3.3选择器的继承

子元素可以继承父元素的样式，反之不行。

##### 3.4权重

!important(10000) > 内联样式(1000) > id选择器(100) > 类、伪类选择器(10) > 标签选择器(1)

#### 4.字体

##### 4.1属性

1. `font-size`  字号(px/%)
2. `font-sfamily `  字体
3. `font-style`   文字样式(normal/italic(斜体)/oblique(倾斜)/inherit(从父元素继承字体样式))
4. `font-weight`    文字粗细(normal(400)/bold(700)/bolder/lighter/100-900)
5. `line-height`    行高(px/数字/em等)
6. `color`  文字颜色(rgb(255,255,255) / #eee / #rrggbb)
7. `text-decoration`   文字修饰(normal/underline(下划线)/overline(上划线)/line-through(删除线))
8. `text-align ` 文本对齐方式(left/center/right)
9. `text-transform`  字母大小写(capitalize(每个单词首字母大写)/uppercase(全部大写)/lowercase(全部小写)/none)
10. `text-index ` 文本缩进(px/em/%/pt等)

font复合属性：

​	`font: font-style font-variant font-weight font-size/line-height font-family;`

  注意：

- 属性值的位置顺序
- 除了font-size和font-family之外，其它任何一个属性值都可以忽略
- font-variant: 文本修饰(normal/small-caps(当大写字母变得小一些，如果没有大写字母那将会把所有字母全变成大写))		

#### 5.css背景

##### 5.1属性

1. `background-color`   背景色(transparent/color)
2. `background-image`    背景图(none/url)
3. `background-repeat`   背景图像铺排方式(repeat/no-repeat/repeat-x/repeat-y)
4. `background-position`  设置对象的背景图像位置({x-number | top | center | bottom} {x-number | top | center | bottom})
5. `background-attachment`   设置图像滚动位置(scroll/fixed)
6. `background`	设置背景的复合写法 `background: color image repeat attachment position`

#### 6.css浮动

##### 6.1 介绍

​	浮动就是让块级标签不独占一行。

​	目的：把块级标签元素可以排在一行上。

​	原理：就是让元素脱离文档流，不占用标准流。

​	**属性值**：

- left: 左浮动
- right:  右浮动
- none:  默认值。不浮动

##### 6.2清除浮动

目的：让后面的元素自动掉到下一行

方法：

1. 添加空标签，并设置样式:   clear: both;

    clear: left;  清除左浮动

   clear: right;  清除右浮动

   clear: both;  清除左右浮动

   clear: none;  左右浮动都不清除

2. 在要清除浮动的父级添加样式：   overflow: hidden;

   overflow: hidden; 超出部分隐藏，也可以用来实现清除浮动。

3. 在要清除浮动的父级添加伪元素，并设定样式

   父元素:after{

   ​	content: "";

   ​	display: block;

   ​	clear: both;

   }

#### 7.盒子模型

每个元素都是一个盒子，一个盒子由margin（外边距）,border（边框线）,padding（内边距）,content（内容）组成。

区别外边距和内边距是以边框为参照。

系统默认外边距为8px。

##### 7.1组成

1. 外边距(margin)：指元素边框线之外的距离。

   margin-left: 左边距

   margin-right: 右边距

   margin-top: 上边距

   margin-bottom: 下边距

   margin: 可以用来设置任意一个边的边距，可以带1至4个参数。

   ​			1个(apx)：表示上下左右都有这样的外边距apx

   ​			2个(apx bpx)：表示上下外边距apx 左右外边距bpx

   ​			3个(apx bpx cpx)：表示上外边距apx 左右外边距bpx  下外边距cpx

   ​			4个(apx bpx cpx dpx)：表示上外边距apx 右外边距bpx 下外边距cpx 左外边距dpx

2. 内边距(padding)：指元素的文本内容与边框之间的距离。

   它的用法与margin完全一样。

3. 边框(border)

   border-width: 边框线宽度

   border-style: 边框线样式

   border-color: 边框线颜色

   复合写法：border: border-width border-style border-color;

   ***注意**：border-width border-style border-color这三个参数没有位置之分。*

##### 7.2尺寸

​		盒子宽度 = width + padding左右 + border左右

​		盒子高度 = height + padding上下 + border上下

##### 7.3标准盒模型

`box-sizing: content-box; `

width 和 height 指的是内容区域的宽度和高度。

增加内边距、边框和外边距不会影响内容区域的尺寸，但是会增加元素框的总尺寸。 

##### 7.4IE盒模型

` box-sizing: border-box;`

 width 和 height 指的是内容区域+border+padding的宽度和高度。 

#### 8.table

table一般不用来布局，主要用来格式化数据。

##### 8.1属性

1. table属性

   width：宽度

   height：高度

   border：边框线

   border-collapse：collapse；单线边框

2. td, tr属性

   width：宽度

   height：高度

   border：边框线

   text-align： 文本左右对齐(left(默认)/center/right)

   vertical-align: 文本垂直对齐(top/middle(默认)/bottom)

#### 9.列表

不是描述性的文本的任何内容都可以认为是列表。比如：菜单、商品列表等

##### 9.1类型

无序(ul)、有序(ol)和自定义列表(dl)。

ul和ol的列表项都是用li表示的，而dl是由一个dt和一个或多个dd组成的。

dl一般用来设定一个定义，比如名词解释等。dt:  标题，dd: 描述，用来对dt的内容进行解释并说明的。

##### 9.2样式

​	用来修改标识类型

​	list-style-image: 用图像表示标识

​	list-style-position: 标识的位置 outside(默认值)/ inside

​	list-style-type: 标识类型

​			属性值：

​			a)无序

​				disc（默认，实心黑圆点）/circle（空心圆点）/square（实心黑方点）

​			b)有序

​				decimal(数字1,2,3 默认值)/decimal-leading-zero(01,02,03)/lower-roman(小写罗马数字i,ii,iii,iv)/upper-roman/lower-alpha(小写字母a,b,c,d)/upper-alpha/lower-greek/lower-latin/upper-latin

​	list-style: list-style-image list-style-position list-style-type; 这三个参数没有位置之分。

#### 10.布局

网站开发策略：先整体再局部，至顶向下，逐步细化。

#####  10.1定位布局

定位：设定元素在文档中的位置。会将标签(元素)转换为块级

分类：

1. static: 静态定位，

   默认值，没有定位，不能设置偏移值(left/top/right/bottom)，占用标准流（文档流）

2. relative: 相对定位

   占用标准流（文档流），它会出现在文档流中它该出现的位置。可以通过设置偏移值改变其位置。它相对于**自身所占的位置做偏移**

3. absolute: 绝对定位

   脱离文档流，默认相对于**body**做偏移。

   绝对定位一般与相对定位结合使用，它相对的父级是relative定义的元素做偏移。relative的元素必须是absolute的父级。

4. fixed: 固定定位

   脱离文档流，默认相对于**浏览器窗口左上角**(0,0)****做偏移，它与relative设定的对象没有关系，也就是说，它跟父级的定位没有任何关系。

注意：

`z-index: 0;` 默认为0

当多个元素添加绝对定位，元素将会叠加在一起，可以使用z-index设置元素显示的层次。

在static和relative中无用。

##### 10.2双飞翼布局

由三列组成，两端固定，中间自适应。

优点：因为在DOM中center在三列结构的最前面，因此可以实现主要内容的优先加载。

```
<div class="box">
	<div class="column center"></div>
	<div class="column left"></div>
	<div class="column right"></div>
</div>
<style>
.box{
	overflow: hidden; // 清除浮动
}
.column{
	float: left;
}
.center{
	width: 100%;
}
.left{
	width: 300px;
	margin-left: -100%;
}
.right{
	width: 300px;
	margin-left: -300px;
}
</style>
```

##### 10.3圣杯布局

由三列组成，两端固定，中间自适应。外观与双飞翼布局一样。

布局时与双飞翼相比增加了定位和偏移设置。

特点：

- header和footer各自占领屏幕所有宽度，高度固定。
- 中间的center是一个三栏布局
- 三栏布局两侧宽度固定，中间部分自动填充整个区域
- 中间部分的高度是三栏中最高区域的高度	

```
<body>
	<header class="header"></header>
	<div class="container">
		<div class="column center"></div>
		<div class="column left"></div>
		<div class="column right"></div>
	</div>
	<footer class="footer"></footer>
</body>
/* 样式 */
<style>
	.header, .footer{
		width: 100%;
		height: 150px;
	}
	.container{
		padding:0 30px;
		overflow: hidden;
	}
	.column{
		float: left;
		position: relative;
	}
	.left{
		width: 200px;
		marign-left: -100%;
		left: -200px;
	}
	.right{
		width: 200px;
		margin-left: -200px;
	}
</style>
```

##### 10.4侧边栏固定布局

###### 	10.4.1两栏布局

​				a)左侧固定，右侧自适应

​				b)右侧固定，左侧自适应

​				c)左右都固定

###### 	10.4.2三栏布局

​				a)左侧固定，中间自适应，右侧固定

​				b)左侧自适应，中间和右侧固定

​				c)左侧和中间固定，右侧自适应

#### 11.BFC&IFC

FC: formatting Context(格式上下文)。它是适应CSS2.1规范中的一个概念。它是页面中的一块渲染区域，并且有一套渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用。

分为：BFC和IFC。

##### 11.1BFC：块级格式上下文

​	a) 形成BFC的条件

​			i) 浮动元素（float除none以外的值）

​			ii) 定位元素（position(absolute/fixed)）

​			iii) display（值为inline-block/table-cell/table-caption时）

​			iv) overflow（值为hidden/auto/scroll）

​	b) BFC特性

​			i) 内部的盒子会在垂直方向上一个接一个的放置

​			ii) 垂直方向上的距离由 margin 的最大值决定 (如果不想margin叠加，需将其变成一个独立的容器 v)

​			iii) BFC的区域不会与float元素区域重叠

​			iv) 计算BFC的高度时，浮动元素也参与计算

​			v) BFC就是页面上的一个独立的容器，容器里面的子元素不会影响到外面的元素

​	c) BFC的作用

​			i) 解决margin重叠的问题（添加独立BFC）

​			ii) 解决浮动高度塌陷的问题（在父级添加overflow: hidden;）

​			iii) 解决侵占浮动元素的问题（添加overflow: hidden; 清除浮动）			

##### 11.2IFC: 内联（行级）格式上下文

​	a) 形成IFC的条件

​			i) font-size

​			ii) line-height

​			iii) height

​			iv) vertical-align

​	b) IFC特性

​			i) IFC的元素会在一行中从左至右排列

​			ii) 在一行上的所有元素会在该区域形成一个行框

​			iii) 行宽的高度为包含框的高度，高度为行框中最高元素的高度

​			iv) 浮动的元素不会在行框中，并且浮动元素会压缩行框的宽度

​			v) 行框的宽度容纳不下子元素时，子元素会换下一行显示，并且会产生新行框

​			vi) 行框的元素内遵循 text-align 和 vertical-align

容器的高度：

​		height  =  line-height  +  vertical-align


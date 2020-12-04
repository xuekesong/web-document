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

1. [选择器](#选择器)
2. 阴影
3. 形状转换（2D <-> 3D）
4. 变形
5. 动画（过渡动画、帧动画）
6. [边框](#5边框)
7. 多重背景
8. 反射
9. 文字
10. 颜色（rgba/hsl/hsla）
11. 滤镜（filter）
12. 弹性布局
13. 多列布局
14. 盒模型
15. Web字体
16. 媒体查询

#### 选择器

丰富

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

#### 4.文本

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

#### 5边框

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

#### 6.背景

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

#### 7.颜色

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

#### 8.透明度

调整元素的不透明度，大多数情况下用于做元素的遮罩效果。取值范围：0-1的一个小数

IE8及8以下版本不支持opacity，处理兼容的方式需再添加一行代码来处理。

​	filter: alpha(opacity=数值)       数值范围：0-100

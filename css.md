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


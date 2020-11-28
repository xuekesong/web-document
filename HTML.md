<!DOCTYPE html><!-- 表声明的意思，意思是下面的文档标签将以html5规范进行解析 -->
<html>
    <!-- 头部，主要用来完成一个网页的相关设置 -->
    <head>
        <meta charset="utf-8" /> <!-- 汉字编码 -->
        <meta name="keywords" content="设置一个网站的搜索关键字" />
        <meta name="description" content="设置网站的描述内容" />
        <title>网页标题</title>
        <link rel="shortcut icon" href="链接favicon.ico" /> <!--网站icon-->
        <style>内部样式</style>
    </head>
    <!-- 主体部分 -->
    <tbody></tbody>
    <!-- 脚本代码部分 -->
    <script></script>
</html>

## HTML

#### 1.概述

​	HTML：超文本标记语言。它是一种标识性语言，非编程语言，不能使用逻辑运算。通过标签将网络上的文档格式进行统一，使分散网络资源连接成一个整体。

​    **超文本**——是一种组织信息的方法，通过超级链接将多种媒介关联起来。

​	**标记**——标签。用<>包裹的具有一定含义的内容

​	**特点**——具有简易性、可扩展性、平台无关性、通用性

#### 2.HTML结构

```
<!-- 表声明的意思，意思是下面的文档标签将以html5规范进行解析 -->
<!DOCTYPE html>
<html>
    <!-- 头部，主要用来完成一个网页的相关设置 -->    
	<head>
        <meta charset="utf-8" /> <!-- 汉字编码 -->
        <meta name="keywords" content="设置一个网站的搜索关键字" />
        <meta name="description" content="设置网站的描述内容" />
        <title>网页标题</title>
        <link rel="shortcut icon" href="链接favicon.ico" /> <!--网站icon-->
        <style>内部样式</style>
    </head>
 <!-- 主体部分 -->
    <tbody></tbody>
    <!-- 脚本代码部分 -->
    <script></script>
</html>
```

#### 3.meta标签

```
<meta charset="utf-8" /> <!-- 汉字编码 -->
<meta name="keywords" content="设置一个网站的搜索关键字" />
<meta name="description" content="设置网站的描述内容" />
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
<!--整屏显示禁止缩放-->
<meta content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no, viewport-fit=cover" name="viewport">
<!--添加到主屏后的标题（IOS）-->
<meta name="apple-mobile-web-app-title" content="WeBounty">
<!--启用全屏模式（IOS）-->
<meta name="apple-mobile-web-app-capable" content="yes" />
<meta name="apple-touch-fullscreen" content="yes" />
<!--禁止手机号码识别（IOS）-->
<meta name="format-detection" content="telephone=no" />
<!--禁止电子邮箱识别（Android）-->
<meta name="format-detection" content="email=no" />
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<!--百度禁止转码-->
<meta http-equiv="Cache-Control" content="no-siteapp" />
```

#### 4.实体转义

| 实体字符   | 编译后字符       |
| ---------- | ---------------- |
| `&lt;`     | 小于号（<）      |
| `&gt;`     | 大于号（>）      |
| `&amp;`    | 与号（&）        |
| `&nbsp;`   | 空格             |
| `&copy;`   | 版权（&copy;）   |
| `&times;`  | 乘号（&times;）  |
| `&divide;` | 除号（&divide;） |

#### 5.块元素

​	标签：address、div、dl、dt、dd、form、h1~h6、p、table、ul等

​	特点：

1. 独占一行
2. 宽度和高度是可控的，如果没有设置其宽度，将默认铺满整行
3. 其内可以包含块级和行级元素

#### 6.行内元素

   标签：a、b、span、strong、i、img(行内块元素)、input、textarea、em、label、select等

   特点：（相当于执行了display:inline;操作）

1. 不会独占一行，与相邻的行级元素占同一行，直到行占满，会自动掉到下一行
2. 宽度和高度不可控
3. 其内只有包含行内元素

## W3C标准

#### 1.组成

​    w3c标准由结构、表现和行为三部分组成。

#### 2.标签嵌套规则

1. 块元素可以包含内联元素或某些块元素，但内联元素不能包含块元素，只能包含其它的内联元素
2. 块元素不能放在<p>标签中
3. h1~h6、p、dt 这几个元素只能包含内联元素，不能再包含块元素
4. 块元素与块级元素并列、内联元素与内联元素并列

#### 3.文件命名规范

  文件和目录名一般以字母或下划线_开头

## 浏览器

#### 1.主流浏览器

IE(Edge)、FireFox、Chrome、Opera、Safari

#### 2.内核

浏览器内核由渲染引擎和JS引擎两部分组成

Trident(IE)、Gecko(FireFox)、Webkit(Safari/Chrome)、Blink(Chrome/Opera)

国内大多数浏览器采用的是双核驱动(Trident&Webkit或Trident&Blink)

移动端：iphone/ipad采用的是webkit内核，android4.4以下版本才用的是webkit内核，而4.4以上版本采用的是Blink内核

## 标签

标签由标签名、标签属性和文本内容三部分组成(注意：单标签没有文本内容)

标签属性是对标签的一种描述方式

标签属性分通用属性、自有属性、自定义属性

#### 1.通用属性

所有标签都具有的属性，包括id 、class、style、title

#### 2.自定义属性

通常用来传值或用于图片懒加载等方面

格式：data-*

#### 3.table表格标签

table主要用于呈现格式化数据。表格是由行和列组成。

完整表格组成：caption(标题)、thead(表头)、tbody(表体)、tfoot(表尾)

	/*
		border: 设置表格边框，默认单位是像素
		width: 设置表格宽度，默认单位是像素
		align: 设置表格对齐 (left(默认)/ center/ right)
		cellpadding: 设置单元格文本与边框的距离
		cellspacing: 设置单元格边框间距
	*/
	<table border="1" width="500" align="center" cellpadding="0" cellspacing="0">
		<caption>标题</caption>
		<thead>
			<tr>
	            <th></th> <!-- 表头 文本会自动加粗且居中 -->
	            <th></th>
	            <th></th>
	        </tr>
		</thead>
		<tbody>
			<tr> /*行*/
	            /*td 列 
	                valign 垂直对齐(top/middle/bottom) 
	                align 水平对齐(left/center/right)
	                rowspan 合并行
	                colspan 合并列
	            */
	            <td rowspan="2" align="center" valign="middle"></td> 
	            <td></td>
	            <td></td>
	        </tr>
		</tbody>
	    <tfoot>
	        <tr> /*行*/
	            <td colspan="3" align="center" valign="middle">表尾</td> 
	        </tr>
	    </tfoot>
	</table>

#### 4.form表单标签

是所有标签最核心标签之一。它是用来实现前后端交互的一个重要标签。

##### 4.1常用属性

​	name: 	表单名称

​	action:	表单数据提交的地方(通常是一个后台文件名(.jsp/.php/.asp/.py/.aspy等，或网址))。

​					如果是#，表示提交到当前文件下。

​	method: 	前端提交数据到后端的方法。

​						主要有：get和post。默认是get

##### 4.2表单元素

1. input类:输入

   type: text/password/radio/checkbox/file/button/image/submit/reset

   - text:
     - 单行文本输入框 type="text"可以不写，默认值
     - 属性：placeholder(提示)/ name(命名)/minlength和maxlength(最少/多输入的字符个数)/disabled(失效)/value(默认值)/pattern(正则匹配)
   - password:密码框 属性和text一样
   - radio：单选钮，通常是两项以上。
     - 属性：name/value/checked(选中)/disabled(失效)/readonly(只读)
   - checkbox: 复选框，可以选择0项或多项
     - 属性：name/value/checked(选中)/disabled(失效)/readonly(只读)
   - file: 文件上传按钮
   - button: 普通按钮，通常用来调用脚本代码。
   - image: 图片按钮，用法和button一样。
     - 特殊属性：src(用来加载提示图片，用它替换了value)
     - 也有提交功能，与submit功能一样
   - submit: 提交按钮，用来将表单数据提交到后台
     - 属性：value(按钮的标题)/disabled(失效)
   - reset: 重置按钮，将表单所有组件输入的内容全部清空，还原为初始状态
     - 属性：value(按钮的标题)/disabled(失效)

2. textarea类

   文本域（也可以叫多行文本框），主要用于输入大批量的内容

   属性：name/id/cols(列数)/rows(行数)/placeholder/minlength/maxlength/required/value

3. select类

   下拉列表框，默认用于单项选择。用option呈现每个选项

   属性：multiple(多选)/size(最多显示的行数)

4. button类

   普通按钮，具有提交功能。可以单独使用，不写在form元素中;如果写在form中，有提交功能


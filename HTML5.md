HTML5由W3C和WHAT组织机构共同研发出来的，于2014年正式发布。

HTML5成为了新一代网页开发标准。

#### 1.新特性

1. ##### 增加了音频播放

   1. audio

      播放音乐或音频。IE9以下的版本不支持。

      支持的格式：.mp3/.ogg/.wav

      属性：

      ​	src: 文件路径

      ​	autoplay: 自动播放

      ​	loop: 循环

      ​	controls: 控制条

      ​	muted: 静音

      ​	preload: 预加载（当时用autoplay时，preload自动失效）	

   2. video

      加载视频。IE9以下的版本不支持。

      支持的格式：.mp4/.ogg/.webm

      属性：

      ​	src: 文件路径

      ​	autoplay: 自动播放

      ​	loop: 循环

      ​	controls: 控制条

      ​	muted: 静音

      ​	preload: 预加载（当时用autoplay时，preload自动失效）

      ​	width: 宽度

      ​	height: 高度

      ​	poster: 视频播放前的海报

   3. embed

      嵌入内容或加载插件。

      属性：

      ​	src: 文件路径

      ​	width: 宽度

      ​	height: 高度

      ​	type：类型

      ```
      <embed src="movie.ogg" type="video/ogg" />
      ```

2. ##### 新增了canvas画布（绘画，制作动画（如小游戏开发等））

   是一个容器元素。

   ```
   <canvas id="canvas" width="300" height="200" style="background-color: #ff0;"></canvas>
   /* 用来包裹脚本代码 */
   <script>
   	var canvas = document.getElementById('canvas'); // DOM操作 获取canvas
   	var ctx = canvas.getContext('2d'); // 绘制2D图
   	ctx.fillStyle = '#ff0'; // 设置填充色
   	ctx.fillRect(50, 70, 200, 100); // 绘制矩形 (x坐标, y坐标, width, height)
   </script>
   ```

   注意：

   	1. 单独使用canvas没有意义，它必须结合javascript使用。它的具体功能是通过javascript体现的。
    	2. canvas的宽高最好不要通过css实现，而是直接使用标签属性width和height实现。

3. ##### 地理定位

4. ##### 增加了离线缓存

5. ##### 硬件加速

6. ##### Web Socket（全双工通信）

7. ##### 增加了本地存储

8. ##### 新增了一些语义化标签

   1) mark: 高亮显示(行级标签)

   2) details(描述)与summary(摘要): 一般用于名词解释或用于封装一个区块

   ```
   <details>
   	<summary>前端开发</summary>
   	<ul>
   		<li>组件化开发</li>
   		<li>模块化开发</li>
   	</ul>
   </details>
   ```

   3) meter: 定义度量衡

   ​	属性：value(当前值)、min(最小值)、max(最大值)

   ```
   <meter vlaue="110" min="80" max="120"></meter>公里/小时
   ```

   4) progress: 进度条

   ​	属性：value/max/min

   ```
   任务已完成：<progress vlaue="70" min="0" max="100"></progress> 70%
   ```

   5) dialog: 对话框或窗口(弹窗，居中展示)

   6) figure: 用于对元素进行组合（一般用来组合一张图的标题、图片和图片的描述）

#### 2.网页布局标签

​	header: 页首

​	nav: 导航栏

​	aside: 侧边栏

​	main: 主体

​	section: 区块

​	article: 文章

​	footer: 页尾

#### 3.常用属性

1. contentEditable

   将标签转换为可编辑状态。可用于所有标签。值：true/false

   ```
   <p contentEditable="true">contentEditable</p>
   ```

2. hidden

   对元素进行隐藏。一般用来传值或当某个条件成立，执行内容显示。默认值为hidden。

3. data-*

   用于存储页面或应用程序的私有自定义数据。一般用于传值。

4. multiple

   规定输入域中可选择多个内容。用于表单组件中，如file/select。

5. required

   约束表单元互在提交前必须输入值。用于表单组件中，需要结合提交按钮使用。form

6. pattern

   用于验证输入字段的模式。用于表单组件中，需要结合提交按钮使用。

   ```
   <form>
   	<input type="text" pattern="[A-Za-z]{4,6}" /> /* 正则验证 */
   </form>
   ```

#### 4.表单组件

1. color: 颜色
2. email: 邮箱
3. tel: 电话号码
4. url: 网址
5. number: 数字
6. range: 范围
7. search: 搜索
8. date: 日期
9. datetime: 日期时间
10. datetime-local: 本 - 日期时间
11. year: 年份
12. month: 月份
13. time: 时间
14. week: 周

#### 5.表单属性

1. formaction: 修改action数据提交的地方

   ```
   <form action="#">
   	<input type="submit" formaction="https://baidu.com" />
   </form>
   ```

2. formenctype: 修改表单请求类型

3. formmethod: 修改数据提交方法(get/ post)

   1. get是以字节为单位提交，只接受ASCII，而post是以字符为单位提交
   2. get是明文方式，提交的数据会显示在地址栏中，一般不用来传输一些敏感数据，因为传输的数据暴露在外面，而post是密文方式提交的。
   3. get在连蓝其中回退是无害的，而post会再次提交
   4. get会被浏览器主动缓存，而post不会，除非手动设置
   5. get和post在传输字节数上一般没有限制，个别浏览器会有，可以理解为get一般不超过2k，而post一般不超过2M

4. form: 设置表单元素属于哪个表单

   ```
   <form id="user-info">
   	<input type="submit" />
   </form>
   <input type="password" name="userpwd" form="user-info" />
   ```

5. novalidate: 不验证

#### 6.input属性

1. autocomplete:  自动完成

   值：on/off，默认on

   用来帮助用户输入，每次输入的内容，浏览器是否保存输入的值，以备将来使用。

   为了保护敏感数据（如用户账号、密码等），避免本地浏览器对他们不安全存储，一般需要关闭。

2. autofocus: 自动获取焦点

3. step: 步长

4. mutiple: 多选

5. pattern: 正则匹配

6. placeholder: 输入提示

7. required: 必须输入
# HTML

<P>
<a href="https://www.runoob.com/html/html-quicklist.html">速查列表</a></P>

HTML 是用来描述网页的一种语言。

- meta标签提供元数据，不会显示在页面上，描述网页
- font-family（字体）
- color（颜色）
- font-size（字体大小）
-  text-align（文字对齐）

- <h1 style="text-align:center;">居中对齐的标题</h1>
  <p>这是一个段落。</p>

##### 图像

```html
<img src="pulpit.jpg" alt="Pulpit rock" width="304" height="228">
```

alt:当图片无法显示时，才会显示信息来代替

##### 表格

1. table定义表格，tr定义行，td定义表格数据，th定义表头
2. colspan跨列，rowspan跨行，cellpadding单元格边距，cellspacing单元格间距

##### 列表

无序列表：ul,ol

有序列表：ol，li

自定义列表：dl，dt

##### 表单

 1.form，input

<form>
First name: <input type="text" name="firstname"><br>
Last name: <input type="text" name="lastname">
</form>

2.type：password（密码），radio 单选框，checkbox复选框，button按钮，submit提交

<form name="input" action="html_form_action.php" method="get">
Username: <input type="text" name="user">
<input type="submit" value="Submit">
</form>

##### iframe

<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<p><a href="https://www.runoob.com" target="iframe_a">RUNOOB.COM</a></p>

inframe可以在一个设定的框内显示一个页面



# CSS

1. ### 选择器

   ①id选择器，以#来定义

   <style>
   #para1
   {
   	text-align:center;
   	color:red;
   } 
   </style>
   <p id="para1">Hello World!</p>

   ②class选择器

   ```html
   <style>
   p.ex
   {
       text-align:center;
   }
   </style>
   <p class="ex">这个段落居中对齐。</p> 
   ```

   

   

   

2. ### 插入样式表

   ①外部样式表：通过一个文件改变外观

   <head> <link rel="stylesheet" type="text/css" href="mystyle.css"> </head>

​		②内部样式表：单个文档需要特殊样式，可以在			<style> 标签在文档头部定义内部样式表

<head> 
<style> hr {color:sienna;} p {margin-left:20px;} body {background-image:url("images/back40.gif");} 
</style>
</head>

3. # 定位

- static：没有定位
- relative：相对定位元素的定位是相对其正常位置。
- fixed:相对于浏览器窗口是固定位置
- absolute：绝对定位的元素的位置相对于最近的已定位父元素
- sticky:无论鼠标滚动到哪，它都会出现在固定的目标定位

4. ## 重叠的元素

   z-index属性指定了一个元素的堆叠顺序

5. # anchor伪类

   ```
   a:link {color:#FF0000;} /* 未访问的链接 */
   a:visited {color:#00FF00;} /* 已访问的链接 */
   a:hover {color:#FF00FF;} /* 鼠标划过链接 */
   a:active {color:#0000FF;} /* 已选中的链接 */
   ```

   
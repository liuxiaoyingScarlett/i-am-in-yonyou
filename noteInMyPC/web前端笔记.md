# web前端笔记

## 标签
+ pre:被包围在pre标签中的文本通常会保留空格和换行符
+ sup:定义上标文本
+ sub:定义下标文本
+ fieldset:元素集，将表单信息分组，通常与legend标签（表示提示信息）一起用

+ 行内元素尽量不要包含块级元素？后果？

## 布局方式
### 1.frameset布局

a.多个frame组成frameset

+ frameset的属性：

		cols=""--->按列划分

		rows=""--->按行划分

+ frame的属性：

		name框架名称，设置target时使用
		
		src！必须！设置此框架要显示的网页路径

		scrolling是否显示滚动条

> 注：有frame无body,有body无frame

b.内联框架iframe

属性：宽，高，名称，路径

> iframe是body的子级，而frameset是body的同级且只能有一个



## 表格

+ 表格的标题caption居于表格之上
+ 常见实体字符： &lt, &gt, &quot, &laquo, &raquo  
	[实体字符对照表](http://tool.xker.com/htmlchar.php)

## H5

### 1.常见H5新增标签

+ header页面头部
+ footer页脚
+ artical 页面独立的内容区域
+ aside页面的侧边栏
+ details文档某部分的细节
+ summary是detail的标题
+ time定义日期或时间
+ ruby：rp标签定义不支持ruby标签的浏览器所显示的标签，rt定义注释拼音
+ mark标记
+ nav导航链接

+ progress进度标签
+ section文档中的节或文章
+ video视频
+ audio音频
+ source资源，用于定义多媒体资源视频和音频，一个媒体下可定义多个资源，一个不能打开可以打开另一个
+ datalist提示可能的值，input的list属性绑定datalist,datalist中的option中的值单独写不会显示，最好写在value属性中
+ embed引入flash或插件
+ canvas画布



## CSS

#### 

背景图片是否重复：  
background-repeat:repeat / repeat-x / repeat-y / no-repeat

背景图片是否随内容滚动：  
background-attachment:  scroll / fixed / 

透明度：（1为不透明，0为透明）  
opacity属性会被子元素继承，，一般使用rgba()来实现相同效果

以下3个同时使用才有效果：
white-space:nowrap--->不自动换行  
overflow:hidden--->多出内容隐藏  
text-overflow:ellipsis--->超出的文本以省略号显示

### 选择器

+ 关系选择器

	后代选择器：E F  
	子选择器：E > F  
	相邻选择器：E + F  
	兄弟选择器：E ~ F 

+ 属性选择器

	E[attr]--->有attr属性的E元素  
	E[attr="val"]--->attr属性等于val的E元素 
	E[attr^="val"]--->attr属性以val开头的E元素
	E[attr$="val"]--->attr属性以val结束的E元素  
	E[attr~="val"]--->attr属性列表中有val的E元素  
	E[attr*="val"]--->attr属性中有val字符串的E元素

+ 伪类选择器**(重点)**  
	伪类选择器通过*冒号*来定义，定义了元素的状态，如点击按下，点击完等，

	E:link--->仅限于a标签，未被访问前的样式  
	E:visited--->仅限于a标签，已被访问后的样式  
	E:hover--->鼠标悬停时的样式  
	E:active--->不限于a标签，鼠标按下时的样式   
	E:not(selector)--->不含有s选择器的元素E(注：not中的值不加引号)
	E:first-child--->父元素的第一个子元素E  
	E:last-child--->父元素的最后一个子元素E  
	E：only-child--->E元素是父元素的唯一的子元素
	E:empty--->？
	E:checked--->被选中的E元素  
	E:nth-child(n)--->父元素的第n个E子元素

+ 伪对象选择器**(重点)**  
	伪类反应无法再CSS中获取到的某个元素的状态或者属性，而伪元素表示DOM外部的某种文档结构  
	常用伪元素：(与content一起使用，表示插入的内容)   
	**1.E:before/E::before;**  
	**2.E:after/E::after;**  
	在被选择元素内部的最前或最后插入伪元素

### 浮动  
+ position定位：  
	static:默认值，遵循正常文档流  
	relative:对象遵循正常文档流  
	absolute:对象脱离文档流，使用top,left,bottom,right定位  
	fixed:对象脱离文档流，使用top,left,bottom,right定位，当出现滚动条时，对象不会随着滚动
	（绝对定位默认相对于浏览器，一般将其父元素设置为relative）
> 注：脱离文档流的元素不添加宽高属性无法显示！行元素加了position:absolute后可设置宽和高（加了float或fixed后同理）  
> 注：z-index仅在定位元素上(relative,absolute,fixed)有效！ 
	
	display:table-cell&veritical:middle可以使内部内容居中
	padding不允许设置为负值，会被强制为0 
+ margin外边距  
	1.块级元素的垂直相邻外边距会合并，合并原则：以大为准  
	2.行内元素实际上不占用上下外边距，左右不合并  
	3.浮动元素的外边距也不会合并  
	4.允许指定负的外边距值，不过使用时要小心  

+ 伸缩盒模型(弹性盒模型)  
	父元素设置为display:flex;子元素各项目设置flex-grow:比例值
+ css中可被继承的属性  
	color,cursor,font-family,font-size,font-style,font-weight,font,letter-spacing,line-height,list-style,text-align,text-indet  
	border,padding,margin不能继承！  
+ CSS3  
	过渡transition--->css的属性值在一定的时间区间内平滑地过渡
	transition:属性名 时间 速度曲线 何时开始（时间不可省略）
	transform:对元素进行旋转，缩放，移动或倾斜
		二维旋转：transform:rotate(30deg)正值顺时针，负值逆时针
> 注：transform必须与transition结合使用，不然有些起始和结束状态相同的情况下看不到效果  
三维旋转:rotateX();rotateY();translate3d(x,y,z)-->元素的位移  

+ CSS3动画animation  
	@keyframes规则 用于创建动画 如下：  
			@keyframes myfirst {
				0% {width:200px;}
				25% {width:400px;}
				50% {width:300px;}
				100% {width:600px;}
			} 
	animation调用动画  

+ 设置resize必须要设置overflow属性，且不能为visible(默认值),一般设为auto
	box-sizing用于设置标准盒模型(content-box)和怪异盒模型(border-box)的转换。  

+ 响应式布局  ？？？？


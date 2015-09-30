* transition(过渡)主要包含四个属性值：_（Internet Explorer 9 以及更早的版本，不支持 transition 属性）_
	- 执行变换的属性：transition-property :

		none(没有属性改变)；all（所有属性改变）这个也是其默认值；indet（元素属性名）
	
	- 变换延续的时间：transition-duration:
		
		默认值为0
	
	- 在延续时间段，变换的速率变化transition-timing-function  
		
		ease：（逐渐变慢）默认值

		linear：（匀速）

		ease-in：(加速)

		ease-out：（减速）

		ease-in-out：（加速然后减速）

		cubic-bezier：（该值允许你去自定义一个时间曲线）， 特定的cubic-bezier曲线。 (x1, y1, x2, y2)四个值特定于曲线上点P1和点P2。所有值需在[0, 1]区域内，否则无效。

	- 变换延迟时间transition-delay
		
		ransition-delay是用来指定当改变元素属性值后多长时间开始执行transition效果


* cursor属性：规定要显示的光标的类型（形状）。

* (**2D**转换)
	
	+ Transform（变形）：		
	
		- 旋转rotate(<angle>) 

		- 扭曲skew(<angle>):skew(x,y)/skewX(x)/skewX(x)

		- 缩放scale(<number>):scale(x,y)/scaleX(x)/scaleY(y)

		- 移动translate(<number>)：translate(x,y)/translateX/translateY

		- 矩阵变形matrix

	+ transform-origin(X,Y):用来设置元素的运动的基点（参照点）

		- 值：
			+ X:left,center,right;
			+ Y:top,center,bottom。
			+ X和Y的值可以是百分值,em,px。


* ( **伪元素** )：

	- :before : 在元素之前添加内容。
	- :after : 在元素之后添加内容。
	- :first-line : 向文本的首行添加特殊样式。
	- :first-letter : 向文本的第一个字母添加特殊样式。

* ( **伪类** )：hover 选择器：:用于选择鼠标指针浮动在上面的元素。
	
	提示：
	
	:link 选择器设置指向未被访问页面的链接的样式，
	
	:visited 选择器用于设置指向已被访问的页面的链接，
	
	:active 选择器用于活动链接。

	注释：在 CSS 定义中，:hover 必须位于 :link 和 :visited 之后（如果存在的话），这样样式才能生效。


* ( **伪类** ):lang	向带有指定 lang 属性的元素添加样式。

* ( **伪类** ):focus	向拥有键盘输入焦点的元素添加样式。

* ( **伪类** ):first-child 选择器用于选取属于其父元素的首个子元素的指定选择器。

	选择列表中的第一个 < li > 元素并设置其样式：
	<!--python-->	
		li:first-child
		{

			background:yellow;
		}

* :nth-child(__n__) 选择器 : 匹配属于其父元素的第 N 个子元素，_不论元素的类型_。n 可以是数字、关键词或公式。
		
	规定属于其父元素的第二个子元素的每个 p 的背景色：
	<!--python--> 
		p:nth-child(2)
		{
			background:#ff0000;
		}

* :nth-of-type(__n__) 选择器匹配属于父元素的_特定类型_的第 N 个子元素的每个元素。n 可以是数字、关键词或公式。

	规定属于其父元素的第二个 p 元素的每个 p：
	<!--python--> 
		p:nth-of-type(2)
		{
			background:#ff0000;
		}

*  border-collapse:collapse:表格设置合并边框模型.

*  border-spacing：设置相邻单元格的边框间的距离（仅用于“边框分离”模式）。

	table
  		{
  		border-collapse:separate;
  		border-spacing:10px 50px;
  		}

* HTML <td> 标签的 rowspan 属性:规定单元格可横跨的行数。

	rowspan="0" 指示浏览器横跨到表格部分的最后一行（thead、tbody 或者 tfoot）。

* HTML <td> 标签的 colspan 属性:规定单元格可横跨的列数。

	colspan="0" 指示浏览器横跨到列组的最后一列。


* HTML < td > 标签的 scope 属性:

	+ 值有：col, row, colgroup, rowgroup

	+ 定义将表头单元与数据单元相关联的方法。

	+ 标识某个单元是否是列、行、列组或行组的表头。

	+ 不会在普通浏览器中产生任何视觉变化。

	+ 屏幕阅读器可以利用该属性。
	
* <span> 标签被用来组合文档中的行内元素。
	
	span 没有固定的格式表现。当对它应用样式时，它才会产生视觉上的

	变化。
	
	可以为 span 应用 id 或 class 属性，这样既可以增加适当的语义，又便于
	
	对 span 应用样式。

* 相邻兄弟选择器（Adjacent sibling selector）可选择紧接在另一元素后的元素，且二者有相同父元素。

	- 相邻兄弟选择器使用了加号（+），即相邻兄弟结合符（Adjacent sibling combinator）。

	- 例如，如果要增加紧接在 h1 元素后出现的段落的上边距，可以这样写：

		<!--python-->	
		
			h1 + p {
				margin-top:50px;
			}

	这个选择器读作：“选择紧接在 h1 元素后出现的段落，h1 和 p 元素拥有共同的父元素”。

* able-layout 属性: 用来显示表格单元格、行、列的算法规则。

	- 值：
		
	 + automatic	默认。列宽度由单元格内容设定。	 
	 + fixed	列宽由表格宽度和列宽度设定。
	 + inherit	规定应该从父元素继承 table-layout 属性的值。__任何的版本的 Internet Explorer （包括 IE8）都不支持属性值 "inherit"__
	 

* !important 语法:覆盖原本的权重。

* 所有的 inline 元素都没有 width 和 height。
  
    可以设置 display: block; 把 inline 元素当作 block 元素来处理，再设置 width 和 height。

* 背景：background:#FFF url(http://www.divcss5.com/img201301/divcss5-logo-2013.gif) no-repeat 10px 5px fixed

	10px:左边距是10px;  

	5px:右边距是5px

	background-color 背景颜色

	background-image 背景图片:url(图片地址路径) 

	background-repeat 背景重复：no-repeat; repeat-x; repeat-y

	background-attachment 背景图片是固定(fixed)还是滚动(scroll)

	background-position 背景图片的定位 : 默认值 0% 0% 第一个值是水平位置，第二个值是垂直位置。
	center,top/center/bottom left/center/right

* HTML <img> 标签的 alt 属性: 它规定在图像无法显示时的替代文本。

	alt 文本的使用原则：	
	1. 如果图像包含信息 - 使用 alt 描述图像
	2. 如果图像在 a 元素中 - 使用 alt 描述目标链接
	3. 如果图像仅供装饰 - 使用 alt=""

* HTML < input > list 属性: list 属性引用数据列表，其中包含输入字段的预定义选项。

	语法 < input list="value"> 
	
	值为文档中的 datalist 的 id。

* HTML < option> 标签： option 元素定义下拉列表中的一个选项（一个条目）。

	浏览器将 < option> 标签中的内容作为 < select> 标签的菜单或是滚动列表中的一个元素显示。
	
	option 元素位于 select 元素内部。

	- 可选的属性：
		+ disabled：规定此选项应在首次加载时被禁用。
		+ label：定义当使用 <optgroup> 时所使用的标注。
		+ selected：规定选项（在首次显示在列表中时）表现为选中状态。
		+  value：定义送往服务器的选项值。

* [HTML 事件属性](http://www.w3school.com.cn/tags/html_ref_eventattributes.asp "HTML 事件属性")

* HTML < br> 标签 : 会告诉浏览器立即停止当前的文本流，并在下一行的左边，或者在左对齐的内联图形或表格的右边开始继续输出文本流。
	
	+ 但是有时候，您也许希望当前的文本流在当前左边或右边的**内联表格**或**图像**的下面一行继续输出。
	
		- HTML 4 和 XHTML 通过 < br> 标签的 **clear** 属性标签提供了这样的功能。
	
		- 它具有三个值：left、right 或者 all，每个值都代表一个边界或两边的边界。
	
		- 当指定的边界没有图像时，浏览器才会继续输出文本。
		
		- < br> 标签的 clear 属性只对这些左对齐或右对齐的图像或表格起作用。 

* CSS clip 属性： 剪裁**绝对定位**元素。

		值：
		- shape	设置元素的形状。唯一合法的形状值是：rect (top, right, bottom, left)
		- auto	默认值。不应用任何剪裁。
		- inherit	规定应该从父元素继承 clip 属性的值。


* CSS3 border-image 属性:可以使用图片来创建边框。

	border-image 属性是一个简写属性，用于设置以下属性：
	- border-image-source 用在边框的图片的路径。
	- border-image-slice 图片边框向内偏移。
	- border-image-width 图片边框的宽度。
	- border-image-outset 边框图像区域超出边框的量。
	- border-image-repeat  图像边框是否应平铺(repeated)、铺满(rounded)或拉伸(stretched)。

	语法：
	<!--o-->
		border-image:url(border.png) 30 30 round;
		-moz-border-image:url(border.png) 30 30 round; /* 老的 Firefox */
		-webkit-border-image:url(border.png) 30 30 round; /* Safari 和 Chrome */
		-o-border-image:url(border.png) 30 30 round; /* Opera */

* CSS3 background-origin 属性：规定背景图片的定位区域。

	背景图片可以放置于 content-box、padding-box 或 border-box 区域。

* CSS3 background-clip 属性： 规定背景的绘制区域。

	背景可被裁剪到(border-box)边框盒,(padding-box)内边距框,(content-box)内容框。

* CSS3 文本阴影 text-shadow :可向文本应用阴影。

	能够规定水平阴影、垂直阴影、模糊距离，以及阴影的颜色。

* CSS3 @font-face 规则：

	1. 在新的 @font-face 规则中，您必须首先定义字体的名称（比如 myFirstFont），然后指向该字体文件。
			
		如需为 HTML 元素使用字体，请通过 font-family 属性来引用字体的名称 (myFirstFont)：

	<!--html-->
		<style> 
		@font-face
		{
		font-family: myFirstFont;
		src: url('Sansation_Light.ttf'),
     		 url('Sansation_Light.eot'); /* IE9+ */
		}

		div
		{
		font-family:myFirstFont;
		}
		</style>

	2. 若使用粗体字体，必须另外定义一个粗体文本添加描述符（font-weight:bold）的 @font-face：
		
	<!--html-->
		@font-face
		{
		font-family: myFirstFont;
		src: url('Sansation_Bold.ttf'),
     		 url('Sansation_Bold.eot'); /* IE9+ */
		font-weight:bold;
		}

* @keyframes 规则：规定动画。(_Internet Explorer 9，以及更早的版本，不支持 @keyframe 规则或 animation 属性。_)

	当您在 @keyframes 中创建动画时，请把它捆绑到某个选择器，否则不会产生动画效果。

	通过规定至少以下两项 CSS3 动画属性，即可将动画绑定到选择器：

	- 规定动画的名称
	- 规定动画的时长

 	animation 所有动画属性的简写属性，除了 animation-play-state 属性。
	其他属性点击[这里](http://www.w3school.com.cn/css3/css3_animation.asp "CSS3 动画")查看。
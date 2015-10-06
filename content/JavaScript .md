* JavaScript 对大小写敏感。

* 注释：

	- 单行：以 // 开头
	- 多行：以/*开始，以*/结尾

* JavaScript 中的所有事物都是对象：字符串、数字、数组、日期，等等。

	在 JavaScript 中，对象是拥有属性和方法的数据（变量）。 
	
	- 属性是与对象相关的值。
	- 方法是能够在对象上执行的动作。

* JavaScript 函数： return语句

	- 通过使用 return 语句实现函数停止执行，并返回指定的值。（带有返回值的函数）
	- 在仅仅希望退出函数时 ，也可使用 return 语句。返回值是可选的。

* 如果您把值赋给**尚未声明**的变量，该变量将被自动作为**全局变量**声明，即使它在函数内执行。

* 运算符 + 用于加值。
 
	- JavaScript 算术运算符：用于执行变量与/或值之间的加法运算。
	- 用于字符串的 + 运算符：用于把文本值或字符串变量加起来（连接起来）。
	- 用于字符串和数字进行加法运算：如果把数字与字符串相加，结果将成为**字符串**。

* 逻辑运算符
	
	- &&：and
	- ||：or
	- ! ：not

* 条件运算符

	- JavaScript 还包含了基于某些条件对变量进行赋值的条件运算符。
	- 语法：variablename=(condition)?value1:value2
		+ condition值为true,则variablename=value1
		+ condition值为false,则variablename=value2

* switch函数

	<!--javascript--> 
		switch(n)
		{
		case 1:
 	 		执行代码块 1
  			break;
		case 2:
  			执行代码块 2
  			break;
		default:
  			n 与 case 1 和 case 2 都不同时执行的代码
		}
	
	工作原理：
	- 首先设置表达式 n（通常是一个变量）。
	- 随后表达式的值会与结构中的每个 case 的值做比较。
	- 如果存在匹配，则与该 case 关联的代码块会被执行。使用 break 来阻止代码自动地向下一个 case 运行。
	-  default 关键词来规定匹配不存在时做的事情。
	
* For 循环：

		for (语句 1; 语句 2; 语句 3)
  		{
  			被执行的代码块
  		}
	
	语句 1 在循环（代码块）开始前执行（可选）--for (; 语句 2; 语句 3)
	
	语句 2 定义运行循环（代码块）的条件（可选）--for (语句 1;; 语句 3)
	
	语句 3 在循环（代码块）已被执行之后执行 （可选）--for (语句 1;语句 2; )

* For/In 循环：遍历对象的属性。

	var person={fname:"John",lname:"Doe",age:25};

	for (x in person)

* JavaScript 标签

	标记 JavaScript 语句，需在语句之前加上冒号： label:语句

	break 和 continue 语句仅仅是能够跳出代码块的语句。

	语法:

	- break labelname;

	- continue labelname;

---
	1. continue 语句（带有或不带标签引用）只能用在循环中。

	2. break 语句（不带标签引用），只能用在循环或 switch 中。

	3. 通过标签引用，break 语句可用于跳出任何 JavaScript 代码块：

---


* Throw 语句 : 允许我们创建自定义错误。具体点击[JavaScript 错误](http://www.w3school.com.cn/js/js_errors.asp)

----

* ( ) 是一个分组操作符，它的内部只能包含表达式！

* 暂时看不懂！！！！！[深入理解JavaScript系列（2）：揭秘命名函数表达式--汤姆大叔](http://www.cnblogs.com/TomXu/archive/2011/12/29/2290308.html )
	



---
#### JavaScript Timing

* HTML DOM setTimeout() 方法：
	
	- setTimeout() 方法用于在指定的毫秒数(millisec)后调用函数或计算表达式(code)。
	
	- 语法：setTimeout(code,millisec)

* HTML DOM clearTimeout() 方法：

	- clearTimeout() 方法可取消由 setTimeout() 方法设置的 timeout。

	- 语法：clearTimeout(id_of_settimeout)
	
		+ id_of_settimeout：由 setTimeout() 返回的 ID 值。该值标识要取消的延迟执行代码块。

---
#### JavaScript 消息框

* HTML DOM alert() 方法（警告框）：
	
	- alert() 方法用于显示带有一条指定消息和一个 OK 按钮的警告框。
	
	- 语法：alert(message)
		
		+ message	要在 window 上弹出的对话框中显示的纯文本（而非 HTML 文本）

* HTML DOM prompt() 方法（提示框）：
	
	- prompt() 方法用于显示可提示用户进行输入的对话框。
	
	- 语法：prompt(text,defaultText)

		+ text：可选。要在对话框中显示的纯文本（而不是 HTML 格式的文本）。
		
		+ defaultText：可选。默认的输入文本。 
		
		+ 如果用户单击提示框的取消按钮，则返回 null。如果用户单击确认按钮，则返回输入字段当前显示的文本。

* HTML DOM confirm() 方法（确认框 ）：

	- confirm() 方法用于显示一个带有指定消息 和 OK 及取消按钮的对话框。

	- 语法：confirm(message)
	
		+ message：要在 window 上弹出的对话框中显示的纯文本（而非 HTML 文本）

		+ 如果用户点击确定按钮，则 confirm() 返回 true。如果点击取消按钮，则 confirm() 返回 false。 


* JavaScript RegExp 对象：表示正则表达式，它是对字符串执行模式匹配的强大工具。

	- 直接量语法：/pattern/attributes
	- 创建 RegExp 对象的语法：new RegExp(pattern, attributes);

# JQuery

* 由于 jQuery 是为处理 HTML 事件而特别设计的，那么当您遵循以下原则时，您的代码会更恰当且更易维护：

	- 把所有 jQuery 代码置于事件处理函数中

	- 把所有事件处理函数置于文档就绪事件处理器中 -- $(document).ready(function(){})

	- 把 jQuery 代码置于单独的 .js 文件中

	- 如果存在名称冲突，则重命名 jQuery 库

* jQuery 效果 - toggle() 方法：toggle() 方法切换元素的可见状态。（不适用于 visibility:hidden 的元素）

	- 如果被选元素可见，则隐藏这些元素

	- 如果被选元素隐藏，则显示这些元素。
	

	语法：$(selector).toggle(speed,callback,switch)

	- Callback 函数(参数)：在当前动画 100% 完成之后执行。

	- switch	：可选。布尔值。规定 toggle 是否隐藏或显示所有被选元素。

		+ True - 显示所有元素

		+ False - 隐藏所有元素

		+ 如果设置此参数，则无法使用 speed 和 callback 参数。
		
* jQuery fadeTo() 方法：允许渐变为给定的不透明度（值介于 0 与 1 之间）。

* jQuery animate() 方法：允许您创建自定义的动画。 

	- 语法：$(selector).animate({params},speed,callback);

		+ params 参数定义形成动画的 CSS 属性。

			- 多个参数之间用逗号( , )分隔，各个参数同时执行。

* jQuery stop() 方法：用于停止动画或效果，在它们完成之前。
	
	- 语法：$(selector).stop(stopAll,goToEnd);

		+ 可选的 stopAll 参数规定是否应该清除动画队列。默认是 false，即仅停止活动的动画，允许任何排入队列的动画向后执行。

		+ 可选的 goToEnd 参数规定是否立即完成当前动画。默认是 false。

		+ 默认地，stop() 会清除在被选元素上指定的当前动画。

* JavaScript escape() 函数：可对字符串进行编码，这样就可以在所有的计算机上读取该字符串。

	- 语法：escape(string)
	
	- string（必需）：要被转义或编码的字符串。

	- 返回：已编码的 string 的副本。其中某些字符被替换成了十六进制的转义序列。
	
	- 可以使用 unescape() 对 escape() 编码的字符串进行解码。
	
	- ECMAScript v3 反对使用该方法，应用使用 decodeURI() 和 decodeURIComponent() 替代它。  


* jQuery - AJAX load() 方法：从服务器加载数据，并把返回的数据放入被选元素中。

	- 语法：$(selector).load(URL,data,callback);

		+ URL（必需）：参数规定您希望加载的 URL。

		+ data（可选）： 参数规定与请求一同发送的查询字符串 键/值对集合。

		+ callback（可选）：参数是 load() 方法完成后所执行的回调函数名称。

		+ 回调函数可以设置不同的参数：

			* responseTxt - 包含调用成功时的结果内容

			* statusTXT - 包含调用的状态

			* xhr - 包含 XMLHttpRequest 对象

* JQuery - AJAX get() 和 post() 方法：

	- jQuery $.get() 方法：通过 HTTP GET 请求从服务器上请求数据。

		+ 语法：$.get(URL,callback);

		+  URL 参数（必需）：规定您希望请求的 URL。
		
		+  callback 参数（可选）：是请求成功后所执行的函数名。

	- jQuery $.post() 方法：通过 HTTP POST 请求从服务器上请求数据。

		+ 语法：$.post(URL,data,callback);

		+ URL 参数（必需）：规定您希望请求的 URL。

		+ data 参数（可选）：规定连同请求发送的数据。

		+ callback 参数（可选）：是请求成功后所执行的函数名。

* jQuery - noConflict() 方法：释放会 $ 标识符的控制，这样其他脚本就可以使用它了。

	- jQuery 使用 $ 符号作为 jQuery 的简写。

	- 具体使用方法，[点这里](http://www.w3school.com.cn/jquery/jquery_noconflict.asp "JQuery-noConflict方法") 



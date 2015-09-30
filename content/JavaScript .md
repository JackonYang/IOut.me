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
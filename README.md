# wzyjs
使用<script src=”XXX.js”>调用外部的JavaScript(.js文件)
JavaScript.html文件：
<html>
<body>
<script language="javascript" type="text/javascript" src="JavaScript.js">
	
</script>
</body>
</html>
JavaScript.js文件：
document.write("外部的JavaScript文件");
alert("消息");


把JavaScript代码放到HTML页面不同的位置
页面中的脚本会在页面载入浏览器后立即执行。我们并不总希望这样。有时，我们希望当页面载入时执行脚本，而另外的时候，我们则希望当用户触发事件时才执行脚本。
(1)把JavaScript代码放到HTML<body>部分
把页面载入时就需要执行的JavaScript代码放到<body>标签之间。这是一种规范，建议这样做。
(2)把JavaScript代码放到HTML<head>部分
把当脚本被调用时，或当事件被触发时才会执行的JavaScript代码放到<head>标签之中，这样就可以确保在调用JavaScript之前就载入了它。这是一种规范，建议这样做。
示例代码
<html>
<head>
	<script type="text/javascript">
		function message()
		{
			document.write("head之间的JavaScript！");
		}
	</script>
</head>

<body>
	<script language="javascript" type="text/javascript">
		document.write("body之间的JavaScript！");
	</script>
	<button onclick="message()">head</button><!-- 调用head之间的JavaScript -->
</body>
</html>


关系运算(<、>、<=、>=、==、!=)
<script language="javascript" type="text/javascript">
	var bool = 2<1;
	document.write(bool+"<br>");//输出false
	var bool = "a"<"b";//字母 a的字符代码是 97,字母b的字符代码是 98
	document.write(bool+"<br>");//输出ture
	var bool = "98"<97;//字符串 "98"将被转换成数字 98
	document.write(bool+"<br>");//输出false
	var bool = "a"<9999;//这样比较总是返回false，不管是<、>、<=、>=
	document.write(bool+"<br>");//输出false
</script>


等性运算符(==、===、!=、!==)
全等号由三个等号表示（===），只有在无需类型转换运算数就相等的情况下，才返回 true。
<script language="javascript" type="text/javascript">
	var i = "66";
	var j = 66;
	document.write((i == j)+"<br>");//输出 "true"
	document.write((i === j)+"<br>");//输出 "false"
	document.write((i != j)+"<br>");//输出 "fale"
	document.write((i !== j)+"<br>");//输出 "true"
</script>


赋值运算符
每种主要的算术运算以及其他几个运算都有复合赋值运算符：
乘法/赋值（*=）
除法/赋值（/=）
取模/赋值（%=）
加法/赋值（+=）
减法/赋值（-=）
有符号右移/赋值（>>=）
无符号右移/赋值（>>>=）


Type运算符
typeof 运算符有一个参数，即要检查的变量或值，对变量或值调用 typeof 运算符将返回下列值之一：Undefined：如果变量是 Undefined 类型的；Boolean：如果变量是 Boolean 类型的；Number：如果变量是 Number 类型的；String：如果变量是 String 类型的；Object：如果变量是一种引用类型或 Null 类型的。
<script type="text/javascript">
	var temp1="王子岳";
	var temp2;//Undefined类型只有一个值，即 undefined。当声明的变量未初始化时，该变量的默认值是 undefined。
	document.write((typeof temp1)+"<br>");//string
	document.write((typeof temp2)+"<br>");//undefined
	document.write((typeof 86)+"<br>");//number
	document.write((typeof null)+"<br>");//object
</script>
Undefined：Undefined类型只有一个值，即 undefined。当声明的变量未初始化时，该变量的默认值是 undefined。
null：另一种只有一个值的类型是 Null，它只有一个专用值 null，即它的字面量。值 undefined 实际上是从值 null 派生来的，因此 ECMAScript 把它们定义为相等的。alert(null == undefined); //输出 "true"。


delete运算符
delete 运算符删除对以前定义的对象属性或方法的引用。例如：
<script type="text/javascript">
	var o = new Object;
	o.name = "王子岳";
	document.write(o.name+"<br>");	//输出 "王子岳"
	delete o.name;
	document.write(o.name+"<br>");	//输出 "undefined"
</script>


instanceof运算符
能用 instanceof 运算符检查给定变量指向的对象的类型。例如：
<script type="text/javascript">
	function Car()//使用原型方式(或混合的构造函数/原型方式)申明instanceof才有用
	{}
	var car=new Car();
	document.write((car instanceof Car)+"<br>");//输出 true
</script>


with语句
(1)语法及作用
作用：with 语句用于设置代码在特定对象中的作用域。
语法：with (对象) { 对象使用范围 }
(2)示例
<script type="text/javascript">
	var s = "王子岳";
	with(s)
	{
		document.write(toString()+"<br>");	//输出 "王子岳",等效于s.toString()
	}
</script>
提示：with 语句是运行缓慢的代码块，尤其是在已设置了属性值时。大多数情况下，如果可能，最好避免使用它。


分支语句
(1)if...else...语句
<script language="javascript" type="text/javascript">
	var i=50;
	if(i==0)
	{
		document.write("i等于0");
	}
	else
	{
		document.write("i不等于0");
	}
</script>
(2)switch语句
<script language="javascript" type="text/javascript">
	var i=2;
	switch(i)
   {
   case 1:
     document.write("i等于1")
     break
   case 2:
     document.write("i等于2")
     break
   case 3:
     document.write("i等于3")
     break
   default:
     document.write("错误")
	}
</script>

消息框
(1)警告框
语法：alert(“文本”);
<script language="javascript" type="text/javascript">
	alert("我是警告框！！");
</script>
(2)确认框
语法：confirm(“文本”);
<script language="javascript" type="text/javascript">
	var r=confirm("点击确认!");//确认对话框
	if (r==true)
	{
		alert("你点击了确认！");
	}
	else
	{
		alert("你点击了取消！");
	}
</script>
(3)提示框
语法：prompt(“文本”,“默认值”);
<script language="javascript" type="text/javascript">
 	var name=prompt("请输入您的名字","王子岳");
  	if (name!=null && name!="")
	{
		document.write("你好！" + name);
    }
</script>

函数(一般定义到<head>标签之间)
(1)定义函数
function 函数名(var1,var2,...,varX)
  	{
  		代码．．．(return)
  	}
在函数内申明的变量，只能在函数中访问(其生存期就在整个函数中)。在函数外申明的变量，在整个HTML页面内都有效(生存期在整个HTML页面)。
(2)关于函数的arguments对象
在函数代码中，使用特殊对象 arguments，开发者无需明确指出参数名，就能访问它们。
例如，在函数 sayHi() 中，第一个参数是 message。用 arguments[0] 也可以访问这个值，即第一个参数的值（第一个参数位于位置 0，第二个参数位于位置 1，依此类推）。
<html>
<head>
<script type="text/javascript" language="javascript">
	function sayHi(message)//注意直接写参数名，不要写var申明
	{
		document.write(message+"<br>");
		document.write(arguments[0]);//使用arguments对象获得参数
	}
</script>
</head>

<body>
<script type="text/javascript" language="javascript">
	sayHi("王子岳");//调用函数
</script>
</body>
</html>
使用arguments.length检测参数个数
<html>
<head>
<script type="text/javascript" language="javascript">
	function num()
	{
		document.write("参数个数"+arguments.length+"<br>");//获取参数个数
	}
</script>
</head>

<body>
<script type="text/javascript" language="javascript">
	num();//调用函数
	num(1,2);
	num(1,2,3,5,"王子岳");
</script>
</body>
</html>
模拟函数重载
<html>
<head>
<script type="text/javascript" language="javascript">
	function num()
	{
		var i=arguments.length;
		
		switch(i)
		{
		case 1:
			document.write("参数："+arguments[0]+"<br>");
			break;
		case 2:
			document.write("相加："+(arguments[0]+arguments[1])+"<br>");
			break;
		default:
			document.write("参数个数出错！！");
			break;
		}
	}
</script>
</head>

<body>
<script type="text/javascript" language="javascript">
	num("王子岳");//调用函数
	num(55,2);
	num(1,2,3,5,"王子岳");
</script>
</body>
</html>

(3)Function对象(类)
Function对象的使用
函数实际上是功能完整的对象。Function 类可以表示开发者定义的任何函数。用 Function 类直接创建函数的语法如下：var function_name = new function(arg1, arg2, ..., argN, function_body)。
<html>
<head>
<script type="text/javascript" language="javascript">
	var sayHi = new Function("name","document.write(name+\"你好！！\");");
</script>
</head>

<body>
<script type="text/javascript" language="javascript">
	sayHi("王子岳");//调用函数
</script>
</body>
</html>
尽管可以使用 Function 构造函数创建函数，但最好不要使用它，因为用它定义函数比用传统方式要慢得多。不过，所有函数都应看作 Function 类的实例。
使用Function类的length属性
<html>
<head>
<script type="text/javascript" language="javascript">
	function fun1(){}
	function fun2(a1,a2){}
	function fun3(a1,a2,a3,a4,a5,a6,a7){}
</script>
</head>

<body>
<script type="text/javascript" language="javascript">
	document.write(fun1.length+" "+fun2.length+" "+fun3.length);
</script>
</body>
</html>
使用Function的length属性可以得到函数的形参个数
使用Function类的valueOf()方法和toString()方法
<html>
<head>
<script type="text/javascript" language="javascript">
	function fun()
	{
		document.write("王子岳");
	}
</script>
</head>

<body>
<script type="text/javascript" language="javascript">
	document.write(fun.toString());//输出函数的源代码
</script>
</body>
</html>
这两个方法返回的都是函数的源代码，在调试时尤其有用。


(4)闭包
闭包就是：函数可以使用函数之外定义的变量。
<html>
<head>
<script type="text/javascript" language="javascript">
	var iBaseNum=100;
	function fun(iNum1, iNum2)
	{
  		function doAdd() 
  		{
    		return iNum1 + iNum2 + iBaseNum;//使用函数外的变量
  		}
  		return doAdd();
	}
</script>
</head>
<body>
<script type="text/javascript" language="javascript">
	document.write(fun(10,30));
</script>
</body>
</html>

循环语句
(1)for循环
for循环的使用格式
格式1：
for (变量=开始值;变量<=结束值;变量=变量+步进值) 
{
    需执行的代码
}
格式2：
for (property in expression) 
{
    需执行的代码
}
例子
<script type="text/javascript" language="javascript">
	for (sProp in window) 
	{
  		document.write(sProp+"<br>");//显示 window 对象的所有属性。
	}
</script>
<script type="text/javascript" language="javascript">
	var array=new Array(1,2,3,4,5,6,7,8,9,0,-3); 
	for (i in array) 
	{
  		document.write(array[i]+"<br>");//显示数组内容
	}
</script>
(2)while循环
While循环的使用格式
格式1：
while (expression) 
{
需执行的代码
}
格式2：
do 
{
需执行的代码
} while (条件);
例子
<script type="text/javascript" language="javascript">
var i=10
do
{
	document.write(i+"<br>");
	i--;
}while (i>0)
</script>
(3)使用break和continue退出循环
break 命令可以终止循环的运行，然后继续执行循环之后的代码（如果循环之后有代码的话）。continue 命令会终止当前的循环，然后从下一个值继续运行。



1.JavaScript对象简介
(1)JavaScript对象也是有属性和方法的
对象属性的使用
<script type="text/javascript" language="javascript">
	var txt="王子岳";
	document.write(txt.length);//输出3
</script>
对象方法的使用
<script type="text/javascript" language="javascript">
	var txt="abcdefg";
	document.write(txt.toUpperCase());//输出ABCDEFG
</script>
(2)对象的定义与实例化
可以先实例化对象，再定义对象的属性和方法。
<script type="text/javascript" language="javascript">
	var oCar = new Object();//先实例化对象
	oCar.color = "red";//定义属性
	oCar.showColor = function()//定义方法
	{
		document.write(this.color+"<br>");//使用this引用当前对象
	};
	oCar.showColor();//调用方法，输出 "red"
	document.write(oCar.color);//使用属性，输出 "red"
</script>
如果构造函数无参数，括号则不是必需的。因此可以采用下面的形式实例化对象：
var oCar = new Object;
(3)对象的作用域
JavaScript对象只有公用作用域
由于缺少私有作用域，开发者确定了一个规约，说明哪些属性和方法应该被看做私有的。这种规约规定在属性前后加下划线：obj._color_ = "blue";下划线并不改变属性是公用属性的事实，它只是告诉其他开发者，应该把该属性看作私有的。
JavaScript对象没有静态作用域
严格来说，JavaScript并没有静态作用域。不过，它可以给构造函数提供属性和方法。构造函数只是函数，函数也是对象，对象可以有属性和方法。例如：
<script type="text/javascript" language="javascript">
	function sayHello()//构造函数，sayHello是一个类名
	{
		document.write("hello<br>");
	}
	sayHello.alternate = function()//构造函数的方法成员，可以看成静态方法
	{
		document.write("hi<br>");
	}
	sayHello.message="你好";//构造函数的属性，可以看成静态属性
	sayHello();//输出 "hello"
	sayHello.alternate();//输出 "hi"
	document.write(sayHello.message);//输出“你好”
</script>
关键字this
要掌握的最重要的概念之一是关键字this的用法，它用在对象的方法中。关键字 this 总是指向调用该方法的对象
<script type="text/javascript" language="javascript">
	function showColor() 
	{
		document.write(this.color+"<br>");
	}

	var oCar1 = new Object;
	oCar1.color = "red";
	oCar1.showColor = showColor;

	var oCar2 = new Object;
	oCar2.color = "blue";
	oCar2.showColor = showColor;

	oCar1.showColor();	//输出 "red"
	oCar2.showColor();	//输出 "blue"
</script>

(4)定义类或对象的方法
工厂方式
<script type="text/javascript" language="javascript">
	function createCar(sColor,iDoors,iMpg)//创建对象的工厂
	{
	  var oTempCar = new Object;
	  oTempCar.color = sColor;//属性
	  oTempCar.doors = iDoors;//属性
	  oTempCar.mpg = iMpg;//属性
	  oTempCar.showColor = function()//方法
	  {
	    document.write(this.color+"<br>");
	  };
	  return oTempCar;
	}
	
	var oCar1 = createCar("red",4,23);//创建对象
	var oCar2 = createCar("blue",3,25);//创建对象
	
	oCar1.showColor();//输出 "red"
	oCar2.showColor();//输出 "blue"
</script>

构造函数方式：首先在构造函数内没有创建对象，而是使用this关键字。使用new运算符构造函数时，在执行第一行代码前先创建一个对象，只有用 this 才能访问该对象。然后可以直接赋予 this属性，默认情况下是构造函数的返回值(不必明确使用 return 运算符)。
<script type="text/javascript" language="javascript">
	function Car(sColor,iDoors,iMpg) 
	{
	  this.color = sColor;
	  this.doors = iDoors;
	  this.mpg = iMpg;
	  this.showColor = function() 
	  {
	    document.write(this.color+"<br>");
	  }
	}
	var oCar1 = new Car("red",4,23);
	var oCar2 = new Car("blue",3,25);
	oCar1.showColor();//输出 "red"
　　	oCar2.showColor();//输出 "blue"
</script>
构造函数方式的问题：就像工厂函数，构造函数会重复生成函数，为每个对象都创建独立的函数版本。


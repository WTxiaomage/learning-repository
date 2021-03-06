- JS 中一共分成六种数据类型 
  - String 字符串 
  - Number 数值 
  - Boolean 布尔值 
  - Null 空值 
  - Undefined 未定义 
  - Object 对象 
  - 其中基本数据类型有 前 5 种 对象为引用数据类型

- String 字符串
  - 在JS中字符串需要使用引号引起来
  - 使用双引号或单引号都可以
  - 双引号中只能放单引号（或者反过来，正确嵌套），双引号不能放双引号，单引号不能放单引号
  - 在字符串中使用\作为转义字符
	```
	\'      ==>     '
	\"     ==>     "
	\n     ==>    换行
	\t      ==>    制表符
	\\      ==>     \	
	```
  - 使用typeof运算符检查字符串时，会返回"string"	

- Number 数值
	- JS中所有的整数和浮点数都是Number类型	
	- 其他进制的数字的表示：
		- 0b 开头表示二进制，但是不是所有的浏览器都支持
		- 0 开头表示八进制
		- 0x 开头表示十六进制
	- JS中可以表示的数字的最大值
	- Number.MAX_VALUE =1.7976931348623157e+308
	- Number.MIN_VALUE =5e-324 大于0的最小值
	- 如果使用Number表示的数字超过了最大值，则会返回一个
	 		Infinity 表示正无穷，
	 		-Infinity 表示负无穷
	 		使用typeof检查Infinity也会返回number
	- NaN 是一个特殊的数字，表示Not A Number
			使用typeof检查一个NaN也会返回number

	- 如果使用JS进行浮点运算，可能得到一个不精确的结果
	（其实所有语言在设计之初都存在某些数据无法精确显示，计算机底层是01表示数据，其他语言有解决方案，JavaScript没有而已）
	- 	所以千万不要使用JS进行对精确度要求比较高的运算


- Boolean 布尔值
	- 布尔值主要用来进行逻辑判断，布尔值只有两个
	- true 逻辑的真
	- false 逻辑的假
	- 使用typeof检查一个布尔值时，会返回"boolean"	

- Null 空值
	- 空值专门用来表示为空的对象，Null类型的值只有一个
	- null
	- 使用typeof检查一个Null类型的值时会返回"object"
	其他数据类型的typeof值都返回相应的数据类型，null返回object（历史遗留原因）
- Undefined 未定义
	- 如果声明一个变量但是没有为变量赋值此时变量的值就是undefined
	- 该类型的值只有一个 undefined
	- 使用typeof检查一个Undefined类型的值时，会返回"undefined"

- 引用数据类型	
	- Object 对象


- 类型转换
	- 类型转换就是指将其他的数据类型，转换为String Number 或 Boolean(主要是转换为这三种类型)
	
	- 转换为String
		- 方式一（强制类型转换）：
			- 调用被转换数据的toString()方法
				```
				var a = 123;
				a = a.toString();
				```
			- 注意：这个方法不适用于null和undefined
				由于这两个类型的数据中没有方法，所以调用toString()时会报错
				
		- 方式二（强制类型转换）：
			- 调用String()函数
			    ```
				var a = 123;
				a = String(a);
				```
			- 原理：对于Number Boolean String都会调用他们的toString()方法来将其转换为字符串，
				对于null值，直接转换为字符串"null"。对于undefined直接转换为字符串"undefined"
				
		- 方式三（隐式的类型转换）: 
			- 为任意的数据类型 +""
				```
				var a = true;
				a = a + "";
				```
			- 原理：和String()函数一样	
			
	- 转换为Number
		- 方式一（强制类型转换）：
			- 调用Number()函数
			    ```
				var s = "123";
				s = Number(s);
				```
			- 转换的情况：
				```
				1. 字符串 --> 数字
					- 如果字符串是一个合法的数字，则直接转换为对应的数字                         "123"
					- 如果字符串是一个非法的数字（空格也一样），则转换为NaN                    "123ab"
					- 如果是一个空串或纯空格的字符串，则转换为0                                           “”
				2. 布尔值 --> 数字
					- true转换为1
					- false转换为0
				3. 空值 --> 数字
					- null转换为0
				4. 未定义 --> 数字
					- undefined 转换为NaN
				```

		- 方式二（强制类型转换）：
			- 调用parseInt()或parseFloat()
			- 这两个函数专门用来将一个字符串转换为数字的
					如果对非String使用parseInt()或parseFloat()
					它会先将其转换为String然后在操作
			- parseInt()
				- 可以将一个字符串中的有效的整数位提取出来，并转换为Number
				    ```
					var a = "123.456px";
					a = parseInt(a); //123
					```
				- 如果需要可以在parseInt()中指定一个第二个参数，来指定进制	
					
			- parseFloat()
				- 可以将一个字符串中的有效的小数位提取出来，并转换为Number
					```
					var a = "123.456px";
					a = parseFloat(a); //123.456
					```
		- 方式三（隐式的类型转换）：
			- 使用一元的+来进行隐式的类型转换
				```
				var a = "123";
				a = +a;
				```
			- 原理：和Number()函数一样	
			
	- 转换为布尔值
		- 方式一（强制类型转换）：
			- 使用Boolean()函数
				```
				var s = "false";
				s = Boolean(s); //true
				```
			- 转换的情况:
				```
				字符串 --> 布尔
				- 除了空串其余全是true
					
				数值 --> 布尔
				- 除了0和NaN其余的全是true
					
				null、undefined ---> 布尔
				都是false
					
				对象 ---> 布尔
				都是true
				```
		- 方式二（隐式类型转换）：	
			- 为任意的数据类型做两次非运算，即可将其转换为布尔值
			    ```
				var a = "hello";
				a = !!a; //true
				```
				

- 事件（Event）
	- 事件指的是用户和浏览器之间的交互行为。比如：点击按钮、关闭窗口、鼠标移动。。。
	- 我们可以为事件来绑定回调函数来响应事件。
	- 绑定事件的方式：
		1. 可以在标签的事件属性中设置相应的JS代码
			例子：
				<button onclick="js代码。。。">按钮</button>
		2. 可以通过为对象的指定事件属性设置回调函数的形式来处理事件
			例子：
			```
			<button id="btn">按钮</button>
			<script>
				var btn = document.getElementById("btn");
				btn.onclick = function(){
				
				};
			</script>
			```

- 事件对象
	- 当响应函数被调用时，浏览器每次都会将一个事件对象作为实参传递进响应函数中，
		这个事件对象中封装了当前事件的相关信息，比如：鼠标的坐标，键盘的按键，鼠标的按键，滚轮的方向。。
	- 可以在响应函数中定义一个形参，来使用事件对象，但是在IE8以下浏览器中事件对象没有做完实参传递，而是作为window对象的属性保存
	- 例子：
		```
		元素.事件 = function(event){
			event = event || window.event;      //兼容IE8以下的写法
			
		};
		
		元素.事件 = function(e){
			e = e || event;
			
		};
		```
- 事件的冒泡（Bubble）
	- 事件的冒泡指的是事件向上传导，当后代元素上的事件被触发时，将会导致其祖先元素上的同类事件也会触发。
		```
		<div id="box1">
			我是box1
			<span id="s1">我是span</span>
		</div>
		```	    
		说白了就是点span的时候，触发span点击事件，也会触发div的点击事件，因为点span的同时，也点到了div的区域
	- 事件的冒泡大部分情况下都是有益的，如果需要取消冒泡，则需要使用事件对象来取消
	- 可以将事件对象的cancelBubble设置为true，即可取消冒泡
		- 例子：
			```
			元素.事件 = function(event){
				event = event || window.event;
				event.cancelBubble = true;
			};
			```
	
	chrome认为浏览器的滚动条是body的，可以通过body.scrollTop来获取
	火狐等浏览器认为浏览器的滚动条是html的，需要解决兼容问题
		```
		var st = document.body.scrollTop || document.documentElement.scrollTop;
		var sl = document.body.scrollLeft || document.documentElement.scrollLeft;
		```
	
	
	
	
	
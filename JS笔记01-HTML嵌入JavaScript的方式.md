# JavaScript

*运行在浏览器上的脚本语言*

## HTML嵌入JavaScript的方式

- 事件句柄

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>HTML嵌入JavaScript的方式</title>
  	</head>
  	<body>
  		<!-- 
  		1.JS是一门事件驱动型的编程语言
  		  其中有一个事件叫做鼠标单击：click
  		  对应的事件句柄叫做：onclick
  		  事件句柄是以HTML标签的属性存在的
  		  事件发生时onclick="JS代码"会被浏览器调用
  		2.JS代码弹出消息框
  		  在JS中有一内置对象叫做window，代表浏览器对象，使用其中的alert函数即可弹窗
  		  window.alert('消息内容')
  		  JS中的字符既可以双引号也可以使用单引号
  		  JS语句的结尾可以加分号也可以不加
  		-->
  		<input type="button" value="Hello" onclick="window.alert('Hellow')" /><br />
  		<!-- window.可以省略 -->
  		<input type="button" value="Hello" onclick="alert('Hello')
  		                                            alert('Hello Again')" />
  		
  	</body>
  </html>
  
  ```

  

- 脚本块

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>HTML嵌入JavaScript的方式2</title>
  	</head>
  	<body>
  		<!-- 脚本块 -->
  		<script type="text/javascript">
  			// 暴露在在脚本块中的程序，在页面打开的时候遵循自上而下的顺序逐行执行
  			window.alert('Hello')//alert函数会阻塞页面的加载
  			window.alert('Hello Again')
  			//JS代码中的单行注释
  			/*
  			JS代码中的
  			多行注释
  			*/
  		</script>
  		<input type="button" value="按钮" />
  		
  		<!-- 
  		JavaScript中的脚本块在一个页面中可以出现多次，没有要求
  		JavaScript中的脚本块出现位置也没有要求
  		 -->
  		
  	</body>
  </html>
  
  ```

  

- 引入外部独立的JS文件

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>HTML嵌入JavaScript的方式3</title>
  		<!-- 引入外部独立的JS文件 -->
  	</head>
  	<body>
  		<!-- 在需要的位置引入JS脚本文件 -->
  		<script type="text/javascript" src="js/引入外部独立的JS文件.js">
  			//这里写的代码不会执行
  		</script>
  		<!-- 同一个JS文件可以把引入多次，但实际开发中这种需求很少 -->
  		<script type="text/javascript" src="js/引入外部独立的JS文件.js"></script>
  		<!-- 不能写成 <script type="text/javascript" src="..." /> -->
  	</body>
  </html>
  
  ```

  ```js
  // js/引入外部独立的JS文件.js
  window.alert('Hello')
  window.alert('Hello Again')
  ```

  
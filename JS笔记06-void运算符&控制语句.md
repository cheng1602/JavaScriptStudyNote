# JavaScript

*运行在浏览器上的脚本语言*

- JavaScript的void运算符

  - void运算符的语法

    `void(表达式)` 

    执行表达式，但不返回任何结果

    `javascript:void(表达式)` 其中`javascript:`的作用是告诉浏览器后面是一段JS代码

    ```html
    <!DOCTYPE html>
    <html>
    	<head>
    		<meta charset="utf-8">
    		<title>JavaScript的void运算符</title>
    	</head>
    	<body>
    		<!-- 保留超链接样式，点击时执行一段JS代码，但页面不进行跳转 -->
    		<a href="javascript:void(0)" onclick="alert('Test Code')">超链接</a>
    		<!-- void(表达式) 括号中必须有表达式 -->
    	</body>
    </html>
    
    ```

    

- JavaScript的控制语句

  1. if 语句
  2. switch 语句
  3. while 语句
  4. do...while... 语句
  5. for 语句
  6. break 语句
  7. continue 语句
  8. for...in 语句（了解）
  9. with 语句（了解）

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>JavaScript的控制语句</title>
  	</head>
  	<body>
  		<script type="text/javascript">
  			//创建数组
  			var arr = [true, 1, -3.14, 'abc']; //JS中数组中元素的数据类型随意
  			//遍历数组
  			for (var i = 0; i < arr.length; i++) {
  				alert(arr[i]);
  			}
  
  			//for...in
  			for (var i in arr) {
  				//alert(i);i是数组中元素的下标
  				alert(arr[i]);
  			}
  
  			//for...in 语句可以遍历对象的属性
  			User = function(userid, password) {
  				this.userid = userid;
  				this.password = password;
  			}
  			var u = new User(1, 'a123');
  			alert(u.userid + u.password);//1a123
  			
  			for (var 属性名 in u){
  				alert(属性名);//userid password
  				alert(u[属性名]);//1 a123
  				//第一次循环输出 userid 1
  				//第二次循环输出 password a123
  			}
  			
  			//with 语句
  			with(u){
  				//自动把u.加到变量前，可读性不好，了解即可
  				alert(userid + ':' + password)
  			}
  			
  		</script>
  
  	</body>
  </html>
  
  ```

  
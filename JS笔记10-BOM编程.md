# JavaScript

*运行在浏览器上的脚本语言*

## BOM编程

- open和close

  - BOM编程中，window对象是顶级对象，代表浏览器窗口
  - window有open和close方法，可以开启窗口和关闭窗口

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>window的open和close</title>
  	</head>
  	<body>
  		<script type="text/javascript">
  
  		</script>
  
  		<input type="button" value="新窗口打开主页" onclick="window.open('https://github.com/cheng1602')" /><br />
  
  		<input type="button" value="当前窗口打开主页" onclick="window.open('https://github.com/cheng1602','_self')" /><br />
  
  		<input type="button" value="新窗口打开主页" onclick="window.open('https://github.com/cheng1602','_blank')" /><br />
  
  		<input type="button" value="父窗口打开主页" onclick="window.open('https://github.com/cheng1602','_parent')" /><br />
  
  		<input type="button" value="顶级窗口打开主页" onclick="window.open('https://github.com/cheng1602','_top')" /><br />
  
  		<input type="button" value="关闭当前窗口" onclick="window.close()" />
  
  
  	</body>
  </html>
  
  ```



- 消息框和确认框

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>消息框和确认框</title>
  	</head>
  	<body>
  		<script type="text/javascript">
  			function closeW() {
  				var c = window.confirm('确认关闭？');
  				if (c) {
  					close();
  				}
  			}
  		</script>
  		<input type="button" value="弹出消息框" onclick="window.alert('消息框')" />
  		<input type="button" value="弹出确认框(关闭)" onclick="closeW()" />
  	</body>
  </html>
  
  ```



- history对象

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>history对象</title>
  	</head>
  	<body>
  		<a href="history对象新窗口.html">history对象新窗口</a>
  		<br />
  		<input type="button" value="forward (1)" onclick="window.history.go(1)" />
  	</body>
  </html>
  
  ```

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>history对象新窗口</title>
  	</head>
  	<body>
  		<input type="button" value="back" onclick="window.history.back()" />
  		<br />
  		<input type="button" value="forward (-1)" onclick="window.history.go(-1)" />
  	</body>
  </html>
  
  ```



- location对象

  - 设置浏览器地址栏上的URL

    ```html
    <!DOCTYPE html>
    <html>
    	<head>
    		<meta charset="utf-8">
    		<title>设置浏览器地址栏上的URL</title>
    	</head>
    	<body>
    		<script type="text/javascript">
    			function cheng() {
    				
    				var L = window.location;
    				L.href = 'https://github.com/cheng1602';
    
    				//其他写法
    				//window.location.href = 'https://github.com/cheng1602';
    				//window.location = 'https://github.com/cheng1602';
    				//document.location = 'https://github.com/cheng1602';
    			}
    		</script>
    		<input type="button" value="笔记" onclick="cheng();" />
    	</body>
    </html>
    
    ```

    


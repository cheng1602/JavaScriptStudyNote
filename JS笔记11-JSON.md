# JavaScript

*运行在浏览器上的脚本语言*

## JSON

- JSON概述

  - *JavaScript Object Notationg* JavaScript对象标记，简称JSN（数据交换格式）
  - JSON主要的作用是：一种标准的数据交换格式
  - JSON是一种标准的轻量级的数据交换格式，特点是体积小易解析
  - 在实际开发中还有一种数据交换模式：XML，体积大，解析复杂，但优点在于语法严谨

  

- 语法格式

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>JSON</title>
  	</head>
  	<body>
  		<script type="text/javascript">
  			//创建JSON对象
  			//JSON也可以称为无类型对象（轻量级、轻巧、体积小、易解析）
  			var studentObj = {
  				"sno": "01",
  				"sname": "张三",
  				"sex": "男"
  			}
  
  			//访问JSON对象
  			document.write(studentObj.sno + studentObj.sname + studentObj.sex);
  			//01张三男
  
  			//JSON数组
  			var students = [{
  					"sno": "01",
  					"sname": "张三",
  					"sex": "男"
  				},
  				{
  					"sno": "02",
  					"sname": "李四",
  					"sex": "男"
  				},
  				{
  					"sno": "03",
  					"sname": "王五",
  					"sex": "男"
  				}
  			];
  
  			//遍历
  			for (i = 0; i < students.length; i++) {
  				document.write('<br />');
  				document.write(students[i].sno+students[i].sname+students[i].sex);
  			}
  			
  		</script>
  	</body>
  </html>
  
  ```

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>复杂一些的JSON对象</title>
  	</head>
  	<body>
  		<script type="text/javascript">
  			var user = {
  				"id": 01,
  				"name": "张三",
  				"sex": true,
  				"address": {
  					"city": "长沙",
  					"street": "岳麓区"
  				}
  			}
  			document.write(user.address.city + user.name);//长沙张三
  		</script>
  	</body>
  </html>
  
  ```



- eval函数

  - 作用

    - 将**字符串**当作一段**JS代码**解释并执行

    - java连接数据库，查询数据之后，将数据在java程序中拼接成JSON格式的字符串，将JSON格式的字符串响应到浏览器

    - java响应到浏览器上的仅仅是一个JSON格式的字符串，而不是JSON对象

    - 可以使用eval函数将JSON格式的字符串转换成JSON对象

      ```html
      <!DOCTYPE html>
      <html>
      	<head>
      		<meta charset="utf-8">
      		<title>eval函数</title>
      	</head>
      	<body>
      		<script type="text/javascript">
      			window.eval("var i = 10");
      			document.write(i);
      			document.write("<br />");
      
      			//java发送的JSON格式的字符串
      			var fromJava = "{\"name\":\"张三\",\"id\":\"01\"}"
      			//将JSON格式的字符串转换成JSON对象
      			window.eval("var jsonObj = " + fromJava);
      			document.write(jsonObj.name + jsonObj.id);//张三01
      		</script>
      	</body>
      </html>
      
      ```
  - 设置table的tbody

    ```html
  <!DOCTYPE html>
    <html>
    	<head>
    		<meta charset="utf-8">
    		<title>设置table的tbody</title>
    	</head>
    	<body>
    		<script type="text/javascript">
    			//有这些JSON数据
    			var user = {
    				"totle": 3,
    				"users": [{
    					"id": "01",
    					"name": "张三"
    
    				}, {
    					"id": "02",
    					"name": "李四"
    
    				}, {
    					"id": "03",
    					"name": "王五"
    				}]
    			}
    
    			//展示到table当中
    			window.onload = function() {
    				document.getElementById('btn').onclick = function() {
    					document.getElementById('sp').innerText = user.totle;
    					var uu = user.users;
    					var tab = '';
    					for (i = 0; i < uu.length; i++) {
    						tab += '<tr><th>' + uu[i].id + '</th><th>' + uu[i].name + '</th></tr>';
    					}
    					document.getElementById('tb').innerHTML = tab;
    				}
    			}
    		</script>
    
    		<input type="button" value="查询用户信息" id="btn" />
    		<h2>用户信息列表</h2>
    		<table border="1px" width="50%">
    			<tr>
    				<th>编号</th>
    				<th>姓名</th>
    			</tr>
    			<tbody id="tb">
    
    			</tbody>
    		</table>
    		总共<span id="sp">0</span>条记录。
    	</body>
    </html>
    
    ```
      

  

  

  

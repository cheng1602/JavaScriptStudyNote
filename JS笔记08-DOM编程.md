# JavaScript

*运行在浏览器上的脚本语言*

## DOM编程

- trim函数

  - 去除字符串的前后空白
  
    ```html
    <!DOCTYPE html>
    <html>
    	<head>
    		<meta charset="utf-8">
    		<title></title>
    	</head>
  	<body>
    		<script type="text/javascript" >
    			/*
    			String.prototype.trim = function(){
    				alert('扩展trim方法');
    			}
    			*/
    			window.onload = function(){
    				document.getElementById('username').onblur = function(){
    					var name = document.getElementById('username').value;
    					name = name.trim();
    					document.getElementById('username').value = name;
    					
    				}
    			}
    		</script>
    		<input type="text" id="username" value="请输入用户名" />		
    	</body>
    </html>
    
    ```
  
    

- 表单验证练习

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>表单验证</title>
  	</head>
  	<body>
  		<script type="text/javascript">
  			window.onload = function() {
  				var passwordTest;
  				var nameTest;
  				var emailTest
  				document.getElementById('passwordR').onblur = function() {
  
  					passwordTest = ((document.getElementById('password').value) === (document.getElementById('passwordR').value));
  					if (!passwordTest) {
  						document.getElementById('03').innerText = '两次输入不相同';
  					} else {
  						document.getElementById('03').innerText = '两次输入相同';
  					}
  					document.getElementById('passwordR').onfocus = function() {
  						document.getElementById('03').innerText = '';
  
  					}
  				}
  
  				document.getElementById('username').onblur = function() {
  					var username = document.getElementById('username').value;
  					var un = /^[a-zA-Z0-9]{6,14}$/;
  					nameTest = un.test(username);
  					if (!nameTest) {
  						document.getElementById('01').innerText = '用户名不合法';
  
  					} else {
  						document.getElementById('01').innerText = '用户名合法';
  					}
  					document.getElementById('username').onfocus = function() {
  						document.getElementById('01').innerText = '';
  
  					}
  				}
  
  				document.getElementById('email').onblur = function() {
  					var email = document.getElementById('email').value;
  					var em = /\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*/;
  					emailTest = em.test(email);
  					if (!emailTest) {
  						document.getElementById('04').innerText = '邮箱地址不合法';
  
  					} else {
  						document.getElementById('04').innerText = '邮箱地址合法！';
  					}
  					document.getElementById('email').onfocus = function() {
  						document.getElementById('04').innerText = '';
  
  					}
  				}
  				
  				document.getElementById('btn').onclick = function(){
  					if(passwordTest && nameTest && emailTest){
  						document.getElementById('btn').type = "submit";
  					}else{
  						alert('请确认填写的内容！')
  					}
  				}
  
  
  			}
  		</script>
  
  		<form action="http://localhost:8080/oa/save">
  			<table>
  				<tr>
  					<td>用户名</td>
  					<td><input type="text" name="username" id="username" />
  						<span style="color: crimson; font-size: 0.75rem;" id="01"></span>
  					</td>
  				</tr>
  				<tr>
  					<td>密码</td>
  					<td><input type="password" name="password" id="password" /></td>
  				</tr>
  				<tr>
  					<td>确认密码</td>
  					<td><input type="password" id="passwordR" />
  						<span style="color: crimson; font-size: 0.75rem;" id="03"></span>
  					</td>
  				</tr>
  				<tr>
  					<td>邮箱</td>
  					<td><input type="text" name="email" id="email" />
  						<span id="04" style="color: crimson;font-size: 0.75rem;">
  					</td>
  				</tr>
  				<tr>
  					<td colspan="2" align="center">
  						<input type="button" value="注册"  id="btn"/>
  						&nbsp;&nbsp;
  						<input type="reset" value="清空" />
  					</td>
  				</tr>
  			</table>
  
  		</form>
  
  	</body>
  </html>
  
  ```

  

- 复选框的全选和取消全选

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>复选框的全选和取消全选</title>
  	</head>
  	<body>
  		<script type="text/javascript">
  			window.onload = function() {
  				var f1 = document.getElementById('01');
  				//根据name取得对象
  				var checkarr = document.getElementsByName('发展');
  				f1.onclick = function() {
  					//全选、取消全选
  					for (var i = 0; i < checkarr.length; i++) {
  						checkarr[i].checked = f1.checked;
  					}
  				}
  
  				//对以上数组进行遍历
  				for (var i = 0; i < checkarr.length; i++) {
  					checkarr[i].onclick = function() {
  						var checkcount = 0;
  						//总量和选中的数量相等时第一个复选框选中
  						for (var i = 0; i < checkarr.length; i++) {
  							if (checkarr[i].checked) {
  								checkcount = checkcount + 1;
  							}
  						}
  						f1.checked = (checkcount === checkarr.length);
  					}
  
  				}
  			}
  		</script>
  		<input type="checkbox" id="01" />全选<br />
  		<input type="checkbox" name="发展" value="德" />德<br />
  		<input type="checkbox" name="发展" value="智" />智<br />
  		<input type="checkbox" name="发展" value="体" />体<br />
  		<input type="checkbox" name="发展" value="美" />美<br />
  	</body>
  </html>
  
  ```

  

- 获取下拉列表选中项的value

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>获取下拉列表选中项的value</title>
  	</head>
  	<body>
  		<script type="text/javascript">
  			
  		</script>
  		<select onchange="alert(this.value)">
  			<option value="">请选择等级</option>
  			<option value="1">D</option>
  			<option value="2">C</option>
  			<option value="3">B</option>
  			<option value="4">A</option>
  		</select>
  	</body>
  </html>
  
  ```

  
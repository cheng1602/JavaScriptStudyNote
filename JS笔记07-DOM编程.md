# JavaScript

*运行在浏览器上的脚本语言*

此节笔记以前的内容都为ECMAScript编程

- JavaScript的三大块

  - ECMAScript：JS的核心语法（ES规范/ECMA-262标准）

  - DOM：Document Object Model（文档对象模型）

    - 对网页当中的节点进行增删改查的过程

    - HTML文档被当作一棵DOM树来看待

      例如：`var domObj = document.getElementById('id');`

  - BOM：Browser Object Moder（浏览器对象模型）

    - 关闭浏览器窗口、打开新的浏览器窗口、后退、前进、浏览器地址栏上的地址等

  

## DOM编程

- DOM和BOM的区别与联系

  - BOM的顶级对象是：window
  - DOM的顶级对象是：document
  - 实际上BOM包括DOM

  

- 获取文本框的value

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>获取文本框的value</title>
  	</head>
  	<body>
  		<script type="text/javascript">
  			window.onload = function() {
  				document.getElementById('02').onclick = function() {
  					//获取文本框的value
  					var getValue = document.getElementById('01').value;
  					alert(getValue);
  				}
  
  				document.getElementById('04').onclick = function() {
  					document.getElementById('01').value = document.getElementById('03').value;
  				}
  			}
  		</script>
  		<input type="text" id="01" value='01' />
  		<input type="button" value="获取文本框的value" id="02" /><br />
  
  		<!-- 可以获取也可以修改 -->
  		<input type="text" id="03" value='03' />
  		<input type="button" value="将文本框03的内容填入01" id="04" /><br />
  
  		<!-- blur事件：失去焦点 -->
  		<input type="text" onblur="alert(this.value)" />
  
  	</body>
  </html>
  
  ```



- innerHTML和innerText操作div和span

  ```html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>innerHTML和innerText操作div和span</title>
  		<style type="text/css">
  			#div1 {
  				background-color: black;
  				width: 12.5rem;
  				height: 12.5rem;
  				border: aquamarine 0.0625rem solid;
  				position: absolute;
  				top: 12.5rem;
  				left: 12.5rem;
  			}
  		</style>
  	</head>
  	<body>
  		<script type="text/javascript">
  			window.onload = function() {
  				document.getElementById('01').onclick = function() {
  					//设置div的内容
  					//第一步：获取div对象
  					var divElt = document.getElementById('div1');
  					//第二步：使用innerHTML属性来设置元素内部的内容
  					divElt.innerHTML = '<font color="white">这里面就是内容</font>';
  					//div中显示白色字样的：这里面就是内容
  					//divElt.innerText = '<font color="white">这里面就是内容</font>';
  					//div中显示：<font color="white">这里面就是内容</font>
  				}
  			}
  		</script>
  		<input type="button" value="设置div" id="01" />
  		<div id="div1"></div>
  	</body>
  </html>
  
  ```

  - innerHTML和innerText的区别
    - 相同点：都是设置元素内部的内容
    - 不同点：
      - innerHTML会把后面的字符串当作一段HTML代码解释并执行
      - innerText只会将后面的字符串作为普通字符串来看待



- 正则表达式

  - 概述

    *Regular Expression*

    正则表达式主要用在字符串格式匹配方面

    正则表达式实际上是一名独立的学科，大部分编程语言都支持正则表达式

  - 常见的正则表达式符号

    | 符号     |                    含义                    |
    | -------- | :----------------------------------------: |
    | .        |         匹配除换行符以外的任意字符         |
    | \w       |        匹配字母或数字或下划线或汉字        |
    | \s       |              匹配任意空白字符              |
    | \d       |                  匹配数字                  |
    | \b       |            匹配单词的开始或结束            |
    | ^        |              匹配字符串的开始              |
    | $        |              匹配字符串的结束              |
    | *        |              重复零次或更多次              |
    | +        |              重复一次或更多次              |
    | ?        |               重复零次或一次               |
    | {n}      |                  重复n次                   |
    | {n;}     |              重复n次或更多次               |
    | {n,m}    |                 重复n到m次                 |
    | \W       | 匹配任意不是字母或数字或下划线或汉字的字符 |
    | \S       |            匹配任意不是空白字符            |
    | \D       |            匹配任意非数字的字符            |
    | \B       |       匹配不是单词的开始或结束的位置       |
    | [^x]     |          匹配除了x以外的任意字符           |
    | [^aeiou] |   匹配除了aeiou这几个字母以外的任意字符    |

    正则表达式当中的小括号优先级较高

    [1-9] 表示1到9中的任意1个数字（次数是1次）

    [A-Za-z0-9] 表示A-Za-z0-9中的任意1个字符

    [A-Za-z0-9-] 表示A-Z、a-z、0-9、-以上所有字符中的任意1个字符

    | 表示或者

    例如：QQ号：`^[1-9][0-9]{4,}$`

  - 正则表达式对象的创建与调用

    - 创建方式一

      `var regExp = /正则表达式/flags;`

    - 创建方式二（使用内置支持类RegExp）

      `var regExp = new RegExp ("正则表达式","flags");`

    - 关于flags

      | flags |       含义       |
      | ----- | :--------------: |
      | g     |     全局匹配     |
      | i     | 区分大小写的匹配 |
      | m     |     多行匹配     |

      *ES规范制定之后才支持m，当前面是正则表达式时，m不能用，只有前面是普通字符串时才可以使用*

    - 正则表达式对象的test()方法

      - 语法结构：`正则表达式对象.test(用户填写的字符串);` 
      - 匹配成功返回true，匹配失败返回false
    
  - 验证邮箱的正则表达式
  
    `\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*`
  
    ```html
    <!DOCTYPE html>
    <html>
    	<head>
    		<meta charset="utf-8">
    		<title>验证邮箱的正则表达式</title>
    	</head>
    	<body>
    		<script type="text/javascript">
    			window.onload = function() {
    				document.getElementById('button01').onclick = function() {
    					var email = document.getElementById('email').value;
    					var regExp = /\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*/;
    					var test = regExp.test(email);
    					if (!test) {
    						document.getElementById('emailError').innerText = '邮箱地址不合法！';
    
    					} else {
    						document.getElementById('emailError').innerText = '验证成功！';
    					}
    					document.getElementById('email').onfocus = function() {
    						document.getElementById('emailError').innerText = '';
    
    					}
    				}
    			}
    		</script>
    		<input type="text" id="email" />
    		<span id="emailError" style="color: crimson;font-size: 0.75rem;"></span>
    		<br />
    		<input type="button" value="验证" id="button01" />
    	</body>
    </html>
    
    ```
  
    


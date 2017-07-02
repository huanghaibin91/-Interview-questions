# JavaScript篇 #

----------
1. 介绍js的基本数据类型

	> Undefined、Null、Boolean、Number、String、
	> 
	> ECMAScript 2015 新增:Symbol(创建后独一无二且不可变的数据类型 )

2. 介绍js有哪些内置对象？

	> Object 是 JavaScript 中所有对象的父对象
	> 
	> 数据封装类对象：Object、Array、Boolean、Number 和 String
	> 
	> 其他对象：Function、Arguments、Math、Date、RegExp、Error

3. 说几条写JavaScript的基本规范？

	> - 不要在同一行声明多个变量。
	> - 请使用 ===/!==来比较true/false或者数值
	> - 使用对象字面量替代new Array这种形式
	> - 不要使用全局函数。
	> - Switch语句必须带有default分支
	> - 函数不应该有时候有返回值，有时候没有返回值。
	> - For循环必须使用大括号
	> - If语句必须使用大括号
	> - for-in循环中的变量 应该使用var关键字明确限定作用域，从而避免作用域污染。

4. JavaScript有几种类型的值？，你能画一下他们的内存图吗？

	> 栈：原始数据类型（Undefined，Null，Boolean，Number、String）
	>  堆：引用数据类型（对象、数组和函数）
	> 
	>  两种类型的区别是：存储位置不同；
	>  原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；
	>  引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定。如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体
	>  ![栈]('./image/zhan.png')
	>  ![堆]('./image/dui.png')

5. 如何实现数组的随机排序？

	    方法一：
		  	var arr = [1,2,3,4,5,6,7,8,9,10];
		  	function randSort1(arr){
		  		for(var i = 0,len = arr.length;i < len; i++ ){
		  			var rand = parseInt(Math.random()*len);
		  			var temp = arr[rand];
		  			arr[rand] = arr[i];
		  			arr[i] = temp;
		  		}
		  		return arr;
		  	}
		  	console.log(randSort1(arr));
	  	
	  	方法二：
		  	var arr = [1,2,3,4,5,6,7,8,9,10];
		  	function randSort2(arr){
		  		var mixedArray = [];
		  		while(arr.length > 0){
		  			var randomIndex = parseInt(Math.random()*arr.length);
		  			mixedArray.push(arr[randomIndex]);
		  			arr.splice(randomIndex, 1);
		  		}
		  		return mixedArray;
		  	}
		  	console.log(randSort2(arr));
	
	  	方法三：
		  	var arr = [1,2,3,4,5,6,7,8,9,10];
		  	arr.sort(function(){
		  		return Math.random() - 0.5;
		  	})
		  	console.log(arr);

6. Javascript如何实现继承？

	> - 构造继承
	> - 原型继承
	> - 实例继承
	> - 拷贝继承

7. 谈谈This对象的理解

	> - this总是指向函数的直接调用者（而非间接调用者）；
	> - 函数是否在 new 中调用（ new 绑定？如果是的话 this 绑定的是新创建的对象。 
	> - 函数是否通过 call、 apply(显式绑定）或者硬绑定调用？如果是的话，this绑定的是指定的对象。
	> - 函数是否在某个上下文对象中调用（ 隐式绑定）？ 如果是的话， this绑定的是那个上下文对象。 
	> - 如果都不是的话，使用默认绑定。 如果在严格模式下，就绑定到 undefined， 否则绑定到全局对象。
	> - 在事件中，this指向触发这个事件的对象，特殊的是，IE中的attachEvent中的this总是指向全局对象Window；

8. 什么是window对象? 什么是document对象?

	> window对象是指浏览器打开的窗口。
	> document对象是Documentd对象（HTML 文档对象）的一个只读引用，window对象的一个属性。

9. ["1", "2", "3"].map(parseInt) 答案是多少？

	> parseInt() 函数能解析一个字符串，并返回一个整数，需要两个参数 (val, radix)，
	> 其中 radix 表示要解析的数字的基数。【该值介于 2 ~ 36 之间，并且字符串中的数字不能大于radix才能正确返回数字结果值】;
	> 但此处 map 传了 3 个 (element, index, array),我们重写parseInt函数测试一下是否符合上面的规则。
	> 
		 function parseInt(str, radix) {
		     return str + '-' + radix;
		 };
		 var a = ["1", "2", "3"];
		 a.map(parseInt);  // ["1-0", "2-1", "3-2"] 不能大于radix
	 
	> 因为二进制里面，没有数字3,导致出现超范围的radix赋值和不合法的进制解析，才会返回NaN，所以["1", "2", "3"].map(parseInt) 答案也就是：[1, NaN, NaN]

10. 什么是闭包（closure），为什么要用它？

	 > 闭包是指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量,利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。
	> 
	>  闭包的特性：
	> 
	>  1.函数内再嵌套函数
	>  2.内部函数可以引用外层的参数和变量
	>  3.参数和变量不会被垃圾回收机制回收
	> 
		  //li节点的onclick事件都能正确的弹出当前被点击的li索引
		   <ul id="testUL">
		      <liindex = 0</li>
		      <liindex = 1</li>
		      <liindex = 2</li>
		      <liindex = 3</li>
		  </ul>
		  <script type="text/javascript">
		    var nodes = document.getElementsByTagName("li");
		  	for(i = 0;i<nodes.length;i+= 1){
		  	    nodes[i].onclick = (function(i){
		  	              return function() {
		  	                 console.log(i);
		  	              } //不用闭包的话，值每次都是4
		  	            })(i);
		  	}
		  </script>
	> 
	>  执行say667()后,say667()闭包内部变量会存在,而闭包内部函数的内部变量不会存在
	>  使得Javascript的垃圾回收机制GC不会收回say667()所占用的资源
	>  因为say667()的内部函数的执行需要依赖say667()中的变量
	>  这是对闭包作用的非常直白的描述
	> 
		  function say667() {
		  	var num = 666;
		  	var sayAlert = function() {
		  		alert(num);
		  	}
		  	num++;
		  	return sayAlert;
		  }
	>
		  var sayAlert = say667();
		  sayAlert()//执行结果应该弹出的667

11. new操作符具体干了什么呢?

	> - 创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
	> - 属性和方法被加入到 this 引用的对象中。
	> - 新创建的对象由 this 所引用，并且最后隐式的返回 this 。
	>
			var obj  = {};
			obj.__proto__ = Base.prototype;
			Base.call(obj);

12. 同步和异步的区别?

	> 同步的概念应该是来自于OS中关于同步的概念:不同进程为协同完成某项工作而在先后次序上调整(通过阻塞,唤醒等方式).同步强调的是顺序性.谁先谁后.异步则不存在这种顺序性.
	> 
	> 同步：浏览器访问服务器请求，用户看得到页面刷新，重新发请求,等请求完，页面刷新，新内容出现，用户看到新内容,进行下一步操作。
	> 
	> 异步：浏览器访问服务器请求，用户正常操作，浏览器后端进行请求。等请求完，页面不刷新，新内容也会出现，用户看到新内容。

13. 如何解决跨域问题?

	> jsonp、 iframe、window.name、window.postMessage、服务器上设置代理页面

14. 模块化开发怎么做？

> - 立即执行函数,不暴露私有成员
> 
		var module1 = (function(){
			var _count = 0;
		    var m1 = function(){
		     　　//...
		    };
		    var m2 = function(){
		     　　//...
		    };
		    return {
		     　　m1 : m1,
		     　　m2 : m2
		    };
		})();

15. AMD（Modules/Asynchronous-Definition）、CMD（Common Module Definition）规范区别？

	> Asynchronous Module Definition，异步模块定义，所有的模块将被异步加载，模块加载不影响后面语句运行。所有依赖某些模块的语句均放置在回调函数中。
	> 区别：
	> 1. 对于依赖的模块，AMD 是提前执行，CMD 是延迟执行。不过 RequireJS 从 2.0 开始，也改成可以延迟执行（根据写法不同，处理方式不同）。CMD 推崇 as lazy as possible.
	> 2. CMD 推崇依赖就近，AMD 推崇依赖前置。看代码：
	> 
		// CMD
		define(function(require, exports, module) {
			var a = require('./a')
			a.doSomething()
			// 此处略去 100 行
			var b = require('./b') // 依赖可以就近书写
				b.doSomething()
			    // ...
		})
		// AMD 默认推荐
		define(['./a', './b'], function(a, b) { // 依赖必须一开始就写好
			a.doSomething()
			   // 此处略去 100 行
			   b.doSomething()
			   // ...
		})

16. DOM操作——怎样添加、移除、移动、复制、创建和查找节点?

	> - 创建新节点
	>     createDocumentFragment()    //创建一个DOM片段
	>     
	>     createElement()   //创建一个具体的元素
	>     
	>     createTextNode()   //创建一个文本节点
	>     
	> - 添加、移除、替换、插入
	> 
	>     appendChild()
	>     
	>     removeChild()
	>     
	>     replaceChild()
	>     
	>     insertBefore() //在已有的子节点前插入一个新的子节点
	>     
	> - 查找
	>     getElementsByTagName()    //通过标签名称
	>     
	>     getElementsByName()    //通过元素的Name属性的值(IE容错能力较强，会得到一个数
	>     组，其中包括id等于name值的)
	>     
	>     getElementById()    //通过元素Id，唯一性

17. .call() 和 .apply() 的区别？

	> - apply()函数有两个参数：第一个参数是上下文，第二个参数是参数组成的数组。如果上下文是null，则使用全局对象代替。如：function.apply(this,[1,2,3]);
	> - call()的第一个参数是上下文，后续是实例传入的参数序列。如：function.call(this,1,2,3);

18. 哪些前端性能优化的方法？

	> - 减少http请求次数：CSS Sprites, JS、CSS源码压缩、图片大小控制合适；网页Gzip，CDN托管，data缓存 ，图片服务器。
	> 
	> - 前端模板 JS+数据，减少由于HTML标签导致的带宽浪费，前端用变量保存AJAX请求结果，每次操作本地变量，不用请求，减少请求次数
	> 
	> - 用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能。
	> 
	> - 当需要设置的样式很多时设置className而不是直接操作style。
	> 
	> - 少用全局变量、缓存DOM节点查找的结果。减少IO读取操作。
	> 
	> - 避免使用CSS Expression（css表达式)又称Dynamic properties(动态属性)。
	> 
	> - 图片预加载，将样式表放在顶部，将脚本放在底部  加上时间戳。
	> 
	> - 避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢。
	> 
	> - 对普通的网站有一个统一的思路，就是尽量向前端优化、减少数据库操作、减少磁盘IO。向前端优化指的是，在不影响功能和体验的情况下，能在浏览器执行的不要在服务端执行，能在缓存服务器上直接返回的不要到应用服务器，程序能直接取得的结果不要到外部取得，本机内能取得的数据不要到远程取，内存能取到的不要到磁盘取，缓存中有的不要去数据库查询。减少数据库操作指减少更新次数、缓存结果减少查询次数、将数据库执行的操作尽可能的让你的程序完成（例如join查询），减少磁盘IO指尽量不使用文件系统作为缓存、减少读写文件次数等。程序优化永远要优化慢的部分，换语言是无法“优化”的。

19. JS数组去重

		Array.prototype.unique1 = function () {
		  var n = []; //一个新的临时数组
		  for (var i = 0; i < this.length; i++) //遍历当前数组
		  {
		    //如果当前数组的第i已经保存进了临时数组，那么跳过，
		    //否则把当前项push到临时数组里面
		    if (n.indexOf(this[i]) == -1) {
				n.push(this[i];
			}
		  }
		  return n;
		}
		
		Array.prototype.unique2 = function()
		{
		    var n = {},r=[]; //n为hash表，r为临时数组
		    for(var i = 0; i < this.length; i++) //遍历当前数组
		    {
		        if (!n[this[i]]) //如果hash表中没有当前项
		        {
		            n[this[i]] = true; //存入hash表
		            r.push(this[i]); //把当前数组的当前项push到临时数组里面
		        }
		    }
		    return r;
		}
		
		Array.prototype.unique3 = function()
		{
		    var n = [this[0]]; //结果数组
		    for(var i = 1; i < this.length; i++) //从第二项开始遍历
		    {
		        //如果当前数组的第i项在当前数组中第一次出现的位置不是i，
		        //那么表示第i项是重复的，忽略掉。否则存入结果数组
		        if (this.indexOf(this[i]) == i) {
					n.push(this[i];
				}
		    }
		    return n;
		}

20. js操作获取和设置cookie

		//创建cookie
		function setCookie(name, value, expires, path, domain, secure) {
		    var cookieText = encodeURIComponent(name) + '=' + encodeURIComponent(value);
		    if (expires instanceof Date) {
		        cookieText += '; expires=' + expires;
		    }
		    if (path) {
		        cookieText += '; expires=' + expires;
		    }
		    if (domain) {
		        cookieText += '; domain=' + domain;
		    }
		    if (secure) {
		        cookieText += '; secure';
		    }
		    document.cookie = cookieText;
		}
		
		//获取cookie
		function getCookie(name) {
		    var cookieName = encodeURIComponent(name) + '=';
		    var cookieStart = document.cookie.indexOf(cookieName);
		    var cookieValue = null;
		    if (cookieStart > -1) {
		        var cookieEnd = document.cookie.indexOf(';', cookieStart);
		        if (cookieEnd == -1) {
		            cookieEnd = document.cookie.length;
		        }
		        cookieValue = decodeURIComponent(document.cookie.substring(cookieStart + cookieName.length, cookieEnd));
		    }
		    return cookieValue;
		}
		
		//删除cookie
		function unsetCookie(name) {
		    document.cookie = name + "= ; expires=" + new Date(0);
		}

21. ajax 有那些优缺点?如何解决跨域问题?

	> - 优点：
	> 	- 通过异步模式，提升了用户体验.
	> 	- 优化了浏览器和服务器之间的传输，减少不必要的数据往返，减少了带宽占用.
	> 	- Ajax在客户端运行，承担了一部分本来由服务器承担的工作，减少了大用户量下的服务器负载。
	> 	- Ajax可以实现动态不刷新（局部刷新）
	> - 缺点：
	> 	- 安全问题 AJAX暴露了与服务器交互的细节。
	> 	- 对搜索引擎的支持比较弱。
	> 	- 不容易调试。
	> - 解决跨越问题可以使用，jsonp、 iframe、window.name、window.postMessage、服务器上设置代理页面。

22. GET和POST的区别，何时使用POST？

	> GET：一般用于信息获取，使用URL传递参数，对所发送信息的数量也有限制，一般在2000个字符
	> 
	> POST：一般用于修改服务器上的资源，对所发送的信息没有限制。
	> 
	> GET方式需要使用Request.QueryString来取得变量的值，而POST方式通过Request.Form来获取变量的值，也就是说Get是通过地址栏来传值，而Post是通过提交表单来传值。
	> 
	> 然而，在以下情况中，请使用 POST 请求：
	> 无法使用缓存文件（更新服务器上的文件或数据库）
	> 向服务器发送大量数据（POST 没有数据量限制）
	> 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠

23. ajax过程

	> - 创建XMLHttpRequest对象,也就是创建一个异步调用对象.
	> - 创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息.
	> - 设置响应HTTP请求状态变化的函数.
	> - 发送HTTP请求.
	> - 获取异步调用返回的数据.
	> - 使用JavaScript和DOM实现局部刷新. 

24. 写一个获取非行间样式的函数

		function getStyle(ele,attr,value) {
			if(!value) {
				if(ele.currentStyle) {
					return ele.currentStyle(attr)
				} else {
					ele.getComputedStyle(attr,false)
				}
			} else {
				ele.style[attr]=value
			}
		}

25. javascript的同源策略

	> 一段脚本只能读取来自于同一来源的窗口和文档的属性，这里的同一来源指的是主机名、协议和端口号的组合

26. 
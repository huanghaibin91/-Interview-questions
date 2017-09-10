# HTML & CSS篇 #

----------
1.  常见得浏览器？有哪些内核(Layout Engine)?

	> Trident内核：IE,MaxThon,腾讯浏览器,The World,360,搜狗浏览器等。[又称MSHTML]
	> 
	> Gecko内核：Netscape6及以上版本，火狐,MozillaSuite/SeaMonkey等
	> 
	> Presto内核：Opera7及以上。     [Opera内核原为：Presto，现为：Blink;]
	> 
	> Webkit内核：Safari,Chrome等。   [ Chrome的：Blink（WebKit的分支）]
	
2. Doctype作用？标准模式与兼容模式各有什么区别?

	> 1. <!DOCTYPE>声明位于位于HTML文档中的第一行，处于 <html标签之前。告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。
	>
	> 2. 标准模式的排版 和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。

3. HTML5 为什么只需要写 <!DOCTYPE HTML>？

	> HTML5 不基于 SGML(标准通用标记语言)，因此不需要对DTD进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型。

4. 页面导入样式时，使用link和@import有什么区别？
	
	> 1. link属于XHTML标签，除了加载CSS外，还能用于定义RSS, 定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;
	> 2. 页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;
	> 3. import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题;
	
5. 介绍一下你对浏览器内核的理解？
	
	> 1. 主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。
	> 2. 渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。
	> 3. JS引擎：解析和执行javascript来实现网页的动态效果。

6. 简述一下你对HTML语义化的理解？

	> 用正确的标签做正确的事情。
	> html语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;
	> 即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的;
	> 搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO;
	> 使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。

7. 如何实现浏览器内多个标签页之间的通信?

	> WebSocket、SharedWorker；
	> 也可以调用localstorge、cookies等本地存储方式；
	> localstorge另一个浏览上下文里被添加、修改或删除时，它都会触发一个事件，
	> 我们通过监听事件，控制它的值来进行页面信息通信；
	> 注意quirks：Safari 在无痕模式下设置localstorge值时会抛出 QuotaExceededError 的异常；

8. 如何在页面上实现一个圆形的可点击区域？

	> 1. map+area或者svg
	> 2. border-radius
	> 3. 纯js实现 需要求一个点在不在圆上简单算法、获取鼠标坐标等等

9. 介绍一下标准的CSS的盒子模型？低版本IE的盒子模型有什么不同的？
	
	> CSS 框模型 (Box Model) 规定了元素框处理元素内容、内边距、边框和外边距的方式
	> 1. 有两种， IE 盒子模型(IE8以下)、W3C 盒子模型；
	> 2. 盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；
	> 3. 区  别： IE的content部分把 border 和 padding计算了进去;

10. CSS中哪些属性可以继承？哪些不可以？

	> 不可继承的：display、margin、border、padding、background、height、min-height、max-height、width、min-width、max-width、overflow、position、left、right、top、bottom、z-index、float、clear、table-layout、vertical-align、page-break-after、page-bread-before和unicode-bidi。
	> 
	> 所有元素可继承：visibility和cursor。
	> 
	> 内联元素可继承：letter-spacing、word-spacing、white-space、line-height、color、font、font-family、font-size、font-style、font-variant、font-weight、text-decoration、text-transform、direction。
	> 
	> 终端块状元素可继承：text-indent和text-align。
	> 
	> 列表元素可继承：list-style、list-style-type、list-style-position、list-style-image。
	> 
	> 表格元素可继承：border-collapse。

11. div居中

	- 水平居中：给div设置一个宽度，然后添加margin:0 auto属性，flex也可以

	- 让绝对定位的div居中

	    	div {
			 	width: 300px;
			 	height: 300px;
				background-color: pink;	/* 方便看效果 */
			 	margin: auto;
				position: absolute;
			 	top: 0;
			 	left: 0;
			 	bottom: 0;
			 	right: 0;
	 		}
	
	- 水平垂直居中
			
			1. 确定容器的宽高，宽500、高300的层，设置层的外边距
			
			 div {
			 	position: relative;		/* 相对定位或绝对定位均可 */
			 	width:500px;
			 	height:300px;
			 	top: 50%;
			 	left: 50%;
			 	margin: -150px 0 0 -250px; 	/* 外边距为自身宽高的一半 */
			 	background-color: pink;	 	/* 方便看效果 */
			
			  }
			
			2.未知容器的宽高，利用 `transform` 属性
			
			 div {
			 	position: absolute;		/* 相对定位或绝对定位均可 */
			 	width:500px;
			 	height:300px;
			 	top: 50%;
			 	left: 50%;
			 	transform: translate(-50%, -50%);
			 	background-color: pink;	 	/* 方便看效果 */
			
			 }
			
			3.利用 flex 布局，实际使用时应考虑兼容性
			
			 .container {
			 	display: flex;
			 	align-items: center; 		/* 垂直居中 */
			 	justify-content: center;	/* 水平居中 */
			
			 }
			 .container div {
			 	width: 100px;
			 	height: 100px;
			 	background-color: pink;		/* 方便看效果 */
			 } 
	
12. css多列等高如何实现？

	> 利用padding-bottom|margin-bottom正负值相抵；
	> 设置父容器设置超出隐藏（overflow:hidden），这样子父容器的高度就还是它里面的列没有设定padding-bottom时的高度，
	> 当它里面的任一列高度增加了，则父容器的高度被撑到里面最高那列的高度，
	> 其他比这列矮的列会用它们的padding-bottom补偿这部分高度差。

13. 经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用hack的技巧？

	> - 浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。
	> 
	> - IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。
	> 
	>     浮动ie产生的双倍距离 #box{ float:left; width:10px; margin:0 0 0 100px;}
	> 
	>     这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 ——_display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)
	> 
	>     渐进识别的方式，从总体中逐渐排除局部。
	> 
	>     首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。
	>     接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。
	> 
	>     css
	>         .bb{
	>             background-color:red;/*所有识别*/
	>   	      background-color:#00deff\9; /*IE6、7、8识别*/
	>   	      +background-color:#a200ff;/*IE6、7识别*/
	>   	      _background-color:#1e0bd1;/*IE6识别*/
	>         }
	> -  IE下,可以使用获取常规属性的方法来获取自定义属性,
	>      也可以使用getAttribute()获取自定义属性;
	>      Firefox下,只能使用getAttribute()获取自定义属性。
	>      解决方法:统一通过getAttribute()获取自定义属性。
	> -  IE下,even对象有x,y属性,但是没有pageX,pageY属性;
	>      Firefox下,event对象有pageX,pageY属性,但是没有x,y属性。
	> -  解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。
	> -  Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,
	>      可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决。
	> -  超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了解决方法是改变CSS属性的排列顺序:L-V-H-A :  a:link {} a:visited {} a:hover {} a:active {}

14. 对BFC规范(块级格式化上下文：block formatting context)的理解？
	
	> （W3C CSS 2.1 规范中的一个概念,它是一个独立容器，决定了元素如何对其内容进行定位,以及与其他元素的关系和相互作用。）一个页面是由很多个 Box 组成的,元素的类型和 display 属性,决定了这个 Box 的类型。不同类型的 Box,会参与不同的 Formatting Context（决定如何渲染文档的容器）,因此Box内的元素会以不同的方式渲染,也就是说BFC内部的元素和外部的元素不会互相影响。
  
15. 请解释一下为什么需要清除浮动？清除浮动的方式

	> - 清除浮动是为了清除使用浮动元素产生的影响。浮动的元素，高度会塌陷，而高度的塌陷使我们页面后面的布局不能正常显示。
	> - 父级div定义height；
	> - 父级div 也一起浮动；
	> - 常规的使用一个class；
	>	
			.clearfix:before, .clearfix:after {
		  	    content: " ";
		  	    display: table;
		  	}
		  	.clearfix:after {
		  	    clear: both;
		  	}
		  	.clearfix {
		  	    *zoom: 1;
		  	}
	>
	> - SASS编译的时候，浮动元素的父级div定义伪类:after
	>
		   	&:after,&:before{
		   	    content: " ";
		        visibility: hidden;
		        display: block;
		        height: 0;
		        clear: both;
		   	}
	> 
	> - 解析原理：
	> 	- display:block 使生成的元素以块级元素显示,占满剩余空间;
	> 	- height:0 避免生成内容破坏原有布局的高度。
	> 	- visibility:hidden 使生成的内容不可见，并允许可能被生成内容盖住的内容可以进行点击和交互;
	> 	- 通过 content:"."生成内容作为最后一个元素，至于content里面是点还是其他都是可以的，例如oocss里面就有经典的 content:".",有些版本可能content 里面内容为空,是不推荐这样做的,firefox直到7.0 content:”" 仍然会产生额外的空隙；
	> 	- zoom：1 触发IE hasLayout。当设置了zoom的值之后，所设置的元素就会就会扩大或者缩小，高度宽度就会重新计算了，这里一旦改变zoom值时其实也会发生重新渲染。
	> 	
	> 常用清除浮动方法总结：
	> 	
	>（1）父级div定义height。
	> 	
	>（2）结尾处加空div标签clear:both。
	>	
	>（3）父级div定义伪类:after和zoom。
	>	
	>（4）父级div定义overflow:hidden。
	>	
	>（5）父级div定义overflow:auto。
	>	
	>（6）父级div也浮动，需要定义宽度。
	>	
	>（7）父级div定义display:table。
	>	
	>（8）结尾处加br标签clear:both

16. 什么是外边距合并？

	> - 外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。如果有负外边距，如果垂直外边距都设置为负值，浏览器会取两个外边距绝对值的最大值。如果一个正外边距与一个负外边距合并，会从正外边距减去这个负外边距的绝对值。zoom属是IE浏览器的专有属性
	> 
	> ![]('./image/margin1.gif')
	> 
	> - 当一个元素包含在另一个元素中时（假设没有内边距或边框把外边距分隔开），它们的上和/或下外边距也会发生合并，
	> 
	> ![]('./image/margin2.gif')
	> 
	> - 假设有一个空元素，它有外边距，但是没有边框或填充。在这种情况下，上外边距与下外边距就碰到了一起，它们会发生合并
	> 
	> ![]('./image/margin3.gif')
	> 
	> 如果这个外边距遇到另一个元素的外边距，它还会发生合并
	> ![]('./image/margin4.gif')

17. 父元素与子元素之间的margin-top问题

	> 父元素的盒子包含一个子元素盒子，给子元素盒子一个垂直外边距margin-top,父元素盒子也会往下走margin-top的值，而子元素和父元素的边距则没有发生变化。
	>     
	> ![]('./image/margin5.jpg')
	>  	    
	> 解决方法：
	>  	    
	> - 修改父元素的高度，增加padding-top样式模拟（padding-top：1px；常用）
	> - 为父元素添加overflow：hidden；样式即可（完美）
	> - 为父元素或者子元素声明浮动（float：left；可用）
	> - 为父元素添加border（border:1px solid transparent可用）
	> - 为父元素或者子元素声明绝对定位 

18. CSS优化、提高性能的方法有哪些？

	> - 关键选择器（key selector）。选择器的最后面的部分为关键选择器（即用来匹配目标元素的部分）；
	> - 如果规则拥有 ID 选择器作为其关键选择器，则不要为规则增加标签。过滤掉无关的规则（这样样式系统就不会浪费时间去匹配它们了）；
	> - 提取项目的通用公有样式，增强可复用性，按模块编写组件；增强项目的协同开发性、可维护性和可扩展性;
	> - 使用预处理工具或构建工具（gulp对css进行语法检查、自动补前缀、打包压缩、自动优雅降级）；

19. ::before 和 :after中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用

	> - 单冒号(:)用于CSS3伪类，双冒号(::)用于CSS3伪元素。（伪元素由双冒号和伪元素名称组成），双冒号是在当前规范中引入的，用于区分伪类和伪元素。不过浏览器需要同时支持旧的已经存在的伪元素写法，比如:first-line、:first-letter、:before、:after等，而新的在CSS3中引入的伪元素则不允许再支持旧的单冒号的写法。
	> - 想让插入的内容出现在其它内容前，使用::before，否者，使用::after；在代码顺序上，::after生成的内容也比::before生成的内容靠后。如果按堆栈视角，::after生成的内容会在::before生成的内容之上

20. 设置元素浮动后，该元素的display值是多少？

	> 自动变成了 display:block

21. position:fixed;在android下无效怎么处理？

	> fixed的元素是相对整个页面固定位置的，你在屏幕上滑动只是在移动这个所谓的viewport，原来的网页还好好的在那，fixed的内容也没有变过位置，所以说并不是iOS不支持fixed，只是fixed的元素不是相对手机屏幕固定的。
	> 
		<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no"/>

22. 如果需要手动写动画，你认为最小时间间隔是多久，为什么？

	> 多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60＊1000ms ＝ 16.7ms

23. CSS规则优先级

		!important >  id > class > tag  ，important 比 内联优先级高

24. 什么叫优雅降级和渐进增强？

	> - 优雅降级：Web站点在所有新式浏览器中都能正常工作，如果用户使用的是老式浏览器，则代码会检查以确认它们是否能正常工作。由于IE独特的盒模型布局问题，针对不同版本的IE的hack实践过优雅降级了,为那些无法支持功能的浏览器增加候选方案，使之在旧式浏览器上以某种形式降级体验却不至于完全失效.
	> 
	> - 渐进增强：从被所有浏览器支持的基本功能开始，逐步地添加那些只有新式浏览器才支持的功能,向页面增加无害于基础浏览器的额外样式和功能的。当浏览器支持时，它们会自动地呈现出来并发挥作用。
# DOM #

	文档对象模型	

	一个Html文件可以看做是一个文档，也就是一个对象

	元素(Element):所有的标签都可以看成一个元素，也就是一个对象

	节点(Node):文档中所有的内容都是节点，包括标签、属性、文字....

	root(根)

	由文档以及文档中的所有元素值组成的树状图形叫做树形图

	需要处理兼容问题
		1、innerText和textContent   火狐与谷歌支持innerText  IE8只支持textContent

		2、获取第一个子节点、获取第一个子元素
		  获取最后一个子节点、最后一个子元素
		  获取一个元素的上一个节点、上一个元素
		  获取一个元素的下一个节点、下一个元素   
		  代码显示火狐与谷歌都是支持的，可以正确的打印出来
		  IE8获取节点的时候获取的都是元素，使用获取元素的代码时获取的都是undefined

		3、一个事件调用多个方法的兼容
		  addEventListener(type,fun,bool);//谷歌、火狐支持，IE8不支持 type为去掉on的事件 比如onclick在这里填写click
		  attachEvent(type,fun);//谷歌、火狐不支持，IE8支持 type为带on的事件

		4、获取计算后的属性值
			function getStyle(element ,attr){

			return window.getComputedStyle?window.getComputedStyle(element,null)[attr]:element.currentStyle[attr];

				}

		5、获取卷曲的兼容代码
			function  getScroll(){

				return {left:window.pageXoffset||document.documentElement.scrollLeft||document.body.scrollLeft,
						top:window.pageYoffset||document.documentElement.scrollTop||document.body.scrollTop
						}
				}
		6、事件参数对象  
			//谷歌和火狐在注册事件回调函数时，会接收一个事件参数对象，包含的是手势操作的对象，但是IE8不支持 只支持window.event

			//e.pageX     鼠标相对于页面边界X轴的坐标
			//e.pageY     鼠标相对于页面边界Y轴的坐标
			//e.clientX   鼠标相对于可视页面边界的X轴坐标
			//e.clientY   鼠标相对于可视页面边界的y轴坐标
			element.onclick=function (e){
					e=window.event|e;
					
				}
		7、阻止事件冒泡
			事件参数对象 e.stopPropagation;   window.event.cancelBubble=true;

DOM中设置点击事件

		三种方法  onclick   addEventListener   attachEvent

移除事件
    
		onclick=null;    removeEventListener   detachEvent

	事件有三个阶段
		事件捕获阶段(从外向内过程)  事件目标阶段(到了指定的目标的过程)   事件冒泡阶段(事件执行的顺序，从内到外)   默认是事件冒泡阶段  

		使用addEventListener的最后一个参数可以改变事件的阶段

节点的相关操作
	
	节点概念：一对内部标签含有很多节点，包括 标签、属性、文本(换行符、空白符、文字)
	节点：Node   
	相关属性：
		1、nodeType  节点类型 标签：1  属性：2 文本：3
		2、nodeName  节点名字 标签：大写的标签名字  属性：小写的属性名字  文本：#text
		3、nodeValue 节点值   标签：null  属性节点：属性的值   文本：文本的值

	获取节点的相关操作：假设 ulObject 是一个ul的元素对象
		1、获取父节点  ulObject.parentNode  
		  获取父元素  ulObject.parentElement

		2、获取子节点  ulObject.childNodes  谨记子节点包括 标签、属性、文本
		  获取子元素  ulObject.children

	-----以上代表ie8、谷歌、火狐均支持，以下几个需要写出兼容代码，因为ie8获取节点的时候获取的都是元素，获取元素的undefined-------

		3、获取第一个子节点 ulObject.firstChild 
		  获取第一个子元素 ulObject.firstElementChild

		4、获取最后一个子节点 ulObject.lastChild
		  获取最后一个子元素 ulObject.lastElementChild

		5、获取某个元素的上一个兄弟节点 ulObject.previousSibling
		  获取上一个兄弟元素          ulObject.previousElementSibling

		6、获取下一个兄弟节点  ulObject.nextSibling
		  获取下一个兄弟元素  ulObject.nextElementSibling

	获取第一个或者最后一个元素的兼容代码
	
		function getFirstChildElement(element){//获取第一个子元素
			
				if(element.firstElementChild){
					return element.firstElementChild				
					}else{
					
						let node=element.firstChild;
						while(node&&node.nodeType!=1){//防止某些浏览器node获取的不是标签元素，而是其它节点对象
							node=node.nextSibling;
							}	

					}

			}

		function getFirstChildElement(element){//获取最后一个子元素
			
				if(element.lastElementChild){
					return element.lastElementChild				
					}else{
					
						let node=element.lastChild;
						while(node&&node.nodeType!=1){//防止某些浏览器node获取的不是标签元素，而是其它节点对象
							node=node.previousSibling;
							}	

					}

			}

标签内部添加标签的方法 DOM有三种方法

	1、document.write("标签对(比如:<p>我是一个p</p>)");
		这种方式写入标签时：如果在界面加载完成之后，会清除界面上的所有内容
						  界面加载中使用这种方式，则可以共存

	2、对象.innerHtml("标签对")  但是每调用一次就会将以前的清除
	3、let element=document.createElement(""标签对);------>使用父元素.appendChild(element)放入父元素中，是追加效果

DOM之自定义属性

	元素.setAttribute(属性名称，属性值);   
	获取属性值 元素.getAttribute(属性名称);
	清除属性(是否自定义的均可) removeAttribute("属性名称");

# 三大系列 #

offset系列

	offsetWidth:获取元素的宽(包括边框以及内边距的值)

    offsetHeight:获取元素的高(包括边框以及内边距的值)

    offsetLeft:获取元素距离左边位置的值

    offsetTop:获取元素距离上面位置的值
	
	注意：加入一个子元素嵌套在一个父元素中
		1、如果子元素未脱标
			offsetLeft:父级元素margin+父级元素padding+父级元素的border+自己的margin
		2、如果元素脱标
			offsetLeft:自己的left和自己的margin

scroll系列  卷曲

	console.log(my$("dv").scrollWidth);//元素中内容的实际的宽(不含边框) 没有内容就是元素的宽

	console.log(my$("dv").scrollHeight);//元素中内容的实际的高(不含边框) 没有内容或者内容不足元素高度大小就是元素的高

	console.log(my$("dv").scrollTop);//向上卷曲出去的距离

	console.log(my$("dv").scrollLeft);//向左卷曲出去的距离
	
client系列  可视区域

	clientWidth:可视区域的宽(没有边框),边框内部的宽度

	clientHeight:可视区域的高(没有边框),边框内部的高度

	clientLeft:左边边框的宽度

	clientTop :上面的边框的高度

# BOM #

	浏览器对象模型

location对象  浏览器地址栏对象

		//location对象
		//console.log(window.location);
		
		//地址栏上#及后面的内容
		console.log(window.location.hash);

		//主机名及端口号
		console.log(window.location.host);

		//主机名
		console.log(window.location.hostname);

		//文件的路径---相对路径
		console.log(window.location.pathname);

		//端口号
		console.log(window.location.port);

		//协议
		console.log(window.location.protocol);

		//搜索的内容
		console.log(window.location.search);
	
		//设置跳转的页面的地址
		//location.href="http://www.jd.com";//属性----------------->必须记住

		//location.assign("http://www.jd.com");//方法  设置跳转的页面地址

		//location.reload();//重新加载--刷新

		//location.replace("http://www.jd.com");//没有历史记录 设置跳转的页面地址，而且没有浏览记录，就是无法点击返回键返回

history对象

	 window.history.forward();//前进
	 window.history.back();//后退

navigator对象
	
	window.navigator.platform；//获取浏览器所在的平台类型 比如 Android、window、ios

定时器

	let timeId=setInterval(fun, time);//每隔time事件执行一次fun事件,返回值：一个定时器id，可以通过该id关闭该定时器
	关闭定时器   window.clearInterval(timeId);

	


	

	



	

		 
		  
		  
		  
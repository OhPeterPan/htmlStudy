注：<hr>一条横线

# Css概念 #

	层叠样式表或者级联样式表
	
	美化Html结构，相当于页面化妆

# 选择器 #
	选择器{
		属性值：值;
		}
	选择谁的过程，选择标签给他们添加样式(选择一个或者一类标签给他们添加样式)

	常用属性
		width:20px;
		height:200px;
		background-color:red;  背景颜色
		font-size:24px;        文字大小
		text-align:left|center|right  内容的水平对齐方式
		text-indent:2em;       首行缩进
		color:red;             文字颜色
	
	css颜色的表现形式
		1、直接写颜色的名称  red prink blue
		2、16进制显示颜色
		3、rgb(255,255,255) 0~255
		4、rgba  alpha 不透明度(0~1)

	基础选择器
	
		1、标签选择器    标签{属性：值;} 选择所有的标签给他们赋予样式

		2、类选择器(非常重要)
			写法： .自定义类名{属性：值;}
			特点：谁调用谁生效  
				 给标签定义class="xx xx1...."匹配多个选择器 中间使用空格隔开  一个标签可以使用多个类选择器
				 多个标签可以使用同一个选择器
       		命名方式：
				1、不能用纯数字或者数字开头定义类名
				2、不能使用特殊符号或者开头定义类名(_除外)
				3、不建议使用汉字定义类名
				4、不建议使用使用属性以及值定义类名

		3、id选择器
			写法： #自定义名称{属性：值;}
			特点：一个ID选择器一个界面只能使用一次，如果使用2次以及以上不符合w3c标准  JS调用会出问题 
				 一个标签只能调用一个ID选择器
				 一个标签可以即调用ID选择器又可以调用class选择器

		4、通配符选择器(不推荐使用)
			*{属性:值;}  给所有元素用上样式


	复合选择器
		概念：两个或者两个以上的基础选择器通过不同的方式连接在一起
		
		1、交集选择器
			标签+类(ID)选择器 {属性：值;}  既满足标签又满足有类(ID)名就可以匹配成功
			示例：div.box 标签加类选择器    div#miss   标签加ID

		2、后代选择器(重点的重点)  根据浏览器解析顺序来看待本质
			选择器+空格+选择器...{属性:值;}  <div><p><span>XXXX</span></p></div>  div p{}    div span{}  均可以生效
			特点：
				无限制隔代
				只要能代表标签，不管是类选择器还是ID选择器都可以自由组合  

		3、子代选择器
			选择器>选择器{属性：值;}  只能选择标签的直接子标签   <div><p><span></span></p>    <span></span></div>
			div>span   p标签里面的不会被选中
			选中的是直接子元素】、

		4、并集选择器
			把所有样式相同的选择器或者标签全部使用逗号连接在一起
			写法：
				选择器,选择器,选择器,选择器{属性:值;}

文本属性以及属性连写
	font-size:20px;             文字大小
	font-weight:20;             文字粗细 100~900  从700开始加粗  推荐使用数字，不推荐bold
	font-family:微软雅黑;        文字字体
	font-style:normal|italic;   文字风格  normal默认值    italic倾斜
	line-height:40px            行高

	属性连写	示例：font:italic  700 16px/行高  微软雅黑;  需要按照顺序来，否则可能会出错
			文字大小与字体为必写项

文字(字体)的表达方式
	font-family:xx;  
		使用：1、直接使用中文名称   比如  微软雅黑
			 2、字体的英文名称
			 3、Unicode编码
	使用浏览器调试桥(f12) 选择console  输入escape("字体") 得到Unicode编码

# 样式表的书写位置 #
	1、内嵌式  <head>
				<style type="text/css"></style>  样式只在本页面实现  没有真正实现结构与表现分离
				</head>

	2、外联式  <link rel="stylesheet" type="text/css" href="样式表路径">  </link>  用的最多  真正实现结构与表现分离

	3、行内样式表(stylesheet)  示例<h1 style="font-size: 30;color: red;"></h1>  用的最少

# 标签分类(显示方式) #
	1、块元素   div  h1~h6   p   ul,li....
		特点   独占一行  可以定义宽高  嵌套或者包含下，子块元素没有定义的情况下，默认宽度是父块宽度

	2、行内元素 span  a   strong(文本加粗)   em(文字倾斜)   del(删除线)   ins下划线
		特点    在一行上显示  定义宽高无效  可以定义左右的内外边距  上下的会被忽略掉

	3、行内块元素(内联元素)  input  img
		特点   在一行上显示  可以定义宽高

# 元素之间的转换 #
	块元素转行内元素：   display:inline
	行内元素转块元素：   display:block

	块和行内元素转行内块元素(常用)：display:inline-block

# CSS 3大特性 #
 1、样式表之层叠性
	当多个选择器作用到同一个标签时，最后出现的会覆盖前边的(跟浏览器解析的顺序有关)

 2、样式表之继承性
	元素有包含关系时，样式表具有继承性(并不是所有的标签继承)
		文字颜色可以继承
		文字大小可以继承
		文字字体可以继承
		字体粗体可以继承
		文字风格可以继承
		文字行高可以继承   总结：文字的所有特性都可以继承

		特殊情况：h系列不能继承文字字体大小，但是可以根据继承文字的大小浏览器自动去给一个缩放值
				 a标签不能继承文字颜色

 3、样式表之优先级
	默认样式表<标签选择器<类选择器<ID选择器<行内样式表<br>

	对应权重：0 1，10，100，1000，1000以上  对应下边的权重叠加

	
	使用!important 可以将选择器的属性的优先级提到最高   示例： font-size:20px !important;

	继承得来的选择器权重为0

	优先级之权重会叠加  

# 链接伪类 #
	a:link{属性：值;}		链接的默认状态
	a:visited{属性:值;}   	链接访问之后的状态
	a:hover{属性:值;}		鼠标放在连接上面的状态
	a:active{属性:值;}		链接激活的状态	
	注：如果四个一块使用，需要按顺序书写
	 :focus{属性:值;}		获取焦点的状态

	文本修饰：
		text-decoration:none|underline(下划线)|line-through(删除线)
	
背景属性
	background-image:url("图片位置")  背景图片
	background-repeat:repeat|no-repeat|repeat-y|repeat-x

	background-position:left|right|center|top|bottom|具体数值  背景定位
	{ 1、方位值只写一个的时候，默认会加上居中位置、
	  2、写两个方位值的时候，顺序无要求	
	  3、写两个具体值的时候，第一个值代表水平方向，第二个值代表垂直方向
		 }

	background-attachment:scroll(这个是相对于你设置的盒子)|fixed(这个是相对于浏览器的)  是否滚动
	
	属性连写(示例)： background:red url("") 没有顺序要求  url为必写项

行高定义(line-height)
	浏览器默认文字大小：16px

	行高是基线到基线之间的距离

	行高=文字高度加上下边距
	一行文字行高和父元素高度一致的时候文字可以垂直居中显示

行高的单位  (下边都是以文字20px为基准)
	<table>
    <tr>
        <td>单位</td>
	    <td>文字大小</td>
	    <td>值</td>
	  
    </tr>
 <tr>
        <td>px</td>
	    <td>20px</td>
	    <td>20px</td>
    </tr>
<tr>
        <td>em</td>
	    <td>20px</td>
	    <td>40px</td>
	  
    </tr>
<tr>
        <td>%</td>
	    <td>20px</td>
	    <td>20px*百分比</td>
	  
    </tr>
<tr>
        <td>2</td>
	    <td>20px</td>
	    <td>40px*2</td>
	  
    </tr>
</table>

	总结:单位除像素以外，行高都是与文字大小乘积
	
	从父类继承行高，不带单位的行高是跟子元素文字大小相乘 其他的都是与父元素文字大小相乘

盒子模型(三部分组成：边框、内边距、外边距)
	1、边框 (以上边距为例)
		border-top-style:none(无)|solid(实线)|dashed(虚线)|dotted(点线)	盒子样式
		border-top-color:												边框颜色
		border-top-width:												边框宽度
	简写
		border-top:red solid 5px										边框属性连写(style不能少)
	四个边框值相同时
		border:xx xx xx;												四个边框相同的写法(style不能少)
	
	2、边框合并 border-collapse:collapse

	注：	border:0 none  去除边框，这样使用兼容性很好
		outline-style:none  去除轮廓线(就是input点击的那个轮廓线)
		<label for="要绑定的标签ID"></label>  友好性  label  for ID   获取光标焦点

内边距
	padding-left、padding-right、padding-top、padding-bottom
	连写：	padding:20px;一个值的时候都是20   上右下左
			padding:20px 30px;  上下20	左右30
			padding:20px 30px 40px; 上20  左右30   下40
			padding:20px 30px 40px 50px;  上右下左一一对应	 

内边距影响盒子大小(跟Android很类似) 内边距会撑大盒子   border的宽度也会影响盒子的大小

继承的盒子一般不会被撑大
	包含(嵌套)的盒子，如果子盒子没有设置宽度，如果给子盒子设置左右内边距，如果内边距小于父盒子的宽度，就不会撑大盒子

外边距  连写什么的与padding一模一样

垂直方向外边距合并、外边距塌陷
	外边距合并：外边距会用大的直接包括小的(只有垂直方向)
		          .one{
                width: 20px;
                background: orange;
                height: 20px;
                margin-bottom: 20px;
            }
                  .two{
                    background: #eee;
                width: 20px;
                height: 20px;
          margin-top: 100px;
            }

	one和two的实际距离是100px；

	外边距塌陷：
		潜逃的盒子直接给子盒子设置垂直方向外边距的时候会发生外边距塌陷(父元素会被带下来)
	解决方法：
		1、给父盒子设置边框  				不推荐使用
		2、给父盒子设置overflow:hidden;	推荐这个
	
fireworks的简单使用
	ctrl+n  		新建文件
	ctrl+o  		打开文件
	ctrl+alt+r		调出和隐藏标尺
	清除辅助线		
	z 				放大镜
	alt+鼠标左键		放大镜状态下缩小  
	空格				抓手工具
	拉出来两个辅助线->切换到光标工具->将光标放到辅助线之间->按住shift键测量出距离


	
	
	
	
		
	
			

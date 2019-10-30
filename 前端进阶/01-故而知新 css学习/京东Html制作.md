1、搭建项目架构
	
	HTML文件夹  核心文件
	CSS文件夹   控制样式
		a、base.css 基础样式    b、global.css 全局样式
	Image      图片
	JS         音视频文件...  做动态效果

webstrom

获取网站的小图标

	网址+"\favicon.ico"  示例:https://www.baidu.com/favicon.ico 获取百度的小图标

	内容一致性原则  划分盒子区域  

	划分盒子：从上到下，从左到右

	font-weight:normal   加粗变正常
	font-style:normal    倾斜变正常
	text-decoration:none 文字下划线或者删除线变正常
	outline-style:none   去除input蓝色外边框
	resize:none          禁止文本框拖拽

文字居中

	text-align:center  有点小问题，只居中 少用
	pading-left/right  使用内边距挤挤
	定位、margin...

京东网页制作注意事项

	子盒子不能与静态定位定位，只能根据absolute，relative，fix定位

	蛋糕理论 先写普通标签->再写特别标签->最后写更特别的标签   先易后难  蛋糕理论

	尽量避免代码污染

	padding没有负值

	属性权限问题   css之优先级的内容

	选择器一般不超过3个

	模拟鼠标：
		cursor:pointer  变成小手
		cursor:text     变成光标
		cursor:move     变成到四个箭头的光标
		cursor:default  变成箭头

	盒子的稳定性
		设置宽高(盒子剩余法)
		设置padding；padding只有背景颜色，不能有内边距
		设置margin，但是可能会造成盒子塌陷，谨慎使用

	制作logo时，内部需要加上一个文字，为了seo优化，设置首行缩进

	圆角 border-radius:左上 右上 右下 左下;
		取值：a、宽高的一半
			 b、百分比
			 c、em
			 d、左上 右上 右下 左下;  具体数值

	同一个父盒子的元素要么都设置浮动，要么都不设置浮动，否则容易出bug

	行高也可以撑开盒子

	盒子的位置由定位决定。文字的位置由行高决定

	给html同级别相邻的盒子设置浮动会顶对齐

	标准流盒子中的文字不会被浮动的盒子给遮挡住

	清除浮动
		1、clear:both；
		2、overflow:hidden 
		3、单伪元素/双伪元素
			单伪元素：
				.clearfix:after{
				content:".";
				display:block;
				height:0;
				visibility: hidden;
				line-height:0;
				clear:both
				} 
				
				//兼容ie浏览器
				.clearfix{
				zoom:1;
				}
			双伪元素：
				.clearfix:after,.clearfix:before{
				content:".";
				display:table;
				} 
				
				.clearfix:after{
				clear:both;
				}
				//兼容ie浏览器
				.clearfix{
				zoom:1;
				}

	margin与padding使用规则：
		1、需要使用背景图的时候必须使用padding  margin会把背景图也给顶跑了，padding不会
		2、使用margin会出现外观塌陷时使用padding

	层级： 就是谁在上面
		1、必须有定位  除了stand都行，也就是除了默认定位都可以
		2、z-index:x;  x为数字，越小层级越高

	盒子的高被撑开与撑破是两回事  
	撑开表示盒子变成那么大了  没有设置盒子高度撑开
	撑破表示盒子还是那么大，但是内容撑破了它的高度  盒子设置高度但是内容却超过它的高度

	浮动的盒子相互影响，不管是否在同一个盒子中

	决定是否使用 ul>li>a 就要看此处的功能是否需要很强大  不强大就直接使用a标签就可以

	块元素可以继承父盒子的宽高

	浮动的盒子尽量给宽高

	浮动的盒子里面包含文字时最好给宽高，要不然缩放页面会掉下来
	
	a标签  href="";//啥都不写刷新页面
          href="#";//跳转到页面最顶端
		  href="javascript:void(0)"// 关闭a标签的跳转
		  href="javascript:;"// 关闭a标签的跳转

	定位的情况下，right没有left的权限高

	半透明
		opacity : 0.4; 半透明  内部文字的透明度也会改变

	父盒子设置行高之后，行内元素尽量不要使用font设置行高

	table表格一般用于承载文字

	标准流盒子被浮动的盒子压住，浮动的盒子又被定位的压住  和占不占位置都无关

	使用z-index 调整层级  为0比浮动和标准流的盒子高    为负数比浮动和标准流的层级低

	背景图无法撑开盒子 行高可以撑开盒子 高度也可以撑开盒子

	绝对定位不占据位置
	
盒子层级问题

	用法：1、必须有定位  2、设置z-index  不给默认为0  为0的盒子也比浮动和标准流的盒子高    为负数比浮动和标准流的层级低
	

	
		  
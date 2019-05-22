渲染引擎的不同导致兼容性问题

seo搜索引擎优化

Html结构标准：
	<!DOCTYPE html>//声明文档类型
	<html>//根标签
	<head>//头部标签
    <title>//标题标签
        
    </title>
	</head>
	<body>//主体标签

	</body>
	</html>

html标签关系分类：
		包含关系、并列关系
	包含关系(父子)：
			<head>//头部标签
    <title>//标题标签
        
    </title>
	</head>

	并列关系(兄弟姐妹):
	<head><head/><body><body/>

sublime常用快捷键:
	tab:补全标签代码
	ctrl+shift+d:快速复制一行
	ctrl+shift+k:快速复制一行
	ctrl+shift+s:另存为
	ctrl+鼠标左键单击:多行选中
	ctrl+h:查找替换
	ctrl+f:只查找
	ctrl+/:注释
	ctrl+L:快速选中一行
	ctrl+shift+上线箭头:向上或者向下移动
	f11:全屏来回切换

html单标签：
	<br/>换行标签
	<hr/>水平线标签

html双标签：
	<p></p>:段落标签  每对段落标签都会自动上下生成空白行
	<h1></h1>...<h6></h6>:标题标签 数字越大显示字体越小
	<h1></h1>：一个页面里面只能出现一次
	<font></font>:文本标签

文本格式化标签：
	<strong></strong>:文本加粗 工作中尽量使用这个标签
	<b></b>          :文本加粗
	<em></em>(i标签也是 但是工作中尽量不用这个):文字倾斜
	<del></del>(s  尽量用del)：删除线标签
	<ins></ins>(u 尽量用ins)：下划线标签
	2<sup>3</sup> 2的3次方
	h<sub>2</sub>0  h2o 下标
	推荐的标签是因为更有浏览器中更有语义化
	
	<img src="wk.jpg" title="悟空" alt="这里应该是悟空">
	title :鼠标放上去显示的图片
	alt: 替换文本 图片加载失败的时候显示的文字
	当只写宽或者高的时候 图片会等比例缩放

	http开头的都是绝对路径

超链接
  	<a href="img.html" title="图片标签" target="_blank">heheh</a>
		href：连接的地址
		target：_self  自身打开  _blank开启新页面打开
		title：鼠标放在连接上显示的文字
锚链接
	1、定义锚点
	<p id="sd">....</p>
	2、超链接到锚点：
		<a helf="#sd">...</a>

空链 
			<a helf="#">...</a>  当不知道链接路径的时候会用到空链
压缩文件下载
			<a helf="压缩文件的路径">...</a> 不推荐使用
超链接的优化写法
			<head>
			<base target="_blank">  让所有超链接都在新窗口打开
			</head>
特殊符号
		空格 &nbsp;   
		<   &lt;
		>   &gt;
		&   &amp;		
		￥  &yen; 
列表
	无序列表
	   <ul type="square">//square  方块  disc 实心小圆圈    circle 空心小圆圈
		<li></li>//列表项
		<li></li>
		<li></li>
		<li></li>
		</ul>

	有序列表
		<ol type="1" start = "3">  //start决定开始的位置
		<li></li>//列表项  会按照重要性等排序
		<li></li>
		<li></li>
		<li></li>
		</ol>

	自定义列表
		<dl>
			<dt></dt>//小标题
			<dd></dd>//解释标题 可以有无数个
			<dd></dd>
			<dd></dd>
			<dd></dd>
			<dd></dd>
		</dl>
音乐标签
	<embed sec="" hidden=true></embed>
滚动
	<marquee behavior="" direction=""></marquee>
	behavior 滚动的方式
	direction 滚动的方向

meta标签和link标签
	！+tab  h5的标签结构
	1、<meta charset="utf-8">  utf-8通用字符集
	2、<meta name="keywords" content="...">  关键字 给搜索引擎看的 seo优化
	3、网页描述
		<meta name="description" content="...">浏览器可以直接显示出来
	4、网页重定向
		<meta http-equiv="refresh" content="5;http://www.baidu.com">  5秒后去百度


link标签:
	<link rel="stylesheet" href="xx.css">  链接外部样式表文件
	<link rel="icon" href="xx.icon">  标签旁边的图片显示

表格行与列
	对网页重构的一个有益补充  n行n列
	<table >
		<tr>
			<td></td>...<td></td>
		</tr>

		<tr>
			<td></td>...<td></td>
		</tr>
			...
			<tr>
			<td></td>...<td></td>
		</tr>
		</table>
	


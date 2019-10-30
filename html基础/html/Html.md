渲染引擎的不同导致兼容性问题

seo搜索引擎优化

HTML  超文本标记语言    是一门结构化语言

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
	ctrl+shift+k:快速删除一行
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

表头与单元格合并
	<table border="1" width="500"  height="300" align="center" >
	<caption>表头</caption>    caption 表头
	    <tr>
	        <td colspan="2">张三</td>   colspan  同行的列合并   rowspan  同列的行合并
	        <!-- <td>23</td> -->
	        <td>前端工程师</td>
	    </tr>
	    <tr>
	        <td></td>
	        <td></td>
	        <td rowspan="2"></td>
	    </tr>
	    <tr>
	        <td></td>
	        <td></td>
	        <!-- <td></td> -->
	    </tr>
	</table>
表格的标题、内容垂直对齐方式、边框颜色
	表格的标题  
<th></th>
	<table border="2" width="500" height="300" bordercolor="red" cellpadding="0"> cellpadding 边框内文字与边框的距离
    <tr >									   边框颜色
        <th>姓名</th>                                         
        <th>年龄</th>
        <th>职位</th>
    </tr>
    <tr>
        <td valign="bottom">张三</td>      valign 表格内字体所在边框的位置
        <td>23</td>
        <td>前端工程师</td>
    </tr>
    <tr>
        <td>张三</td>
        <td>23</td>
        <td>前端工程师</td>
    </tr>
	</table>

细线表格  实现思路：将table的背景变色  然后给每个td加上背景就可以得到

表单提交 文本输入框、密码输入框、单选框
	<form action="1.php"></form>  action用来处理信息

	<form action="1.php" method="post">
    用户名：<input type="text"  maxlength="6"(最大长度)  readonly="readonly"(只读) disabled="disabled"(未激活状态) name="username"(给这个输入框取个名字) value="默认值"(值，此值将传给处理文件)/><br/>
    密码：<input type="password"/><br/>
    <input type="submit"/>
	</form>

	文本输入框 <input type="text"  maxlength="6"(最大长度)  readonly="readonly"(只读) disabled="disabled"(未激活状态) name="username"(给这个输入框取个名字) value="默认值"(值，此值将传给处理文件)/>
	密码输入框 <input type="password"/><br/>

	单选 <input type="radio" checked="checked" name="gender">男</input> 
		 <input type="radio"  name="gender">女</input>
		只有当name相同时才能实现单选功能

下拉列表
	    <select>
        <option>呵呵呵</option>
        <option>哈哈哈哈</option>
        <option>得得得得</option>
    </select>

    <select  multiple="multiple">   //多选
        <option>郑州市</option>
        <option>商丘市</option>
        <option selected="selected">洛阳市</option>  //selected 设置默认选中项
    </select>
	
 	分组显示
	  <select  > 
      <optgroup label="河南省">
        <option>郑州市</option>
        <option>商丘市</option>
        <option >洛阳市</option>
        </optgroup>
           <optgroup label="北京市">
        <option>朝阳区</option>
        <option>大兴区</option>
        <option >昌平区</option>
        </optgroup>
    </select>

多选框、按钮、信息分组
	<form action="1.php" method="get">
	<!-- 表达信息分组 -->
	    <fieldset>
	        <legnd>表单头部信息</legend>
	<input type="checkbox">打篮球</input>
	<input type="checkbox">吃冰淇淋</input>
	<input type="checkbox">唱歌</input>
	<br>
	<textarea cols="300" rows="20"></textarea><br>
	
	<!-- 上传文件 -->
	<input type="file"></input><br>
	
	<!-- 可以提交信息 -->
	<input type="image" src="swk.jpg"></input><br>
	
	<!-- 可以提交信息 -->
	<input type="submit"></input><br>
	
	<!-- 普通按钮，不能提交信息 -->
	<input type="button" value="普通按钮"></input><br>
	
	<!-- 重置按钮 -->
	<input type="reset"></input>
	    </fieldset>
	</form>

h5表单控件
	<form action="1.php" method="post">
    <!-- 网址标签 -->
    <input type="url"></input><br>
	<!-- 日期标签 -->
	    <input type="date"></input><br>
	<!-- 时间标签 -->
	        <input type="time"></input><br>
	<!-- 邮箱标签 -->
	            <input type="email"></input><br>
	
	    <input type="submit"></input>
	</form>

标签语义化(seo优化 把样式去了之后整体感觉还是很不错  尽量少用无意义的标签  比如div与span)
	
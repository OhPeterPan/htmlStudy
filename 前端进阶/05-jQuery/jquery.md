#jQuery
	javascript库
	
	顶级对象 jQuery或者$

##jquery页面加载事件
	1.$(window).load(fun)  页面上很多元素加载后才能执行
	2.$(document).ready(fun)  页面基本元素加载之后执行
	3.jQuery(fun)          页面基本元素加载之后执行
	4.$(fun)               常用  页面基本元素加载之后执行

##jQuery各种选择器
	1. 标签选择器   
	2. 类选择器  .类名
	3. id选择器  #id名
	4. 通配符选择器 *

	5. 交集选择器  标签.类名
	6. 并集选择器  $("选择器1，,选择器2.....")

	7. 索引选择器 $("选择器:eq(索引的值)")
	8. 奇数选择器 $("选择器:odd")
	9. 偶数选择器 $("选择器:even")
	10. 筛选器	$("选择器:lt(索引)") 小于这个索引的元素
				$("选择器:gt(索引)") 大于这个索引的元素

	11. $("选择器:last") 最后一个元素 
	12. $("选择器:first") 第一个元素

	13. 当前元素.next(); 获取下一个兄弟元素
	14. 当前元素.nextAll(); 获取后面的所有兄弟元素
	15. 当前元素.prev(); 获取上一个兄弟元素
	16. 当前元素.prevAll(); 获取上面的所有兄弟元素
	17. 当前元素.siblings(); 获取所有的兄弟元素
	18. 当前元素.parent();   获取父级元素
	19. 当前元素.children(); 获取所有的子元素(直接子元素)
	20. 当前元素.find("选择器") 获取一个或者多个元素

	21. val(); 获取表单标签元素属性value的值 也就可以设置表单标签的值，设置下拉列表的选中
	22. text();获取标签中间的值
	23. html(); 相当于innerHtml
	24. .css(); 填充样式  可以直接传json格式的属性键值对，或者就是.css("属性",值)....
	25. .addClass(); 添加类样式
	26. .removeClass();清除类样式
	27. .hasClass(); 判断是否包含某个类样式
	28. .index();  获取元素的索引

	---动画相关--- 一般都是两个参数 参数一：时间   参数二：回调函数
	29. .show();  显示
	30. .hide();  隐藏
	31. .stop()   停止
	32. .animate(json属性对象,持续时间,回调函数);
	33. .slideUp(); 滑入
	34. .slideDown();滑出
	35. .fadeIn();  淡入
	36. .fadeOut(); 淡出
	37. .fadeToggle(); 淡入淡出互相切换
	38. .fadeTo(时间，值);
	
	-----元素的创建和追加-----
	39. $("html代码")；创建元素
	40. 父级元素.append(元素); 被动添加
	41. 子元素.appendTo(父级元素); 主动添加
	42. prepend prependTo 在所选元素的最前面插入元素(是子元素)
	43. before  所选元素的前面插入元素  成为其兄弟元素
	44. after   所选元素的后面插入元素  成为其兄弟元素
	45. clone(); 元素的克隆
	46. 父级元素.append("别的元素的子元素"); 此时相当于把别的元素的子元素剪切到该父级元素
	
	-----移除子集元素-----
	47. 元素.empty();  清空所有子元素
	48. 元素.html(""); 清空所有的子元素
	49. 元素.remove(); 自杀，连自己都清除了
	
	-----自定义属性----- 
	50. attr("属性",值);   设置属性
	51. removeAttr("属性"); 移除这个自定义属性
	52. attr("属性")   获取属性的值  元素的选中不要使用这个方法
	53. prop("checked"); 获取选中状态
	54. prop("checked",bool) 设置选中状态
	
	-----元素的属性操作-----
	55. .width();  获取宽度，不带padding和border  获取到的只是数值，不带px
	56. .height();  获取高度     加参数代表设置
	57. .offset();  获取到的是一个对象  包含left和top   这里面的数值均含有margin
	58. .offset({"left":100,"top":100}); 设置left和top
	59. .scrollTop();  向上卷曲的距离
	60. .scrollLeft(); 向左卷曲的位置
	
	-----jQuery事件操作相关-----
	61. .事件(fun);  绑定事件
	62. .bind("事件",fun)
	63. 父元素.delegate("子元素","事件",fun);  父元素委托子元素绑定事件
	64. .on("事件","子元素",fun); delegate内部实现
	65. 对象.unbind();
	66. 对象.undelegate(); 
	67. 对象.off();解绑
	68. 对象.length；  判断对象是否存在
	69. $符号被占用  使用 $.noConflict()释放给其他人这个权限
        let xy=$.noConflict();  xy就相当于$了  或者使用jQuery

###事件参数的几个属性
	   $("#btn").click(function (e) {
            console.dir(e.target);
            console.dir(e.currentTarget);//获取的是触发事件的当前对象  无视事件冒泡
            console.dir(e.delegateTarget);//获取的是代理的这个事件的对象
        });
     
 
	


 	

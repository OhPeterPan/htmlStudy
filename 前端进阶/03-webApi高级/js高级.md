原型

	构造函数中有一个prototype属性，是一个原型对象
	
	实例对象、构造函数、原型对象

	实例对象中的_proto_属性，叫原型，也是一个对象，是给浏览器使用的，不是标准的属性---可以叫原型对象
	构造函数中的prototype属性，叫原型，也是一个对象，给程序员使用-------------------也是原型对象

	实例对象中的_proto_与prototype这个属性是相等的
	又由于示例对象是由构造函数实例化出来的，因此，实例对象中的_proto_属性指向构造函数里面的prototype这个属性

原型对象作用

	1、数据共享，节省内存空间
	2、实现继承

原型链

	判断一个变量是否是对象---->是否含有_proto_

	实例对象与原型对象之间的关系，主要通过_proto_和prototype来实现

	原型的指向是可以改变的，所以js中通过原型指向的改变来实现继承

	原型链：以Person为例：
		Person实例对象的_proto_---->Person构造器prototype的_proto_----->Object prototype的_proto_(此时为null)

继承

	1、原型继承：把构造函数中prototype指向改变为其它的对象，就可以使用该对象的成员了

	2、借用构造函数实现继承  构造函数名字.call(当前对象，属性,属性,属性.....);缺点是不能使用原型对象中的方法

	3、组合继承  原型继承+借用构造函数继承  二者优点合二为一

	4、拷贝继承  把一个对象里面的方法和属性直接拷贝到另外一个对象里
	  实例：
		    function Person() {
		    }
		    Person.prototype.age=10;
		    Person.prototype.sex="男";
		    Person.prototype.height=100;
		    Person.prototype.play=function () {
		      console.log("玩的好开心");
		    };
		    var obj2={};
		    //Person的构造中有原型prototype,prototype就是一个对象,那么里面,age,sex,height,play都是该对象中的属性或者方法
		
		    for(var key in Person.prototype){
		      obj2[key]=Person.prototype[key];
		    }
		    console.dir(obj2);
		    obj2.play();

	
函数相关

	函数表达式和函数声明
	
	函数也是一种类型 Function类型，所以也是对象

apply和call方法的作用

	改变this的指向

	这两个是方法的调用方式，改变函数作用域的this指向

	方法名字/函数名字.apply(对象obj，实参数组);将函数内部this指向改为对象obj
	方法名字/函数名字.call(对象obj,实参可变长度...);效果一样，就是传参方式不同

	当两个方法不传任何参数或者传一个null时，代表内部的this是window对象

bind方法

	call和apply方法是函数调用的时候改变this的指向
	bind是复制一份的时候改变this的指向，有返回值 ，返回值是复制之后的这个方法

函数的几个属性

	示例：function f1(){
			console.log(f1.name);//函数名字
			console.log(f1.arguments.length);//实参的个数
			console.log(f1.length);//形参的个数
			console.log(f1.caller);//该函数的调用者对象(比如在f2函数里被调用，则这里就是f2函数对象)
			}

作用域以及作用域链以及预解析

		作用域链：变量的调用，从里到外一级一级的寻找，找到了就直接使用
		预解析：表示浏览器在解析代码之前，会将变量的声明以及函数的定义提前到该作用域的最前边

闭包

	模式：函数模式的闭包，对象模式的闭包
	作用缓存数据，延长作用域链
	优点和缺点：缓存数据

	函数模式的闭包：一个函数里还有一个函数 
	对象模式的闭包：一个函数中含有一个对象、

	这里应用的是一个点赞获取点赞个数的小案例  js高级第四天

沙箱  一个模拟的运行环境  互不干涉

递归  函数自己调用自己  需要有一个结束条件

深拷贝与浅拷贝

	浅拷贝：很类似于拷贝继承
	深拷贝：利用递归将一个对象拷贝到另外一个对象中


# 概念
	页面与数据之间的交互
	构建用户界面的渐进式框架
	 m v vm 中的vm工具，连接m层与v层的工具类
# cdn
	内容分发网络

# 插值
	文本差值 标签放进去也是文本 不显示标签的含义

# 指令
	v-开头  做一些操作

	v-bind:标签属性 = Vue中data的属性(字符串类型)

	v-model:value='xxxx'  vue与dom数据之间相互影响
	v-model='xxx' 标签之间填充
	v-model.xxx  修饰符 lazy：input失去焦点事件  number:转换为数字类型   trim：去除空格

	v-on：JS事件(不带on)="function(#event)"  绑定事件监听器    $event 写死的表示事件的MotionEvent对象
	修饰符： prevent 阻止浏览器的默认事件

	两个事件同时使用  示例：@click.ctrl 按住ctrl键才能点击

	v-show = "xxx(data中的数据)" 标签是否显示  使用的是css中的display来表示显示或者隐藏

	v-if/v-else/v-else-if   v-if = "data中的属性"

	v-for ="v in array"  循环  

	v-cloak  当成一个属性使用

	v-once   data的属性只能使用一次 

	自调用匿名函数的最大的用处就是封装作用域

## 计算属性
	computed:{} 与 Methods 的区别
		只有数据变化的时候才会执行里面的方法

	使用计算属性时，属性名字与computed中的方法名一直，不能加括号，因为获取的值就是computed中的属性值

	computed中的方法执行时会把方法的结果放入到与该方法名字一致的属性中，以供模板使用

## 侦听器
	data:{
		data1:'',
		data2:'',
		}
	watch:{
		data1:function(newVal,oldVal){
			},
		
		data2:function(newVal,oldVal){}
		}

	data中属性的值发生改变时，会把新值和老值都给你

	作用：当数据变化时需要执行异步操作，可以使用侦听器

## ref操作节点
	标签中：ref="dv"  this.$ref.dv获取标签对象

	尽量不要使用这个方式，因为违反mvvm原则

## 过滤器
	示例：
		<div id="dv">{{msg|myFilter}}</div>
		<script>
		    new Vue({
		        el: '#dv',
		        data: {msg: "abcdefg"},
		        filters: {
		            myFilter(val) {
		                return val.toUpperCase();
		            }
		        }
		    });
		</script>

	全局过滤器：
		示例：    Vue.filter('number', (val) => {  
			        var reg = /[0-5]/g;
			        return val.replace(reg, '6');
			    });

## 自定义指令
	示例: 定义一个全局自定义指令     directive指令
		<div id="dv" v-haha>我是一个div</div>
		<script>
		    Vue.directive('haha', {
		        inserted: (el) => {
		            el.style.color = 'red';//文字颜色变为红色
		        }
		    });
		    var app = new Vue({
		        el: '#dv',
		        data: {}
		    });
		</script>

	定义局部指令
		directives:{
			name:{
				  inserted: (el) => {
		            el.style.color = 'red';//文字颜色变为红色
		        	}
				}
			}

## 自定义指令传值

	示例:
	<div id="dv" v-colored="colors">我是一个div</div>
	<script>
	
	    var app = new Vue({
	        el: '#dv',
	        data: {
	            colors: 'yellow'
	        },
	        directives: {
	            colored: {
	                inserted: (el, val) => {
	                    //console.log(val.value);
	                    el.style.color = val.value;
	                }
	            }
	        }
	    });

## 动画以及过渡
	opacity隐藏显示的过渡效果

	下边的v可以使用transition时定义一个name替换：
		v-enter:定义动画从无到有开始的参数
		v-leave-active:定义过渡的属性以及时间参数
		v-enter-to:定义动画从无到有结束的状态
	
		v-leave: 定义动画从有到无开始的状态
		v-leave-active:定义过渡的属性以及时间参数
		v-leave-to:定义动画从有到无结束的参数

	示例：
		    <style type="text/css">
	        .fade-leave {
	            opacity: 1;
	        }
	
	        .fade-leave-active {
	            transition: opacity 1s;
	        }
	
	        .fade-leave-to {
	            opacity: 0;
	        }
	
	        .fade-enter {
	            opacity: 0;
	        }
	
	        .fade-enter-active {
	            transition: opacity 3s;
	        }
	
	        .fade-enter-to {
	            opacity: 1;
	        }
	
	    </style>
		</head>
		<body>
		
		<script src="vue.js">
		
		</script>
		
		<div id="dv">
		    <input value="按钮" id="btn" type="button" @click="go"/>
		    <transition name="fade">
		        <p v-show="is">哈哈哈</p>
		    </transition>
		</div>
		<script>
		    var app = new Vue({
		        el: '#dv',
		        data: {
		            is: true,
		        },
		        methods: {
		            go() {
		                this.is = !this.is;
		            }
		        }
		    });
		</script>

## json-server
	本地提供数据  npm install json-server 
	常用命令：json-server --watch db.json 选用db.json文件作为服务器提供者

	JSON.stringify(data)//转成string格式的数据

## axios的使用
	提供一个连接网络的功能
	axios.get()/azios.put()/axios.delete().....

## 组件
	全局组件：Vue.component("组件名字",{template:'<html标签>'});   相当于是创造了一个新标签

	Vue.component('button-counter', {
		  data: function () {
		    return {
		      count: 0
		    }
		  },
		  template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
		})

		
	局部组件：components:{'组件名字':{template:'<html标签>'}};
	组件名字使用驼峰式命名时 -----  ps:'myZujian' => my-zujian

	组件中template中 有且必须有一个根节点

	这对于Vue这个父组件来说，自定义的算是子组件，每个组件都有自己独有的作用域
	子组件中的data必须是一个方法

	vue对象也是一个组件，如果里面包含template，那么会替换 el 选中的节点

	组件传值示例
		<myzujian v-bind:cc="msg"></myzujian>//这用使用传值成功
		var app=new Vue({
			el:'app',
	
				data:{
						msg:'哈哈哈'
					},

			components:{
			myzujian:{
					props:['cc'],//使用这个属性传值
					template:'<h2>我认为{{cc}}</h2>',
					}
				}
		
			});

## Vue生命周期
	
## 路由组件
	第三方插件 ---- vue-router

	路由组件示例(包括传参)
		<div id="dv">

			<ul>
				<li><a href="#/login">登录</a></li>
				<li><a href="#/register">注册</a></li>
				<li><router-link to="/delete/2">删除</router-link></li>
			</ul>
			<router-view></router-view>
		</div>
		
		<script>
		
			var ro = new VueRouter({
				routes:[
					{ path:'/login',component:{template:'<h1>登录</h1>'} },
					{ path:'/register',component:{template:'<h1>注册</h1>'} },
					{ path:'/delete/:id',component:{template:'<h1>删除{{$route.params.id}}</h1>'} },
				],
			});
		
			var app = new Vue({
				el:'#dv',
				router:ro,
			});
		</script>	

	cli+webpack ---- 项目构建工具  命令行工具
	 -- 使用npm引入  npm install @vue/cli  @vue/cli-init -g(global)
	
	 -- webpack+vue搭建项目  vue init webpack xxx(项目名称)
	
	 -- npm run dev 启动vue项目

	

	
	
	
	
	
	

	


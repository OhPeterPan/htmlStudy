## ES6模块的方式加载模块 
	import xxx from '模块名称(比如：Vue(node-modules文件夹中寻找),或者自定义模块路径)'  编译时输出接口  输出的是值的引用    自动采用严格模式，不管加没加"use strict"   顶层的this指向undefined
 
	commonJS加载模块是在运行时加载   输出的是一个值的拷贝 模块顶层的thid指向当前模块

	ES6导出模块:
	export default{
			name:'模块名称',
		}

	commonJS导出：
		module.exports/export(这个后边需要一个字段 export.字段=xxx)

## 跨域请求
	协议不一致/域名不一致/端口号不一致  满足任何一点就行

	跨域时请求可以发送(请求可以发送，服务器也能接收到请求而且可以返回响应)，但是ajax不接受非本域的数据，所有的数据都用不了

	ajax跨域解决方案：jsonp 同域代理  CORS

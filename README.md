# ES6-learn
## 1、ES6怎么来的
* 	ECMAScript 和 JavaScript
	* ECMA 是标准，JS 是实现
	* ECMAScript 简称 ECMA 或 ES
*	历史版本
	* 1996  ES1.0 Netscape 将 JS 提交给 ECMA 组织，ES 正式出现
	* 1999    ES3.0 被广泛支持
	* 2007.10  ES4.0 过于激进，被废除了
	* 2009.12  ES5.0 ES5.0正式发布，同时公布了javascript.next也就是后来的ES6
	* 2011, ES5.1 成为 ISO 国际标准
	* 2015, ES6.0 正式发布。开始指问ES7.0
	
## 2、ES6兼容性和新特性
*	ES6---IE10++、chrome、Firefox、移动端、NodeJS
* 解决不兼容，编译、转换
	* 在线转换（`<script type="text/babel"></script>`）
	* 提前编译 
* babel==bowser.js

##	 3、变量
* var的问题
	* 可以重复声明
	* 无法限制修改
	* 没有块级作用域 语法块: `{ } `
* let和const
	* 不能重复声明
	* 都是块级作用域，  `{ } `块内声明的，块外无效
	* let是变量，可以修改
	* const是常量，不能修改
*	块级作用域举例
	* 用var结果不对，需要闭包处理
	* 用let最简单，解决作用域问题 

```html

<!DOCTYPE html>
	<html lang="en">
	<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <input type="button" value="按钮1">
    <input type="button" value="按钮2">
    <input type="button" value="按钮3">
    <script>
      window.onload=function(){
        //   var Btn = document.getElementsByTagName('input');
        //   for (var  index = 0; index < Btn.length; index++) {
        //     (function(index){
        //             Btn[index].onclick=function(){
        //             alert(index+1)
        //         }
        //     })(index);
           
        //   }
          let Btn = document.getElementsByTagName('input');
          for (let  index = 0; index < Btn.length; index++) {
            Btn[index].onclick=function(){
            alert(index+1)
           
            }
          }
      }  
    </script>
</body>
</html>

``` 
##	4、函数-箭头函数

* 箭头函数就是函数的简写
	* 如果只有一个参数，`（）`可以省略
	* 如果只有一个`return`, `{}`可以省略 

```
//箭头函数
()=>{}

//普通函数
function name(){}

```

```
let show=()=>{
	alert('abc)
}

let show2 = (a,b)=> {alert(a+b)}

let show3 = a => a*2
```

## 5、函数-参数
*	函数的参数
	* 参数扩展/数组展开（`...args`）
	* 默认参数
	
		```
		function show2(a, b=5, c=8) {
		    console.log(a, b, c)
		}
		show2(12, 3)
		``` 
	* 收集剩余的参数
		* `function show(a,b,...arg){}` 
		* 必须是最后一个
	* 展开数组
		* 展开后的效果，跟直接把数组的内容写在这儿一样的
		
```
	function show(a, b, ...args) {
	    console.log(a)
	    console.log(b)
	    console.log(args)
	}
	console.log(show(12, 34, 22, 45, 55))
	
	
	let arr=[1,2,3]
	let arr2=[4,5,6]

	//...arr
	//1,2,3
	
	let arr3=[...arr,...arr2]
```

##	 6、解构赋值
*	解构赋值
	* 左右两边结构必须一样
	* 左右必须是个东西
	* 声明和赋值不能分开（必须在一句话里完成）
	
	```
	let [a,b,c]=[1,2,3];
	console.log(a, b, c)
	
	let {x, y, z} = {x: 11, y: 22, z: 33}
	console.log(x, y, z)
	
	let [json, arr, num, str] = [{ a: 1, b: 2 }, [1, 2, 	3], 8, 'zxf']
	console.log(json, arr, num, str)
	``` 

## 7、数组
* 新增4个方法
	* map 
	* reducer 
	* filter 
	* forEach
* map映射 
 
 ```
 	let arr=[1,2,3]
	arr.map(item=>item*2)
	
	
	let score = [19, 85, 99, 25,90]
	let result = score.map(item => item >= 60 ? '及格' : '不及格')
	console.log(result)
 ```
 
* reducer 
	* 汇总，一堆出来一个
	* 总数、平均数
	
	```
		//总数
		let arr=[12,56,199,4533]
		arr.reduce((tmp,item,index)=>{
		//tmp 中间结果，item当前数，index次数1开始
			console.log(tmp,item,index);
			return tmp+item
		})
		
		//平均值
		arr.reduce((tmp,item,index)=>{
		if(index!=arr.length-1){
			return tmp + item
			
			}else{
				return(tmp+item)/arr.length
			}
		})
	
	
	``` 
	
* filter 
	* 过滤器
	
	```
	//过滤能被3整除的数
	let arr6=[12,34,56,66,78,44]
	arr6.filter(item=>item%3==0)
	
	//过滤价格大于等于200的
	let arr7=[{
	title:'apple',price:10
	},{
	title:'cloth',price:200
	},{
	title:'bag',price:500
	}]

	arr7.filter(json=>json.price>=200)
	``` 
* forEach
	* 循环（迭代）
	
	```
	
	let arr8 = [12, 4, 8, 9]
	let result8 = arr8.forEach(item => console.log(item))
	let result8 = arr8.forEach((item, index)=>console.log(item, index))
	```

## 8、字符串
* 多了两个新方法
	* startsWith
	* endsWith
	
	 ```
		 let url="http://baidu.com"
		 console.log(url.startsWith('http://'))
		 console.log(url.endsWith('.com'))
	 ```
* 字符串模版 
	* 字符串连接
	* 反单引号
	* 可以折行
	
	```
		let aa=12
		let str = `abc${aa}`;
		console.log(str)//abc12
		
		
		let title = '标题'
		let content = '内容'
		let str4 = `<div>
		<h1>${title}</h1>
		<p>${content}</p>
		</div>
		`
		console.log(str4)
		//<div>
		//<h1>标题</h1>
		//<p>内容</p>
	```
	
## 9、面向对象-基础
* 原来写法
	* 类和构造函数一样
	* 属性和方法分开写的
	
	```
		//原来写法
		function User(name,pass){
			this.name = name;
			this.pass = pass;
		}
		User.prototype.showName = function(){
			console.log(this.name)
		}
		User.prototype.showPass = function(){
			console.log(this.pass)
		}
		var user = new User('abc','zzzz')
		user.showName();
		user.showPass()
		
		//继承
		function VipUser(name, pass, level) {
		    User.call(this, name, pass)
		    this.level = level
		}
		VipUser.prototype = new User()
		VipUser.prototype.constructor = VipUser
		VipUser.prototype.showLevel = function () {
		    console.log(this.level)
		}
		
		var vipUser = new VipUser('blue', '1234', 3)
		vipUser.showName()
		vipUser.showLevel()
		
	
	```
* 新版本
 	* class关键字、构造器
 	* class里面直接加方法
 	* 继承:

 	
 	```
 		class User{
			construtor(name,pass){
				this.name = name
				this.pass = pass
				
			}
			showName(){
				console.log(this.name)
			}
			showPass(){
				console.log(this.pass)
			}
		}
		var user = new User('abc','zzzz')
		user.showName();
		user.showPass()
		
		//继承
		class VipUser extends User {
		   constructor(name, pass, level) {
		        super(name, pass)
		        this.level = level
		    }
		    showLevel(){
		        console.log(this.level)
		    }
		}
		
		v1 = new VipUser('blue', '123', 3)
		v1.showLevel()
 	```
 	
## 10、面向对象-应用
* React
	* 用于构建用户界面的javascript库
	* 组件化-----class
	* jsx(js扩展) == babel == browser.js 
	
## 11、json
* JSON对象
	* JSON.stringify
	* JSON.parse

	```
		var json = {a: 12, b: 5}
		var str = 'hi,' + JSON.stringify(json)
		var url = 'http://www.baidu.com/' + encodeURIComponent(JSON.stringify(json))
		console.log(str)
		console.log(url)
		
		var str = '{"a": 12, "b": 4, "c": "abc"}'
		var json = JSON.parse(str)
		console.log(json)
	```
* JSON标准写法：
	* 只能双引号
	* 所有的名字（key）必须用引号包起来
	* 名字和值一样，只留一个即可
	
## 12、Promise
* 异步
	* 操作之间没有关系，同时进行多个操作，代码复杂
* 同步
	* 同时只能做一件事、代码简单
* Promise 对象（消除异步操作）
	* 用同步的方式写异步代码
	* Promise.all		全部
	* Promise.race   竞速
		* 哪个结果获得快，就返回那个结果 

	
	```
	
	let oDate= new Promise(function(resolve,reject){
		//异步代码
		//resolve成功了
		//reject 失败了
	})
	
	Promise.all([
		$.ajax({url:'data/arr.text',dataType:'json'}),
		$.ajax({url:'data/json.text',dataType:'json'}),
		$.ajax({url:'data/num.text',dataType:'json'}),
	]).then(res=>{
		let [arr,json,num]=res;
		alert('成功了')
		console.log(arr,json,num)
	},err=>{
		alert('失败了')
	})
	```
	
## 13、generator-认识生成器函数
* generator生成器函数
	* 普通函数---一路到底
	* generator函数---中间能停
	* yield 有 放弃、退让、退位
	* 创造对象才能执行，调用next()方法启动执行，需要遇到 yield 停, 踹一脚走一步
	* 异步操作直接yield代替普通函数的回调函数
	* 实质生成多个小函数，实现走走停停

	```
		function *show() {
		    console.log('1')
		    yield
		    console.log('2')
		}
		
		let genObj = show()
		genObj.next() // 1
		genObj.next() // 2
		genObj.next() // 最后了，没有结果
		
	```
	
	
## 14.generator-yield是啥
* yield
	* 可以传参，也可以返回
	* yield 只能在Generator函数内部使用
	
## 15.generator-实例
* Promise 适合一次读一组
* generator适合逻辑性的

```
	// 带逻辑-generator
	runner(function * () {
	    let userData = yield $.ajax({url: 'getUserData'})
	
	    if (userData.type == 'VIP') {
	        let items = yield $.ajax({url: 'getVIPItems'})
	    } else {
	        let items = yield $.ajax({url: 'getItems'})
	    }
	})
	
	
	// yield 实例，用同步方式写异步
	server.use(function * () {
	    let data = yield db.query(`select * from user_table`)
	    this.body = data
	})
```
	 

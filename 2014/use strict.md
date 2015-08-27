js严格模式
=========
###标志
	
	"use strict";
	//老版本浏览器会自动忽略
###调用
		
	//整个文件调用	
	(function(){
		"use strict";
	})();
	//单个函数调用
	function(){
		"use strict";
		
	}
###语法 行为

>严格模式下 ，不声明的变量赋值的话，会报错误

>禁止使用with

>eval作用域只在内部，不再能够生成全局变量了

>this关键字不再指向全局

>构造函数如果忘记new  this也不会指向全局 ，抛出错误

>禁止内部遍历调用栈

	function f1(){

	  "use strict";

	  f1.caller;    // 报错
	  f1.arguments; // 报错

	}

	f1();
>无法删除变量 只有configurable：true时才可以

	"use strict";

	var x;

	delete x; // 语法错误

	var o = Object.create(null, {
				x: {
					value: 1,
					configurable: true
				}
	});

	delete o.x; // 删除成功	
> 正常模式下，对一个对象的只读属性进行赋值，不会报错，只会默默地失败。严格模式下，将报错。

	"use strict";
 
	var o = {};

	Object.defineProperty(o, "v", { value: 1, writable: false });

	o.v = 2; // 报错
	
>严格模式下，对禁止扩展的对象添加新属性，会报错。

>严格模式下，删除一个不可删除的属性，会报错。

>严格模式下，对一个使用getter方法读取的属性进行赋值，会报错。

>对象不能有重名的属性

	"use strict";

	var o = {
		p: 1,
		p: 2
	}; // 语法错误
> 多个重名参数报错

	"use strict";

	function f(a, a, b) { // 语法错误  

		return ; 

	}
>禁止八进制表示法

>不允许对arguments赋值

>arguments不再追踪参数的变化

>禁止使用arguments.callee

>不允许在非函数的代码块内声明函数
		
		"use strict";

		if (true) {

		  function f() { } // 语法错误

		}

		for (var i = 0; i < 5; i++) {

		  function f2() { } // 语法错误

		}
	
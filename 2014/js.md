
 编写可维护的JavaScript 笔记
============================
****************************
###1.编程风格
1.  **缩进层级** 使用制表符进行缩进 2个/4个空格缩进
1.  **语句结尾** 不省略分号
1.  **行的长度** 不超过80个字符
1.  **换行** 在运算符后面换行
1.  **空行** 在以下场景中添加：
    - 方法之间
    - 在方法中局部变量与第一条语句之间
    - 在多行和单行注释之前
    - 在方法内的逻辑片段之间
1.  **命名** 驼峰式，小写字母开头 后续单词首字母大写
1.  **变量和函数** 命名前缀是名词  myName / count
1.  **常量**  MAX_COUNT 大写字母和下划线来命名
1.  **构造函数** 首字母大写 大驼峰命名
1.  **直接量** 字符串 数字 布尔 null undefined
1.  **字符串** 单引号、双引号都可以，但双引号需要转义，推荐使用双引号，多行字符串用+链接
1.  **数字** JS中只有一种数据类型 浮点型
1.  **NULL**  使用场景：
    - 初始化一个变量，可能赋值为一个对象
    - 用来和对象比较
    - 当参数传入
    - 当返回值传出

    不能使用：
    - 不要用NULL来检测是否传入某个参数
    - 不要用null来检测一个未被初始化的变量
1.  **undefined**   未被初始化的变量都有一个值 就是undefined，避免在代码中使用它
1.  **对象直接量**   {} 直接量比使用构造函数更简洁更高效率
1.  **数组直接量**   []
-----------
###2.注释
1. **单行**  `  //单行注释      `
1. **多行**
        /* 多行注释 */

        /**
         *  多行注释
         *
         */
1. **使用注释** 使用注释的原则是让代码更清晰
1. **难于理解的代码**   难于理解的代码都应添加注释
1. **可能被误认为错误的代码**     应添加注释
1. **浏览器hack**    应添加注释
1. **文档注释**
        /**
         * @method
         * @param
         * @return
         *
         */

---------------------------------------
###3.语句和表达式
1. **所有语句都应当使用花括号**
    - if else语句
    - for 循环
    - while 循环
    - do...while
    - try...catch...finally
1. **花括号对齐方式**  左括号在第一行语句末尾：
        if(condition){
          doSomething();
        } else {
          doSomethingElse();
        }

1. **语句块间隔**

    风格一：
        if(condition){
          doSomething();
        }
    风格二(推荐)：
        if (condition) {
          doSomething();
        }
    风格三：
        if ( condition ) {
          doSomething();
        }
1.  **switch缩进**  每个case语句都对于switch关键字都缩进一个层级，从第二个case开始每个case前后各一个空行

1.  **with**  不适用
1.  **for循环**  break会跳出循环  continue 只会跳出此次循环，继续执行下一次
1.  **for in **  不仅遍历对象的实例属性，还遍历从原型继承的属性， for in 必须用hasOwnpreperty
---------------------------------------------------
###4.变量、函数和运算符
1.  **变量**  变量声明提前，单var
1.  **函数声明** 先声明fn再执行 函数声明不应出现在语句块中
1.  **函数调用间隔**  函数名与左括号间无间隔
1.  **立即调用函数**  ` (fuction(){}) `
1.  **严格模式**  `use strict ` 以严格模式来解析代码 ，不推荐在全局使用，在函数局部使用
1.  **相等**  不使用强制类型转换 `==` `!=` 如果比较值中一个是否是对象，会调用`ValurOf()`方法 . 推荐使用`===` `!==`
1.  **eval**  禁止使用 `Function`  别无他法的时候使用eval
1.  **原始包装类型**  `String` `Boolean` `Number`
----------------------------------------------------
###5.UI层的松耦合
1.  **松耦合定义** 每个组件尽量独立，修改一个不影响其他的组件
1.  **将Js从css中抽离**  不要使用css表达式，因为浏览器会以高频率重复计算css表达式，严重影响性能，IE9不支持表达式
1.  **将Css从Js中抽离**  Js应只负责添加、移除类，不应该设置style。除了操作运动
1.  **将Js从HTML中抽离**  不要写在标签里，用事件绑定，将Js语句放在外置文件中
1.  **将HTML从Js中抽离**
    - 从服务器加载  将模板放在远程服务器
    - 简单的客户端模板  在HTML注释中包含模板文件，`type=text/x-my-template`的script标签
    - 复杂的模板 模板引擎等 handlebars库
----------------------------------------------------
###6.避免使用全局变量
1.  **不使用`var`会产生全局变量**
1.  **不能跟全局变量重名**
1.  **单全局变量方式**
1.  **命名空间**  `Y.My` `Y.Mail`
1.  **模块**
    - YUI模块
    - 异步定义模块 AMD define
    - requireJs
    - CommonJs
1.  **零全局变量** 很少情况下有
----------------------------------------------------
###7.事件处理
        //典型用法

        function handlerClick(event){

            var popup  = document.getElementById('popup');

            popup.style.left = event.clientX+'px';
            popup.style.top = event.clientY+'px';
        }
1.  **隔离应用逻辑**

        /*
            上述代码只用到了 clientX/clientY 两个属性。 但是却将event事件整个传入 。
        */
        // 1 隔离应用逻辑

        /*
            上述例子中 操作popup的left/right值   算是一种应用逻辑，而这个应用逻辑可能其他地方也会操作

            既然其他地方也会操作这个应用逻辑。我们就将它独立出来 。

        */

        //拆分应用逻辑
        var myPopup = {

                handler:function(event){

                    this.showpopup(event);
                },

                showpopup:function(event){
                     var popup  = document.getElementById('popup');
                    popup.style.left = event.clientX+'px';
                    popup.style.top = event.clientY+'px';
                }
        };

        //调用
        var obtn1=document.getElementById('btn1');

        obtn1.addEventListener('click',function(event){

        	myPopup.handler(event);

        },false);
    ***应用逻辑有可能被多处使用，如果正常写可能会被复制很多份，将应用逻辑和事件处理拆分开***

1.  **不要分发事件对象**

        /*
        	在1里面  只需要用到clientX 和clientY 但是却将event时间对象穿进去。

        	好的api  依赖是透明的。 showpopup方法只需要2个数据 而不是一个event

        	传递一个event进去反而将事情变得复杂。

        */
        //重写以上例子
        var myPopup2 = {
        		handler:function(event){
        			event.preventDefault();
        			event.stopPropagation();

        			this.showpopup(event.clientX,event.clientY);
        		},

        		showpopup:function(x,y){

        			var popup  = document.getElementById('popup');
        			popup.style.left = x+'px';
        			popup.style.top = y+'px';
           		}
        };
        //调用
        var obtn2=document.getElementById('btn1');

        obtn1.addEventListener('click',function(event){

        	myPopup2.handler(event.clientX,event.clientY);

        },false);
----------------------------------------------------
###8.避免空比较
1.  **检测原始值**  typeof  字符串：string 数字:number 布尔值：boolean  undefined:undefined
1.  **检测引用值**  [] {} new Date()  new RegExp() 都会得到object  用instanceof
1.  **检测函数** typeof最好  早期的IE8甚至跟早版本 检测dom的时候不会返回function 会返回object,可以用in判断一个方法是否存在
1.  **检测数组** object.prototype.toString.call(value)==='[ object Array ]'
1.  **检测属性** 最好用for/in来判断是否存在，它不会读取属性的值。 如果判断一个实例是否有某属性 用hasOwnproperty
----------------------------------------------------
###9.将配置从代码中分离出来
1.  **抽离配置数据**

    可以被认识是配置数据的示例：
    - URL
    - 需要展现给用户的字符串
    - 重复的值
    - 设置（比如每页的配置项）
    - 任何可能发生变更的值

1.  **保存配置数据**

    配置数据最好放在单独的文件中，以便清晰地分割数据和应用逻辑，放在一个单独的Js文件中。

     数据格式可以是：json格式、JSONP格式、将json格式数据给一个变量

----------------------------------------------------
###10.抛出自定义错误
1.  **正确的抛出方式**

        throe new Error('msg');
1.  **try...catch...finally**
        try{
            //尝试某个语句
        } catch(e){
            //捕捉到错误
        } finally{
            //无论如何都执行这里的语句
        }
1.  **使用throw还是try/catch**  千万不要使catch块空着
1.  **错误类型**
    - Error 所有错误的基本类型
    - EvalError eval函数引发的错误
    - RangeError  数字超出边界
    - ReferenceError 期望对象不存在
    - SyntaxError 给eval方法传递的代码中有语法错误
    - TypeError 变量不是期望类型的时候抛出
    - URIError 给`encodeURI()` `encodeURIComponent()` `decodeURI()` `decodeURIComponent()`传递格式非法的URL时抛出

1.  ** **
----------------------------------------------------
###11.不是你的对象不要动
1.  ** **
1.  ** **
1.  ** **
1.  ** **
1.  ** **
----------------------------------------------------
###12.浏览器嗅探
1.  ** **
1.  ** **
1.  ** **
1.  ** **
1.  ** **
----------------------------------------------------
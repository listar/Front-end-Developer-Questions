# 前端面试题目  

# html

## 请描述一下 cookies，sessionStorage 和 localStorage 的区别？

      - cookie是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。
      - cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递。
      - sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。
    
      - 存储大小：
        cookie数据大小不能超过4k。
        sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。
    
      - 有期时间：
        localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
        sessionStorage  数据在当前浏览器窗口关闭后自动删除。
        cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭
        
  	
  	
## iframe有那些缺点？
      *iframe会阻塞主页面的Onload事件；
      *搜索引擎的检索程序无法解读这种页面，不利于SEO;
    
      *iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
    
      使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript
      动态给iframe添加src属性值，这样可以绕开以上两个问题。
  
  
## 网页验证码是干嘛的，是为了解决什么安全问题。
  
       - 区分用户是计算机还是人的公共全自动程序。可以防止恶意破解密码、刷票、论坛灌水；
       - 有效防止黑客对某一个特定注册用户用特定程序暴力破解方式进行不断的登陆尝试。
 

## 如何实现浏览器内多个标签页之间的通信? 
 
        WebSocket、SharedWorker；
       也可以调用localstorge、cookies等本地存储方式；
     
       localstorge另一个浏览上下文里被添加、修改或删除时，它都会触发一个事件，
       我们通过监听事件，控制它的值来进行页面信息通信；
       注意quirks：Safari 在无痕模式下设置localstorge值时会抛出 QuotaExceededError 的异常；      
           
       
   
   
   
   
# CSS   
   
## CSS选择符有哪些？哪些属性可以继承？

      *   1.id选择器（ # myid）
        2.类选择器（.myclassname）
        3.标签选择器（div, h1, p）
        4.相邻选择器（h1 + p）
        5.子选择器（ul > li）
        6.后代选择器（li a）
        7.通配符选择器（ * ）
        8.属性选择器（a[rel = "external"]）
        9.伪类选择器（a:hover, li:nth-child）
    
      *   可继承的样式： font-size font-family color, UL LI DL DD DT;
    
      *   不可继承的样式：border padding margin width height ;   
   
   
## display有哪些值？说明他们的作用。

    block       	块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
    none        	元素不显示，并从文档流中移除。
    inline      	行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
    inline-block    默认宽度为内容宽度，可以设置宽高，同行显示。
    list-item   	象块类型元素一样显示，并添加样式列表标记。
    table       	此元素会作为块级表格来显示。
    inherit     	规定应该从父元素继承 display 属性的值。
    
    
    none | inline | block | list-item | inline-block | table | inline-table | table-caption | table-cell | table-row 
    | table-row-group | table-column | table-column-group | table-footer-group | table-header-group 
    | run-in | box | inline-box | flexbox | inline-flexbox | flex | inline-flex
    
## display与visibility有何异同？
    
    display可以有很多值，visibility只有两个常用值：visible、hidden。
    当display为none、visibility为hidden时都会隐藏元素。但display会隐藏掉元素空间，visibility会保留元素空间。




## CSS优先级算法如何计算？

     *   优先级就近原则，同权重情况下样式定义最近者为准;
     *   载入样式以最后载入的定位为准;
    
      优先级为:
        同权重: 内联样式表（标签内部）> 嵌入样式表（当前文件中）> 外部样式表（外部文件中）。
        !important >  id > class > tag
        important 比 内联优先级高
   
## 用纯CSS创建一个三角形的原理是什么？   

    把上、左、右三条边隐藏掉（颜色设为 transparent）
      #demo {
        width: 0;
        height: 0;
        border-width: 20px;
        border-style: solid;
        border-color: transparent transparent red transparent;
      }
      
      
## 实现三个DIV等分排在一行（考察border-box)

      1.设置border-box width 33.33%
      2.flexbox flex:1
      
   
## rem 和 em的区别？

    em相对于父元素，rem相对于根元素
    
    
    vh vw px em rem 
    

## CSS中link 和@import的区别是？

    link属于HTML标签，而@import是CSS提供的;
    页面被加载的时，link会同时被加载，而@import被引用的CSS会等到引用它的CSS文件被加载完再加载;
    import只在IE5以上才能识别，而link是HTML标签，无兼容问题;
    link方式的样式的权重 高于@import的权重.


## scss、less

## 关系选择符有哪些?


    E F	包含选择符(Descendant combinator)	CSS1	选择所有被E元素包含的F元素。
    E>F	子选择符(Child combinator)	CSS2	选择所有作为E元素的子元素F。
    E+F	相邻选择符(Adjacent sibling combinator)	CSS2	选择紧贴在E元素之后F元素。
    E~F	兄弟选择符(General sibling combinator)	CSS3	选择E元素所有兄弟元素F。
   
   
## 什么是 BFC

   BFC（Block Formatting Context）格式化上下文，是 Web 页面中盒模型布局的 CSS 渲染模式，指一个独立的渲染区域或者说是一个隔离的独立容器。
### 形成 BFC 的条件

   * 浮动元素，float 除 none 以外的值
   * 定位元素，position（absolute，fixed）
   * display 为以下其中之一的值 inline-block，table-cell，table-caption
   * overflow 除了 visible 以外的值（hidden，auto，scroll）
### BFC 的特性
   * 内部的 Box 会在垂直方向上一个接一个的放置。
   * 垂直方向上的距离由 margin 决定
   * bfc 的区域不会与 float 的元素区域重叠。
   * 计算 bfc 的高度时，浮动元素也参与计算
   * bfc 就是页面上的一个独立容器，容器里面的子元素不会影响外面元素。

   
   
   
# JavaScript


## 介绍js的基本数据类型。
      
      最新的 ECMAScript 标准定义了 7 种数据类型:
      
      6 种原始类型:
          Boolean
          Null
          Undefined
          Number
          String
          Symbol (ECMAScript 6 新定义) (创建后独一无二且不可变的数据类型 )
          Bigint
      和 Object


> 值类型(基本类型)：字符串（String）、数字(Number)、布尔(Boolean)、对空（Null）、未定义（Undefined）、Symbol。
> 
> 引用数据类型：对象(Object)、数组(Array)、函数(Function)。
> 
> 注：Symbol 是 ES6 引入了一种新的原始数据类型，表示独一无二的值。


## 值类型和引用类型的区别

### 1）值类型：

+ 占用空间固定，保存在栈中（当一个方法执行时，每个方法都会建立自己的内存栈，在这个方法内定义的变量将会逐个放入这块栈内存里，随着方法的执行结束，这个方法的内存栈也将自然销毁了。因此，所有在方法中定义的变量都是放在栈内存中的；栈中存储的是基础变量以及一些对象的引用变量，基础变量的值是存储在栈中，而引用变量存储在栈中的是指向堆中的数组或者对象的地址，这就是为何修改引用类型总会影响到其他指向这个地址的引用变量。）

+ 保存与复制的是值本身

+ 使用typeof检测数据的类型

+ 基本类型数据是值类型

### （2）引用类型：

+  占用空间不固定，保存在堆中（当我们在程序中创建一个对象时，这个对象将被保存到运行时数据区中，以便反复利用（因为对象的创建成本通常较大），这个运行时数据区就是堆内存。堆内存中的对象不会随方法的结束而销毁，即使方法结束后，这个对象还可能被另一个引用变量所引用（方法的参数传递时很常见），则这个对象依然不会被销毁，只有当一个对象没有任何引用变量引用它时，系统的垃圾回收机制才会在核实的时候回收它。）

+ 保存与复制的是指向对象的一个指针

+ 使用instanceof检测数据类型

+ 使用new()方法构造出的对象是引用型


## 介绍js有哪些内置对象？

     Object 是 JavaScript 中所有对象的父对象
    
     数据封装类对象：Object、Array、Boolean、Number 和 String
     其他对象：Function、Arguments、Math、Date、RegExp、Error
    
     参考：http://www.ibm.com/developerworks/cn/web/wa-objectsinjs-v1b/index.html

## 说几条写JavaScript的基本规范？

     1、不要在同一行声明多个变量
        2、使用===或!==来比较
        3、使用字面量的方式来创建对象、数组，替代new Array这种形式
        4、不要使用全局函数
        5、switch语句必须要带default分支
        6、函数不应该有的时候有return，有的时候没有return
        7、fon-in循环中的变量，用var关键字说明作用域，防止变量污染
        8、变量的声明遵循驼峰命名法，声明构造函数时首字母大写，定义常量的时候尽量用大写字母，用_分割
        9、三元表达式可以替代if语句
        10、&&和||是可以短路的，使用&&时如果前面一个值是错的，那么后面的值不用判断，使用||时，如果前面一个值是对的，那么后面的值不用判断
        11、比较数据类型以下6种情况是false，其他都是true：false、""、0、null、NaN、undefined
        12、数据类型检测用typeof，对象类型检测用instanceof
        13、异步加载第三方的内容
        14、单行注释//，多行注释/**/
        15、使用命名空间解决变量名冲突
        16、多人协作开发，新建一个js文件，const声明常量，在js文件中引用，用常量名替代方法名，这样做可以防止命名冲突

 
## eval是做什么的？

     它的功能是把对应的字符串解析成JS代码并运行；
     应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。
     由JSON字符串转换为JSON对象的时候可以用eval，var obj =eval('('+ str +')');
     
## null，undefined 的区别？

     null 		表示一个对象是“没有值”的值，也就是值为“空”；
     undefined 	表示一个变量声明了没有初始化(赋值)；
    
     undefined不是一个有效的JSON，而null是；
     undefined的类型(typeof)是undefined；
     null的类型(typeof)是object；
 
 
## .call() 和 .apply() 的区别？
  
     例子中用 add 来替换 sub，add.call(sub,3,1) == add(3,1) ，所以运行结果为：alert(4);
  
     注意：js 中的函数其实是对象，函数名是对 Function 对象的引用。
  
   	function add(a,b)
   	{
   	    alert(a+b);
   	}
  
   	function sub(a,b)
   	{
   	    alert(a-b);
   	}
  
   	add.call(sub,3,1);
   	
## new操作符具体干了什么呢?

    1) 创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
    2) 属性和方法被加入到 this 引用的对象中。
    3) 新创建的对象由 this 所引用，并且最后隐式的返回 this 。


    创造一个全新的对象
    这个对象会被执行 [[Prototype]] 连接，将这个新对象的 [[Prototype]] 链接到这个构造函数.prototype 所指向的对象
    这个新对象会绑定到函数调用的 this
    如果函数没有返回其他对象，那么 new 表达式中的函数调用会自动返回这个新对象



   	
## javascript 代码中的"use strict";是什么意思 ? 使用它区别是什么？
  
       use strict是一种ECMAscript 5 添加的（严格）运行模式,这种模式使得 Javascript 在更严格的条件下运行,
      
       使JS编码更加规范化的模式,消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为。
       默认支持的糟糕特性都会被禁用，比如不能用with，也不能在意外的情况下给全局变量赋值;
       全局变量的显示声明,函数必须声明在顶层，不允许在非函数代码块内声明函数,arguments.callee也不允许使用；
       消除代码运行的一些不安全之处，保证代码运行的安全,限制函数中的arguments修改，严格模式下的eval函数的行为和非严格模式的也不相同;
      
       提高编译器效率，增加运行速度；
       为未来新版本的Javascript标准化做铺垫。
   
## 如何判断一个对象是否属于某个类？
  
     使用instanceof （待完善）
      if(a instanceof Person){
          alert('yes');
      }
      
## delete操作符的功能是什么？
      
    delete操作符用于删除程序中的所有变量或对象，但不能删除使用VAR关键字声明的变量。
    var a = ["a", "b"]
        undefined
    delete a[0]
        true
    a
        (2) [empty, "b"]
    
    
## 什么是window对象? 什么是document对象?

    window对象是指浏览器打开的窗口。
    document对象是Documentd对象（HTML 文档对象）的一个只读引用，window对象的一个属性。 
    
      
## 事件是？IE与火狐的事件机制有什么区别？ 如何阻止冒泡？
  
    1. 我们在网页中的某个操作（有的操作对应多个事件）。例如：当我们点击一个按钮就会产生一个事件。是可以被 JavaScript 侦测到的行为。
    2. 事件处理机制：IE是事件冒泡、Firefox同时支持两种事件模型，也就是：捕获型事件和冒泡型事件；
    3. ev.stopPropagation();（旧ie的方法 ev.cancelBubble = true;）         
    
    
## Javascript如何实现继承？
 
     1、构造继承
     2、原型继承
     3、实例继承
     4、拷贝继承
     
      原型prototype机制或apply和call方法去实现较简单，建议使用构造函数与原型混合方式。
      
        function Parent(){
            this.name = 'wang';
        }
     
        function Child(){
            this.age = 28;
        }
        Child.prototype = new Parent();//继承了Parent，通过原型
     
        var demo = new Child();
        alert(demo.age);
        alert(demo.name);//得到被继承的属性
        
## 介绍promise

      就是一个对象，用来传递异步操作的消息。有三种状态：pending(进行中)，resolved(已完成)和rejected(失败)
      有了promise对象，就可以将异步操作以同步操作的流程表示出来，避免了层层嵌套的回调函数  
        
        
## defer 和 async

    defer并行加载js文件，会按照页面上script标签的顺序执行
    async并行加载js文件，下载完成立即执行，不会按照页面上script标签的顺序执行


## JavaScript原型，原型链 ? 有什么特点？

    ①原型对象也是普通的对象，是对象一个自带隐式的 proto 属性，原型也有可能有自己的原型，如果一个原型对象的原型不为null的话，我们就称之为原型链。
    ②原型链是由一些用来继承和共享属性的对象组成的（有限的）对象链。


## 什么是生成器方法？ 怎么定义

    生成器对象是由一个 generator function 返回的,并且它符合可迭代协议和迭代器协议。
    

## 生成器有哪些方法

    Generator.prototype.next() 
        返回 yield 表达式产生的值. 与ES2015 生成器对象的next()方法对应.
    Generator.prototype.close() 
        关闭生成器，因此执行该函数后调用next()函数时将会抛出 StopIteration 错误. 与ES2015 生成器对象的return()方法对应..
    Generator.prototype.send() 
        用于将值发送到生成器。 该值由 yield 表达式返回, 并且返回下一个 yield 表达式产生的值. send(x) 对应于ES2015生成器对象中的 next(x)
    Generator.prototype.throw() 
        向生成器抛出错误. 与ES2015 生成器对象的throw()方法对应.


## Object 构造函数的方法

    Object.assign()
        通过复制一个或多个对象来创建一个新的对象。
    Object.create()
        使用指定的原型对象和属性创建一个新对象。
    Object.defineProperty()
        给对象添加一个属性并指定该属性的配置。
    Object.defineProperties()
        给对象添加多个属性并分别指定它们的配置。
    Object.entries()
        返回给定对象自身可枚举属性的 [key, value] 数组。
    Object.freeze()
        冻结对象：其他代码不能删除或更改任何属性。
    Object.getOwnPropertyDescriptor()
        返回对象指定的属性配置。
    Object.getOwnPropertyNames()
        返回一个数组，它包含了指定对象所有的可枚举或不可枚举的属性名。
    Object.getOwnPropertySymbols()
        返回一个数组，它包含了指定对象自身所有的符号属性。
    Object.getPrototypeOf()
        返回指定对象的原型对象。
    Object.is()
        比较两个值是否相同。所有 NaN 值都相等（这与==和===不同）。
    Object.isExtensible()
        判断对象是否可扩展。
    Object.isFrozen()
        判断对象是否已经冻结。
    Object.isSealed()
        判断对象是否已经密封。
    Object.keys()
        返回一个包含所有给定对象自身可枚举属性名称的数组。
    Object.preventExtensions()
        防止对象的任何扩展。
    Object.seal()
        防止其他代码删除对象的属性。
    Object.setPrototypeOf()
        设置对象的原型（即内部 [[Prototype]] 属性）。
    Object.values()
        返回给定对象自身可枚举值的数组。

## Map 的使用

        const m = new Map();
        const o = {p: 'Hello World'};

        m.set(o, 'content')
        m.get(o) // "content"

        m.has(o) // true
        m.delete(o) // true
        m.has(o) // false   

        const map = new Map([
            ['name', '张三'],
            ['title', 'Author']
        ]);

        map.size // 2
        map.has('name') // true
        map.get('name') // "张三"
        map.has('title') // true
        map.get('title') // "Author" 

        // 例一
        const entries = new Map([
        ['foo', 'bar'],
        ['baz', 42]
        ]);

        Object.fromEntries(entries)
        // { foo: "bar", baz: 42 }

        // 例二
        const map = new Map().set('foo', true).set('bar', false);
        Object.fromEntries(map)
        // { foo: true, bar: false }  

## Map遍历方法
        Map 结构原生提供三个遍历器生成函数和一个遍历方法。

        Map.prototype.keys()：返回键名的遍历器。
        Map.prototype.values()：返回键值的遍历器。
        Map.prototype.entries()：返回所有成员的遍历器。
        Map.prototype.forEach()：遍历 Map 的所有成员。 

## 什么时候使用Object，什么时候使用Map  
    注意区分 Object 和 Map，只有模拟现实世界的实体对象时，才使用 Object。如果只是需要key: value的数据结构，使用 Map 结构。因为 Map 有内建的遍历机制。


## Javascript的事件流模型都有什么？    
    “事件冒泡”：事件开始由最具体的元素接受，然后逐级向上传播
    “事件捕捉”：事件由最不具体的节点先接收，然后逐级向下，一直到最具体的
    “DOM事件流”：三个阶段：事件捕捉，目标阶段，事件冒泡    

## Array 的迭代方法 有哪些？


## 什么是深拷贝、浅拷贝， 什么情况下会浅拷贝？


## JS 作用域与作用域链 

### 什么是作用域？
    ES5 中只存在两种作用域：全局作用域和函数作用域。在 JavaScript 中，我们将作用域定义为一套规则，这套规则用来管理引擎如何在当前作用域以及嵌套子作用域中根据标识符名称进行变量（变量名或者函数名）查找
### 什么是作用域链？
    首先要了解作用域链，当访问一个变量时，编译器在执行这段代码时，会首先从当前的作用域中查找是否有这个标识符，如果没有找到，就会去父作用域查找，如果父作用域还没找到继续向上查找，直到全局作用域为止,，而作用域链，就是有当前作用域与上层作用域的一系列变量对象组成，它保证了当前执行的作用域对符合访问权限的变量和函数的有序访问。



##js是单线程还是多线程， 为什么不是多线程 ？


## 什么是闭包，闭包解决了什么问题？

    闭包是指有权访问另外一个函数作用域中的变量的函数
    JavaScript代码的整个执行过程，分为两个阶段，代码编译阶段与代码执行阶段。编译阶段由编译器完成，将代码翻译成可执行代码，这个阶段作用域规则会确定。执行阶段由引擎完成，主要任务是执行可执行代码，执行上下文在这个阶段创建。


### 闭包产生的本质
当前环境中存在指向父级作用域的引用
### 什么是闭包
闭包是一种特殊的对象，它由两部分组成：执行上下文（代号 A），以及在该执行上下文中创建的函数 （代号 B），当 B 执行时，如果访问了 A 中变量对象的值，那么闭包就会产生，且在 Chrome 中使用这个执行上下文 A 的函数名代指闭包。
### 一般如何产生闭包

返回函数
函数当做参数传递

### 闭包的应用场景
柯里化 bind
模块



## 问：js脚本加载问题，async、defer问题
如果依赖其他脚本和 DOM 结果，使用 defer
如果与 DOM 和其他脚本依赖不强时，使用 async


## 箭头函数和普通函数有啥区别？箭头函数能当构造函数吗？

普通函数通过 function 关键字定义， this 无法结合词法作用域使用，在运行时绑定，只取决于函数的调用方式，在哪里被调用，调用位置。（取决于调用者，和是否独立运行）
箭头函数使用被称为 “胖箭头” 的操作 => 定义，箭头函数不应用普通函数 this 绑定的四种规则，而是根据外层（函数或全局）的作用域来决定 this，且箭头函数的绑定无法被修改（new 也不行）。

箭头函数常用于回调函数中，包括事件处理器或定时器
箭头函数和 var self = this，都试图取代传统的 this 运行机制，将 this 的绑定拉回到词法作用域
没有原型、没有 this、没有 super，没有 arguments，没有 new.target
不能通过 new 关键字调用

一个函数内部有两个方法：[[Call]] 和 [[Construct]]，在通过 new 进行函数调用时，会执行 [[construct]] 方法，创建一个实例对象，然后再执行这个函数体，将函数的 this 绑定在这个实例对象上
当直接调用时，执行 [[Call]] 方法，直接执行函数体
箭头函数没有 [[Construct]] 方法，不能被用作构造函数调用，当使用 new 进行函数调用时会报错。



## 问：事件循环机制 （Event Loop）
事件循环机制从整体上告诉了我们 JavaScript 代码的执行顺序
Event Loop即事件循环，是指浏览器或Node的一种解决javaScript单线程运行时不会阻塞的一种机制，也就是我们经常使用异步的原理。
先执行宏任务队列，然后执行微任务队列，然后开始下一轮事件循环，继续先执行宏任务队列，再执行微任务队列。

宏任务：script/setTimeout/setInterval/setImmediate/ I/O / UI Rendering
微任务：process.nextTick()/Promise  

上诉的 setTimeout 和 setInterval 等都是任务源，真正进入任务队列的是他们分发的任务。


## 手写题：实现柯里化
    预先设置一些参数
    柯里化是什么：是指这样一个函数，它接收函数 A，并且能返回一个新的函数，这个新的函数能够处理函数 A 的剩余参数
    function createCurry(func, args) {
    var argity = func.length;
    var args = args || [];
    
    return function () {
        var _args = [].slice.apply(arguments);
        args.push(..._args);
        
        if (args.length < argity) {
        return createCurry.call(this, func, args);
        }
        
        return func.apply(this, args);
    }
    }

### 什么是柯里化（ curry）
        在数学和计算机科学中，柯里化是一种将使用多个参数的一个函数转换成一系列使用一个参数的函数的技术。
        举例来说，一个接收3个参数的普通函数，在进行柯里化后， 柯里化版本的函数接收一个参数并返回接收下一个参数的函数， 该函数返回一个接收第三个参数的函数。 最后一个函数在接收第三个参数后， 将之前接收到的三个参数应用于原普通函数中，并返回最终结果。



## 问：变量提升
函数在运行的时候，会首先创建执行上下文，然后将执行上下文入栈，然后当此执行上下文处于栈顶时，开始运行执行上下文。
在创建执行上下文的过程中会做三件事：创建变量对象，创建作用域链，确定 this 指向，其中创建变量对象的过程中，首先会为 arguments 创建一个属性，值为 arguments，然后会扫码 function 函数声明，创建一个同名属性，值为函数的引用，接着会扫码 var 变量声明，创建一个同名属性，值为 undefined，这就是变量提升


## 防抖和节流
    综合应用场景

### 防抖(debounce):
    就是指触发事件后在 n 秒内函数只能执行一次，如果在 n 秒内又触发了事件，则会重新计算函数执行时间。

    search搜索联想，用户在不断输入值时，用防抖来节约请求资源。

    window触发resize的时候，不断的调整浏览器窗口大小会不断的触发这个事件，用防抖来让其只触发一次
### 节流(throttle):
    就是指连续触发事件但是在 n 秒中只执行一次函数。节流会稀释函数的执行频率。

    鼠标不断点击触发，mousedown(单位时间内只触发一次)

    监听滚动事件，比如是否滑到底部自动加载更多，用throttle来判断 所谓防抖，就是指触发事件后在 n 秒内函数只能执行一次，如果在 n 秒内又触发了事件，则会重新计算函数执行时间。


说说写JavaScript的基本规范？

JavaScript原型，原型链 ? 有什么特点？

        JavaScript是一种基于原型的面向对象编程语言。在JavaScript中，每个对象都有一个原型对象，该对象本身又有一个原型对象。这种关系组成了原型链，维护了JavaScript对象继承的关系。

        特点：

        原型链可以让JavaScript对象共享属性和方法，减少了内存消耗。
        原型链允许对象继承，但它不像其他语言的继承方式那样严格。
        原型链没有类的概念，而是通过对象直接关联实现继承关系。
        原型链是动态的，允许在运行时修改对象的原型，从而实现动态继承。

JavaScript有几种类型的值？（堆：原始数据类型和 栈：引用数据类型），你能画一下他们的内存图吗？

Javascript如何实现继承？

Javascript创建对象的几种方式？

        JavaScript中创建对象的几种方式如下：

        工厂模式：通过函数来创建一个对象，通过函数的不同来创建不同的对象

        构造函数模式：通过一个构造函数来创建对象，通过new关键字调用该构造函数来创建对象

        原型模式：通过一个原型对象来创建新的对象，新对象可以继承该原型对象的属性和方法

        Object.create()模式：直接使用Object.create()方法来创建对象，该方法会直接以传入的对象作为新对象的原型对象

        类模式：使用class关键字来创建一个类，通过new关键字调用该类来创建对象。



Javascript作用链域?

        作用域链是 JavaScript 的一个重要概念，它代表了 JavaScript 代码在运行时的变量访问顺序。当 JavaScript 引擎寻找变量时，它会在当前执行作用域中查找，如果找不到，则会在该作用域的父作用域中查找，以此类推。这样构成的一系列作用域组成了一个“作用域链”，JavaScript 引擎在查找变量时会沿着这条链搜索，直到找到第一个找到的变量为止。

        作用域链的核心思想是将执行上下文（该语句执行的环境）的作用域链链接在一起，这样 JavaScript 引擎就可以在当前执行作用域内快速查找变量。因此，作用域链非常重要，因为它决定了变量的可见性和生命周期。

谈谈this对象的理解。

    “this” 是 JavaScript 中一个特殊的对象。在函数内部，它代表函数的调用者，但其具体指向取决于函数的调用方式。

    如果函数是作为对象的方法调用的，那么 "this" 将指向该对象。如果函数是通过 "apply" 或 "call" 调用的，那么 "this" 将分别指向 "apply" 和 "call" 的第一个参数。如果函数是作为构造函数调用的，那么 "this" 将指向新创建的对象。

    在箭头函数中， "this" 是继承自外层作用域的，因此不会受到调用方式的影响。这意味着，如果箭头函数是在全局作用域内定义的，那么 "this" 将指向全局对象，如果箭头函数是在对象内部定义的，那么 "this" 将指向该对象。

Webpack热更新实现原理?

请介绍一下JS之事件节流？

什么是JS的函数防抖？


## Object.defineProperty()   Proxy


## 为什么 JavaScript 是单线程
JavaScript语言的一大特点就是单线程，也就是说，同一个时间只能做一件事。那么，为什么JavaScript不能有多个线程呢？这样能提高效率啊。
JavaScript的单线程，与它的用途有关。作为浏览器脚本语言，JavaScript的主要用途是与用户互动，以及操作DOM。这决定了它只能是单线程，否则会带来很复杂的同步问题。比如，假定JavaScript同时有两个线程，一个线程在某个DOM节点上添加内容，另一个线程删除了这个节点，这时浏览器应该以哪个线程为准？
所以，为了避免复杂性，从一诞生，JavaScript就是单线程，这已经成了这门语言的核心特征，将来也不会改变。
为了利用多核CPU的计算能力，HTML5提出Web Worker标准，允许JavaScript脚本创建多个线程，但是子线程完全受主线程控制，且不得操作DOM。所以，这个新标准并没有改变JavaScript单线程的本质。


## 为什么要有Event Loop？
因为Javascript设计之初就是一门单线程语言，因此为了实现主线程的不阻塞，Event Loop这样的方案应运而生。
Event Loop即事件循环，是指浏览器或Node的一种解决javaScript单线程运行时不会阻塞的一种机制，也就是我们经常使用异步的原理。


## Event Loop 任务
在JavaScript中，任务被分为两种，一种宏任务（MacroTask）也叫Task，一种叫微任务（MicroTask）。
MacroTask（宏任务），包括setTimeout、setInterval、setImmediate（浏览器暂时不支持，只有IE10支持）、I/O、UI交互事件 
MicroTask（微任务），包括Promise、process.nextTick（Node独有）、MutaionObserver


## 介绍下 webpack 热更新原理，是如何做到在不刷新浏览器的前提下更新页面 

    1.当修改了一个或多个文件；
    2.文件系统接收更改并通知webpack；
    3.webpack重新编译构建一个或多个模块，并通知HMR服务器进行更新；
    4.HMR Server 使用webSocket通知HMR runtime 需要更新，HMR运行时通过HTTP请求更新jsonp；
    5.HMR运行时替换更新中的模块，如果确定这些模块无法更新，则触发整个页面刷新。
    https://zhuanlan.zhihu.com/p/30669007


## package.json
    安装项目依赖（dependencies & devDependencies）


    dependencies字段指定了项目运行所依赖的模块（生产环境使用），如 antd、 react、 moment等插件库：

    它们是我们生产环境所需要的依赖项，在把项目作为一个 npm 包的时候，用户安装 npm 包时只会安装 dependencies 里面的依赖。



    devDependencies 字段指定了项目开发所需要的模块（开发环境使用），如 webpack、typescript、babel等：

    在代码打包提交线上时，我们并不需要这些工具，所以我们将它放入 devDependencies 中。



    如果一个模块不在 package.json 文件之中，我们可以单独安装这个模块，并使用相应的参数，将其写入 dependencies 字段/ devDependencies 字段中：




# other  

## http状态码有那些？分别代表是什么意思？

  	[
  		100  Continue	继续，一般在发送post请求时，已发送了http header之后服务端将返回此信息，表示确认，之后发送具体参数信息
  		200  OK 		正常返回信息
  		201  Created  	请求成功并且服务器创建了新的资源
  		202  Accepted 	服务器已接受请求，但尚未处理
  		301  Moved Permanently  请求的网页已永久移动到新位置。
  		302 Found  		临时性重定向。
  		303 See Other  	临时性重定向，且总是使用 GET 请求新的 URI。
  		304  Not Modified 自从上次请求后，请求的网页未修改过。

  		400 Bad Request  服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求。
  		401 Unauthorized 请求未授权。
  		403 Forbidden  	禁止访问。
  		404 Not Found  	找不到如何与 URI 相匹配的资源。

  		500 Internal Server Error  最常见的服务器端错误。
  		503 Service Unavailable 服务器端暂时无法处理请求（可能是过载或维护）。
  	]


## 从输入URL到页面加载发生了什么

    DNS解析
    TCP连接
    发送HTTP请求
    服务器处理请求并返回HTTP报文
    浏览器解析渲染页面
    连接结束
    
## get和post的区别？
    
    GET：一般用于信息获取，使用URL传递参数，对所发送信息的数量也有限制，一般在2000个字符
    POST：一般用于修改服务器上的资源，对所发送的信息没有限制。
    GET方式需要使用Request.QueryString来取得变量的值，而POST方式通过Request.Form来获取变量的值，
    也就是说Get是通过地址栏来传值，而Post是通过提交表单来传值。
    
    然而，在以下情况中，请使用 POST 请求：
        ①无法使用缓存文件（更新服务器上的文件或数据库）向服务器发送大量数据（POST 没有数据量限制）。
        ②发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠。
    

    
## 提高页面加载速度，你会做哪些优化？

    html 压缩
    图片懒加载
    css压缩
    js压缩
    cdn
    服务器配置使用 使用压缩文件
    等等...

    
    
## HTTP和HTTPS

    HTTP协议通常承载与 TCP协议之上，在HTTP和TCP之间添加一个安全协议层（SSL或TSL），这个时候，就成了我们常说的HTTPS
    默认HTTP的端口号为80，HTTPS的端口号为443
    
    
## 跨域问题

    


## SSR是什么？
SSR也就是服务端渲染，也就是将Vue在客户端把标签渲染成HTML的工作放在服务端完成，然后再把html直接返回给客户端。
SSR有着更好的SEO、并且首屏加载速度更快等优点。不过它也有一些缺点，比如我们的开发条件会受到限制，服务器端渲染只支持beforeCreate和created两个钩子，当我们需要一些外部扩展库时需要特殊处理，服务端渲染应用程序也需要处于Node.js的运行环境。还有就是服务器会有更大的负载需求。



# vue.js



## vm.$refs
 
    vm.$refs    一个对象，持有注册过 ref 特性 的所有 DOM 元素和组件实例。


## v-show  和 v-if  的区别    

## 介绍一下 Vuex 吧

    Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。每一个 Vuex 应用的核心就是 store（仓库）。store 基本上就是一个容器，它包含着你的应用中大部分的状态 ( state )。
    （1）Vuex 的状态存储是响应式的。当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么相应的组件也会相应地得到高效更新。
    （2）改变 store 中的状态的唯一途径就是显式地提交 (commit) mutation。这样使得我们可以方便地跟踪每一个状态的变化。
    主要包括以下几个模块：

    State：定义了应用状态的数据结构，可以在这里设置默认的初始状态。
    Getter：允许组件从 Store 中获取数据，mapGetters 辅助函数仅仅是将 store 中的 getter 映射到局部计算属性。
    Mutation：是唯一更改 store 中状态的方法，且必须是同步函数。
    Action：用于提交 mutation，而不是直接变更状态，可以包含任意异步操作。
    Module：允许将单一的 Store 拆分为多个 store 且同时保存在单一的状态树中。




## 怎么引入远程cdn的js


## 打包的单个js较大怎么优化


## v-for  的keys使用什么值  keys的作用



##在下次 DOM 更新循环结束之后执行延迟回调
    
    Vue.nextTick( [callback, context] )
    
    在下次 DOM 更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的 DOM。
    
    
    
## Vue.use( plugin ) 是干什么   

    安装 Vue.js 插件。如果插件是一个对象，必须提供 install 方法。
    如果插件是一个函数，它会被作为 install 方法。install 方法调用时，会将 Vue 作为参数传入。
    该方法需要在调用 new Vue() 之前被调用。
    当 install 方法被同一个插件多次调用，插件将只会被安装一次。
    
## keep-alive

    <keep-alive> 包裹动态组件时，会缓存不活动的组件实例，而不是销毁它们。和 <transition> 相似，
    <keep-alive> 是一个抽象组件：它自身不会渲染一个 DOM 元素，也不会出现在父组件链中。 
    当组件在 <keep-alive> 内被切换，它的 activated 和 deactivated 这两个生命周期钩子函数将会被对应执行。    
    
   
## template
  
    一个字符串模板作为 Vue 实例的标识使用。模板将会 替换 挂载的元素。
    挂载元素的内容都将被忽略，除非模板的内容有分发插槽。
    如果值以 # 开始，则它将被用作选择符，并使用匹配元素的 innerHTML 作为模板。
    常用的技巧是用 <script type="x-template"> 包含模板。      
    
## renderError

    只在开发者环境下工作。
    当 render 函数遭遇错误时，提供另外一种渲染输出。其错误将会作为第二个参数传递到 renderError。这个功能配合 hot-reload 非常实用。   



## 为什么vue组件中的 data 必须是一个函数，return 一个对象
因为组件是用来复用的，且 JS 里对象是引用类型，如果组件中 data 是一个对象，子组件中的 data 属性值会相互影响，如果组件中 data 选项是一个函数，每个实例可以维护一份被返回对象的独立拷贝，组件实例之间的 data 属性值不会互相影响

追问：new Vue 实例里，data 可以直接是一个对象？

new Vue() 是根组件，是不会被复用的，因此不存在引用对象的问题。


## 介绍一下Vue中的Diff算法

首先，对比节点本身，判断是否为同一节点，如果不为相同节点，则删除该节点重新创建节点进行替换。
如果为相同节点，进行patchVnode，判断如何对该节点的子节点进行处理，先判断一方有子节点一方没有子节点的情况(如果新的children没有子节点，将旧的子节点移除)。
比较如果都有子节点，则进行updateChildren，判断如何对这些新老节点的子节点进行操作（diff核心）。
匹配时，找到相同的子节点，递归比较子节点。

在diff中，只对同层的子节点进行比较，放弃跨级的节点比较，使得时间复杂从O(n^3)降低值O(n)，也就是说，只有当新旧children都为多个子节点时才需要用核心的Diff算法进行同层级比较。

## mvvm    

    
## 怎么声明404页面 


## .vue是怎么解析到浏览器可识别js




## Vue vs React的区别

### 相同点：

        使用virtural DOM + Diff算法。
        组件化思想。

### 不同点：

        模板语法的不同：react通过JSX渲染模板，vue通过拓展的html语法进行渲染。比如react中插值、条件、循环都通过JS语法实现，vue是通过指令v-bind、v-if、v-for实现的。
        监听数据变化原理不同：vue通过getter、setter劫持通知数据变化，react通过比较引用的方式进行。
        vue使用的响应式数据，而react是不可变数据。vue改变数据直接赋值，react需要调用setState方法（用新的state替换旧的state）。







# angularjs2

## Angular 2 应用程序应用主要由以下 8 个部分组成：
        1、模块 (Modules)
        2、组件 (Components)
        3、模板 (Templates)
        4、元数据 (Metadata)
        5、数据绑定 (Data Binding)
        6、指令 (Directives)
        7、服务 (Services)
        8、依赖注入 (Dependency Injection)
        
## Angular 有三种类型的视图类： 
        组件 、 指令 和 管道 。

##ng-show/ng-hide 与 ng-if的区别？
        我们都知道ng-show/ng-hide实际上是通过display来进行隐藏和显示的。
        而ng-if实际上控制dom节点的增删除来实现的。因此如果我们是根据不同的条件来进行dom节点的加载的话，那么ng-if的性能好过ng-show.




 ## TypeScript

 ### TypeScript的特点

    类型检查。TypeScript在编译代码时进行严格的静态类型检查。这就意味着在编码阶段可能存在的隐患，不必把它们带到线上。

    语言扩展。TypeScript会包括ES6和未来提案中的特性，比如异步操作和装饰器。也会从其他语言借鉴某些特点，比如接口和抽象类。

    工具属性。TypeScript 可以编译成标准的 Javascript。可以在任何浏览器和操作系统上运行。无需任何运行时额外开销。从这个角度讲TypeScript更像时一个工具。

### 类型
    TypeScript中定义了布尔值boolean、数字number、字符串string、数组Array、元组、枚举、接口、any、void等。

    元组。元组表示的是一个已知元素数量和类型的数组，各元素的类型不必相同。

### TS 编译流程
    和Babel以及其他编译到 Javascript 的工具类似， TS　的编译流程包含一下三步：
    解析 －> 转换  －> 生成
    包含了一下几个关键部分：

    Scanner：从源码生成 Token
    Parser: 从 Token 生成 AST
    Binder：从AST 生成 Symbol
    Checker：类型检查
    Emitter： 生成最终的 JS 文件

    
# 知识点
 
     1. vue
     2. react
     3. Angular
     4. webpack
     5. glup
     6. koa
     7. 一门后端语言
     8. jQuery 、zepto
     9. scss、less 、 bootstrap
     10. loadjs
     11. commomJs
     12. eggjs
     13. flutter
     14. 微信小程序
     15. socket.io
     16. pixijs
     17. iconfont、 echarts、 svg
     18. egret、 cocos2d、 unity
     19. restful
     20. 单元测试、eslint
     21. 集成、发布、部署
     22. vuex、dva、Redux、MobX
     等等
     
        
## 设计模式

     mvc
     
     mvvm

     mvp

        MVP（Model-View-Presenter）是一种软件设计模式，用于分离用户界面逻辑和业务逻辑。MVP模式将模型（Model）、视图（View）和表示层（Presenter）分离开来。

    模型（Model）是应用程序的数据和业务逻辑，负责存储、检索和更新数据。

    视图（View）是应用程序的用户界面，显示模型中的数据并允许用户与之交互。

    表示层（Presenter）是应用程序的控制器，负责控制用户界面的行为。它在模型和视图之间建立了一个中介，控制交互流程。

    MVP模式有助于提高应用程序的代码可读性和可维护性，因为它分离了业务逻辑和用户界面逻辑，使得代码更加结构化，更容易管理。
        
## other  

    除了前端以外还了解什么其它技术么？

    1描述一个你遇到过的技术问题，你是如何解决的？
    1.1这个问题很常见，有没有遇到过很不常见的问题？比如在网上根本搜不到解决方法的？
    
    2你最擅长的技术是什么？
    2.2你觉得你在这个技术上的水平到什么程度了？你觉得最高级别应该是怎样的？
    
   
    
    兴趣相关
    最近在学什么？接下来半年你打算学习什么？
    做什么方面的事情最让你有成就感？需求设计？规划？具体开发？
    后续想做什么？3 年后你希望自己是什么水平？

#其他面试题



# 前端学习网站推荐    
        1. 极客标签：     http://www.gbtags.com/

        2. 码农周刊：     http://weekly.manong.io/issues/

        3. 前端周刊：     http://www.feweekly.com/issues

        4. 慕课网：       http://www.imooc.com/

        5. div.io：		 http://div.io

        6. Hacker News： https://news.ycombinator.com/news

        7. InfoQ：       http://www.infoq.com/

        8. w3cplus：     http://www.w3cplus.com/

        9. Stack Overflow： http://stackoverflow.com/

        10.w3school：    http://www.w3school.com.cn/

        11.mozilla：     https://developer.mozilla.org/zh-CN/docs/Web/JavaScript
        
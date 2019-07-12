面试题目  
=====


#html

##请描述一下 cookies，sessionStorage 和 localStorage 的区别？

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
        
  	
  	
##iframe有那些缺点？
      *iframe会阻塞主页面的Onload事件；
      *搜索引擎的检索程序无法解读这种页面，不利于SEO;
    
      *iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
    
      使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript
      动态给iframe添加src属性值，这样可以绕开以上两个问题。
  
  
##网页验证码是干嘛的，是为了解决什么安全问题。
  
       - 区分用户是计算机还是人的公共全自动程序。可以防止恶意破解密码、刷票、论坛灌水；
       - 有效防止黑客对某一个特定注册用户用特定程序暴力破解方式进行不断的登陆尝试。
 

##如何实现浏览器内多个标签页之间的通信? 
 
        WebSocket、SharedWorker；
       也可以调用localstorge、cookies等本地存储方式；
     
       localstorge另一个浏览上下文里被添加、修改或删除时，它都会触发一个事件，
       我们通过监听事件，控制它的值来进行页面信息通信；
       注意quirks：Safari 在无痕模式下设置localstorge值时会抛出 QuotaExceededError 的异常；      
           
       
   
#CSS   
   
##CSS选择符有哪些？哪些属性可以继承？

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
   
   
##display有哪些值？说明他们的作用。

    block       	块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
    none        	元素不显示，并从文档流中移除。
    inline      	行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
    inline-block  默认宽度为内容宽度，可以设置宽高，同行显示。
    list-item   	象块类型元素一样显示，并添加样式列表标记。
    table       	此元素会作为块级表格来显示。
    inherit     	规定应该从父元素继承 display 属性的值。
    
    
    none | inline | block | list-item | inline-block | table | inline-table | table-caption | table-cell | table-row 
    | table-row-group | table-column | table-column-group | table-footer-group | table-header-group 
    | run-in | box | inline-box | flexbox | inline-flexbox | flex | inline-flex
    

##CSS优先级算法如何计算？

     *   优先级就近原则，同权重情况下样式定义最近者为准;
     *   载入样式以最后载入的定位为准;
    
      优先级为:
        同权重: 内联样式表（标签内部）> 嵌入样式表（当前文件中）> 外部样式表（外部文件中）。
        !important >  id > class > tag
        important 比 内联优先级高
   
##用纯CSS创建一个三角形的原理是什么？   

    把上、左、右三条边隐藏掉（颜色设为 transparent）
      #demo {
        width: 0;
        height: 0;
        border-width: 20px;
        border-style: solid;
        border-color: transparent transparent red transparent;
      }
      
      
##实现三个DIV等分排在一行（考察border-box)
      1.设置border-box width 33.33%
      2.flexbox flex:1
   
##rem 和 em的区别？
    em相对于父元素，rem相对于根元素

##CSS中link 和@import的区别是？
    link属于HTML标签，而@import是CSS提供的;
    页面被加载的时，link会同时被加载，而@import被引用的CSS会等到引用它的CSS文件被加载完再加载;
    import只在IE5以上才能识别，而link是HTML标签，无兼容问题;
    link方式的样式的权重 高于@import的权重.

#scss、less
   
   
   
   
#JavaScript


##介绍js的基本数据类型。

      Undefined、Null、Boolean、Number、String、
      ECMAScript 2015 新增:Symbol(创建后独一无二且不可变的数据类型 )

##介绍js有哪些内置对象？

     Object 是 JavaScript 中所有对象的父对象
    
     数据封装类对象：Object、Array、Boolean、Number 和 String
     其他对象：Function、Arguments、Math、Date、RegExp、Error
    
     参考：http://www.ibm.com/developerworks/cn/web/wa-objectsinjs-v1b/index.html

##说几条写JavaScript的基本规范？

     1.不要在同一行声明多个变量。
     2.请使用 ===/!==来比较true/false或者数值
     3.使用对象字面量替代new Array这种形式
     4.不要使用全局函数。
     5.Switch语句必须带有default分支
     6.函数不应该有时候有返回值，有时候没有返回值。
     7.For循环必须使用大括号
     8.If语句必须使用大括号
     9.for-in循环中的变量 应该使用var关键字明确限定作用域，从而避免作用域污染。
 
##eval是做什么的？

     它的功能是把对应的字符串解析成JS代码并运行；
     应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。
     由JSON字符串转换为JSON对象的时候可以用eval，var obj =eval('('+ str +')');
     
##null，undefined 的区别？

     null 		表示一个对象是“没有值”的值，也就是值为“空”；
     undefined 	表示一个变量声明了没有初始化(赋值)；
    
     undefined不是一个有效的JSON，而null是；
     undefined的类型(typeof)是undefined；
     null的类型(typeof)是object；
 
 
##.call() 和 .apply() 的区别？
  
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

   	
##javascript 代码中的"use strict";是什么意思 ? 使用它区别是什么？
  
       use strict是一种ECMAscript 5 添加的（严格）运行模式,这种模式使得 Javascript 在更严格的条件下运行,
      
       使JS编码更加规范化的模式,消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为。
       默认支持的糟糕特性都会被禁用，比如不能用with，也不能在意外的情况下给全局变量赋值;
       全局变量的显示声明,函数必须声明在顶层，不允许在非函数代码块内声明函数,arguments.callee也不允许使用；
       消除代码运行的一些不安全之处，保证代码运行的安全,限制函数中的arguments修改，严格模式下的eval函数的行为和非严格模式的也不相同;
      
       提高编译器效率，增加运行速度；
       为未来新版本的Javascript标准化做铺垫。
   
##如何判断一个对象是否属于某个类？
  
     使用instanceof （待完善）
      if(a instanceof Person){
          alert('yes');
      }
      
##delete操作符的功能是什么？
      
    delete操作符用于删除程序中的所有变量或对象，但不能删除使用VAR关键字声明的变量。
    
    
##什么是window对象? 什么是document对象?

    window对象是指浏览器打开的窗口。
    document对象是Documentd对象（HTML 文档对象）的一个只读引用，window对象的一个属性。 
    
      
##事件是？IE与火狐的事件机制有什么区别？ 如何阻止冒泡？
  
    1. 我们在网页中的某个操作（有的操作对应多个事件）。例如：当我们点击一个按钮就会产生一个事件。是可以被 JavaScript 侦测到的行为。
    2. 事件处理机制：IE是事件冒泡、Firefox同时支持两种事件模型，也就是：捕获型事件和冒泡型事件；
    3. ev.stopPropagation();（旧ie的方法 ev.cancelBubble = true;）         
    
    
 ##Javascript如何实现继承？
 
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
        
##介绍promise
      就是一个对象，用来传递异步操作的消息。有三种状态：pending(进行中)，resolved(已完成)和rejected(失败)
      有了promise对象，就可以将异步操作以同步操作的流程表示出来，避免了层层嵌套的回调函数  
        
        
##defer 和 async
    defer并行加载js文件，会按照页面上script标签的顺序执行
    async并行加载js文件，下载完成立即执行，不会按照页面上script标签的顺序执行


##从输入URL到页面加载发生了什么
    DNS解析
    TCP连接
    发送HTTP请求
    服务器处理请求并返回HTTP报文
    浏览器解析渲染页面
    连接结束
    
##提高页面加载速度，你会做哪些优化？

    
    
##HTTP和HTTPS
    HTTP协议通常承载与 TCP协议之上，在HTTP和TCP之间添加一个安全协议层（SSL或TSL），这个时候，就成了我们常说的HTTPS
    默认HTTP的端口号为80，HTTPS的端口号为443
    
        
##other  

    除了前端以外还了解什么其它技术么？

    1描述一个你遇到过的技术问题，你是如何解决的？
    1.1这个问题很常见，有没有遇到过很不常见的问题？比如在网上根本搜不到解决方法的？
    
    2你最擅长的技术是什么？
    2.2你觉得你在这个技术上的水平到什么程度了？你觉得最高级别应该是怎样的？
    
    mvc
    mvvm
    
    兴趣相关
    最近在学什么？接下来半年你打算学习什么？
    做什么方面的事情最让你有成就感？需求设计？规划？具体开发？
    后续想做什么？3 年后你希望自己是什么水平？
        
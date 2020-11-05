# 前端面试题目  

# html

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
           
       
   
   
   
   
# CSS   
   
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
    inline-block    默认宽度为内容宽度，可以设置宽高，同行显示。
    list-item   	象块类型元素一样显示，并添加样式列表标记。
    table       	此元素会作为块级表格来显示。
    inherit     	规定应该从父元素继承 display 属性的值。
    
    
    none | inline | block | list-item | inline-block | table | inline-table | table-caption | table-cell | table-row 
    | table-row-group | table-column | table-column-group | table-footer-group | table-header-group 
    | run-in | box | inline-box | flexbox | inline-flexbox | flex | inline-flex
    
##display与visibility有何异同？
    
    display可以有很多值，visibility只有两个常用值：visible、hidden。
    当display为none、visibility为hidden时都会隐藏元素。但display会隐藏掉元素空间，visibility会保留元素空间。




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
    
    
    vh vw px em rem 
    

##CSS中link 和@import的区别是？

    link属于HTML标签，而@import是CSS提供的;
    页面被加载的时，link会同时被加载，而@import被引用的CSS会等到引用它的CSS文件被加载完再加载;
    import只在IE5以上才能识别，而link是HTML标签，无兼容问题;
    link方式的样式的权重 高于@import的权重.


##scss、less

##关系选择符有哪些?


    E F	包含选择符(Descendant combinator)	CSS1	选择所有被E元素包含的F元素。
    E>F	子选择符(Child combinator)	CSS2	选择所有作为E元素的子元素F。
    E+F	相邻选择符(Adjacent sibling combinator)	CSS2	选择紧贴在E元素之后F元素。
    E~F	兄弟选择符(General sibling combinator)	CSS3	选择E元素所有兄弟元素F。
   
   
   
   
   
# JavaScript


##介绍js的基本数据类型。
      
      最新的 ECMAScript 标准定义了 7 种数据类型:
      
      6 种原始类型:
          Boolean
          Null
          Undefined
          Number
          String
          Symbol (ECMAScript 6 新定义) (创建后独一无二且不可变的数据类型 )
      和 Object


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
   	
##new操作符具体干了什么呢?

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
    var a = ["a", "b"]
        undefined
    delete a[0]
        true
    a
        (2) [empty, "b"]
    
    
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


##JavaScript原型，原型链 ? 有什么特点？

    ①原型对象也是普通的对象，是对象一个自带隐式的 proto 属性，原型也有可能有自己的原型，如果一个原型对象的原型不为null的话，我们就称之为原型链。
    ②原型链是由一些用来继承和共享属性的对象组成的（有限的）对象链。


##什么是生成器方法？ 怎么定义

    生成器对象是由一个 generator function 返回的,并且它符合可迭代协议和迭代器协议。
    

##生成器有哪些方法

    Generator.prototype.next() 
        返回 yield 表达式产生的值. 与ES2015 生成器对象的next()方法对应.
    Generator.prototype.close() 
        关闭生成器，因此执行该函数后调用next()函数时将会抛出 StopIteration 错误. 与ES2015 生成器对象的return()方法对应..
    Generator.prototype.send() 
        用于将值发送到生成器。 该值由 yield 表达式返回, 并且返回下一个 yield 表达式产生的值. send(x) 对应于ES2015生成器对象中的 next(x)
    Generator.prototype.throw() 
        向生成器抛出错误. 与ES2015 生成器对象的throw()方法对应.


##Object 构造函数的方法

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

##Map 的使用

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

##Map遍历方法
        Map 结构原生提供三个遍历器生成函数和一个遍历方法。

        Map.prototype.keys()：返回键名的遍历器。
        Map.prototype.values()：返回键值的遍历器。
        Map.prototype.entries()：返回所有成员的遍历器。
        Map.prototype.forEach()：遍历 Map 的所有成员。 

##什么时候使用Object，什么时候使用Map  
    注意区分 Object 和 Map，只有模拟现实世界的实体对象时，才使用 Object。如果只是需要key: value的数据结构，使用 Map 结构。因为 Map 有内建的遍历机制。


##Javascript的事件流模型都有什么？    
    “事件冒泡”：事件开始由最具体的元素接受，然后逐级向上传播
    “事件捕捉”：事件由最不具体的节点先接收，然后逐级向下，一直到最具体的
    “DOM事件流”：三个阶段：事件捕捉，目标阶段，事件冒泡    

##Array 的迭代方法 有哪些？


##什么是深拷贝、浅拷贝， 什么情况下会浅拷贝？


##JS 作用域与作用域链 


##js是单线程还是多线程， 为什么不是多线程 ？


##什么是闭包，闭包解决了什么问题？



说说写JavaScript的基本规范？

JavaScript原型，原型链 ? 有什么特点？

JavaScript有几种类型的值？（堆：原始数据类型和 栈：引用数据类型），你能画一下他们的内存图吗？

Javascript如何实现继承？

Javascript创建对象的几种方式？

Javascript作用链域?

谈谈this对象的理解。

Webpack热更新实现原理?

请介绍一下JS之事件节流？

什么是JS的函数防抖？




# other  

##http状态码有那些？分别代表是什么意思？

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


##从输入URL到页面加载发生了什么

    DNS解析
    TCP连接
    发送HTTP请求
    服务器处理请求并返回HTTP报文
    浏览器解析渲染页面
    连接结束
    
##get和post的区别？
    
    GET：一般用于信息获取，使用URL传递参数，对所发送信息的数量也有限制，一般在2000个字符
    POST：一般用于修改服务器上的资源，对所发送的信息没有限制。
    GET方式需要使用Request.QueryString来取得变量的值，而POST方式通过Request.Form来获取变量的值，
    也就是说Get是通过地址栏来传值，而Post是通过提交表单来传值。
    
    然而，在以下情况中，请使用 POST 请求：
        ①无法使用缓存文件（更新服务器上的文件或数据库）向服务器发送大量数据（POST 没有数据量限制）。
        ②发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠。
    

    
##提高页面加载速度，你会做哪些优化？

    html 压缩
    图片懒加载
    css压缩
    js压缩
    cdn
    服务器配置使用 使用压缩文件
    等等...

    
    
##HTTP和HTTPS

    HTTP协议通常承载与 TCP协议之上，在HTTP和TCP之间添加一个安全协议层（SSL或TSL），这个时候，就成了我们常说的HTTPS
    默认HTTP的端口号为80，HTTPS的端口号为443
    
    
##跨域问题

    
    


#vue.js



##vm.$refs
 
    vm.$refs    一个对象，持有注册过 ref 特性 的所有 DOM 元素和组件实例。


## v-show  和 v-if  的区别    

##vuex


##怎么引入远程cdn的js


##打包的单个js较大怎么优化


##v-for  的keys使用什么值  keys的作用



##在下次 DOM 更新循环结束之后执行延迟回调
    
    Vue.nextTick( [callback, context] )
    
    在下次 DOM 更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的 DOM。
    
    
    
##Vue.use( plugin ) 是干什么   

    安装 Vue.js 插件。如果插件是一个对象，必须提供 install 方法。
    如果插件是一个函数，它会被作为 install 方法。install 方法调用时，会将 Vue 作为参数传入。
    该方法需要在调用 new Vue() 之前被调用。
    当 install 方法被同一个插件多次调用，插件将只会被安装一次。
    
##keep-alive

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
   
##mvvm    

    
##怎么声明404页面 


##.vue是怎么解析到浏览器可识别js




#angularjs2

##Angular 2 应用程序应用主要由以下 8 个部分组成：
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
    
    
    
#知识点
 
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
     
        
##设计模式

     mvc
     mvvm
     mvp
        
##other  

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
        
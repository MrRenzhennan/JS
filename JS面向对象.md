# 面向对象
面向对象的语言有一个标志,那就是它们都有类的概念,而通过类可以创建任意多个具有相同属性和方法的对象  
但是ECMAScript中没有类的概念,因此他们的对象也与基于类的语言中的对象有所不同,可以将ECMAScript对象理解为:  
包含多个键值对的集合,其中值可以是普通数据也可以是函数    
特点:  
**封装** 封装是把过程和数据包围起来,对数据的访问只能通过已定义的界面  
**继承** 派生类继承基类的属性和方法  
**多态** 多态是指两个或多个属性不同类的对象,对于同一个消息(方法调用)做出不同响应方式  

## [封装] 创建对象常见方式
### :one: 使用已有类型创建
```js
var obj = new Object();
var data = new Data
```
### :two: 直接使用字面量创建
```js
        //方法一:   直接使用字面量, 定义对象
        var obj = {}; //定义一个 空对象    没有属性和方法
        console.log(typeof obj); //得到这个对象的类型  (object)

        //向定义的变量中 添加属性和方法
        obj.name = "lisi"; //添加属性的属性值
        obj.age = 10;
        obj.say = function(str) { //添加方法
            console.log(str);
        };
        console.log(obj); //访问添加了属性和方法的对象

        //通过对象访问其中的属性和方法
        console.log(obj.name);
        console.log(obj.age);
        obj.say("hello world");
        obj.say("hi");

```
### :three: 构造函数模式,自定义构造函数的方式创建对象
```js
        //方法二:  利用构造函数的方式,生成对象
        function Person(name, age) {
            //那个对象调用的Person,  this 就指向对象
            console.log(this); //window
            this.name = name;
            this.age = age;
            this.say = function(str) {
                console.log("say : " + str);
            };
        }
        //直接在全局上调用 Person函数 ,所有添加的属性和方法都属于 window对象,也就是全局属性和方法
        Person("lisi", 22);
        console.log(window.Person); // 访问 Person 这个函数
        // console.log(window.Person.name); Person函数名
        //上面  使用了this 方法   this 指向 window, 所有在这里 可以直接 使用 window对象调用函数中的属性和方法
        console.log(window.name); //lisi
        console.log(window.age); //22
        window.say("hehe");


        //当Person被window 调用后  window.name 的name 就变成了  window 的一个属性,   window 是最大的一个全局,所以可以直接 调用属性
        say("hello----");
        console.log(name); //lisi
        console.log(age); //22

        //在 window这个全局里 定义 变量   可以在这个全局里 直接访问
        var value = 1000;
        console.log(window.value);


        //new 加上一个 函数名 ,  是将 这个函数 全部赋给这个变量  -------如果没有 new   那么是将这个函数的返回值赋给变量
        var one = new Person("zhangsn", 18);
        console.log(one); // 返回一个函数 ,并且 拥有自己传进的变量
        var two = new Person("wangwu", 28);
        console.log(two);

```
### :four:  原型模式  创建对象
创建的每个函数都有一个prototype(原型)属性,这个属性是一个指针,指向一个对象,  
而这个对象的用途是可以由特定类型的所有实例(对象实例化)共享的属性和方法
```js
        //方法三: 使用原型模式创建对象
        
        // 原型作用域链: 简单的讲就是将相同属性的变量用一个链 链接在一起  由下向上访问变量 直到找到停止
        //             最小作用域可以访问 到最大作用域     小作用域可以访问大作用域      大作用域 不能访问小作用域

        //Javascript中对象的prototype属性的解释是：返回对象类型原型的引用
        function Person1() {}
        Person1.prototype.name = "lisi"; //可以用prototype 直接为函数添加属性
        Person1.prototype.age = 12;

        one = new Person1(); // 用 new 方法  得到函数的全部属性
        one.name = "zhangsan"; //可以用new 方法定义的变量  直接访问 这个函数的属性
        console.log(one);

        two = new Person1();
        two.name = "wangwu";
        console.log(two);


```
### :five:  构造函数模式和原型模式结合
在原型模式中,每创建一个实例都会获得一样的属性值,为了让每个实例对象都有自己特有的属性值,可以将构造函数模式和原型模式相结合
```js
        //方法四: 构造函数模式和原型模式结合    (最常用的方法)
        function Stu(name, age) {
            this.name = name; //在函数里定义 this   谁调用 Stu 函数    name 就是谁的属性
            this.age = age; //在下面 我们将 函数 赋给了变量   那么 那个实例化的对象 将会调用这个函数    this==one
        }

        Stu.prototype.say = function(str) { //我们可以通过 prototype函数  为 我们定义的函数  添加方法
            console.log("say: " + str);
        };
        Stu.prototype.eat = function(str) { //方法可以添加 多个  不会发生冲突
            console.log("eat: " + str);
        }

        one = new Stu("liwu", 20); // 使用 new 方法  将函数的全部 赋给变量
        console.log(one);
        // console.log("0000", name);   //这种方法 是 在全局 window函数 下有 name 属性,那么才可以这样调用
        console.log(one.name); //
        one.say("wo shi one");
        one.eat("window shuo shi ")

        two = new Stu("liliu", 30); //将函数 赋给新的 实例化对象    背会与其他 对象 产生联系
        console.log(two);
        one.say("wo shi two")
```
## [继承]
### :one: 原型链继承
```js
        function Super() {
            this.superName = "Super"
        }
        Super.prototype.getSuperName = function() {
            console.log(this.superName);
        };



        function Sub() {
            this.subName = "sub";
        }
        Sub.prototype = new Super(); //将 Super函数的全部属性 通过 prototype方法 添加给 Sub函数 [new 方法 是 将函数的全部属性 赋给一个变量 ,prototype方法 是为函数添加熟悉性]
        //通过两个方法的结合使用  可以 实现不同函数,不同作用域之间 属性的继承

        Sub.prototype.getSubName = function() {
            console.log(this.subName);
        };

        var s = new Sub(); //将 Sub函数的属性 和在Super函数哪里继承来的属性   全部 通过new方法  赋给变量 s
        console.log(s);
        // console.log(s.getSuperName()); //super   可以通过实例化的对象 s   调用 自己的属性  和 继承 过来的属性
        // console.log(s.getSubName()); //sub
```
### :two: 原型链继承问题
```
1.所有实例共享属性,修改任意一个会影响其他实例
2.创建实例时无法传递参数
```
```js
        function F() {
            //这里注意 对象的类型,,,,数组类型 和 普通类型是不一样的
            this.colors = ["red", "blue", "black"];
            this.value = 10;
        };

        function S() {}
        S.prototype = new F();

        var one = new S();
        one.colors.push("green"); //为 colors 属性 的数组 添加一项

        one.value = 20; //通过这种 赋值  会覆盖 继承过来的 属性
        console.log(one);

        var two = new S(); //当再次 获得 S函数的属性时     在上面改变的 数组变量 会被储存 (也就是"green"会在这里出现),但是 不同变量不会改变
        console.log(two);

        var three = new S();
        console.log(three);

        console.log(S.prototype); //F {colors: Array[4], value: 10}
        /*继承过来的属性中,如果对数组进行了修改 那么在这个函数中 数组变量 将永远是修改后的样式  ;;;;;但是 普通变量将不会被改变,需要每次改变,修改一次*/
```
### [call/apply]借用构造函数的继承
```js
        function Super(name, age) {
            this.name = name;
            this.age = age;
        };

        function Sub(name, age, id) {
            Super.call(this, name, age); //call方法    调用Super函数的方法 自己用
            //console.log(this); //Sub {name: "lisi", age: 10}
            this.id = id;
        }

        var one = new Sub("lisi", 10, 1000);
        console.log(one); //Sub {name: "lisi", age: 10, id: 1000}
```
[call和apply的区别]
```js
        /************************************************************************/
        //call 和 apply 方法的应用
        console.log(Math.max.apply(null, [1, 2, 3, 4, 5])); //5
        console.log(Math.max.call(null, [1, 2, 3, 4, 5])); //NaN
        /*call, apply都属于Function.prototype的一个方法,它是JavaScript引擎内在实现的,因为属于Function.prototype,所以每个Function对象实例,也就是每个方法都有call, apply属性.
        既然作为方法的属性,那它们的使用就当然是针对方法的了.这两个方法是容易混淆的,因为它们的作用一样,只是使用方式不同.
        call方法:
        语法：call([thisObj[,arg1[, arg2[,   [,.argN]]]]])
        定义：调用一个对象的一个方法，以另一个对象替换当前对象。
        说明：
        call 方法可以用来代替另一个对象调用一个方法。call 方法可将一个函数的对象上下文从初始的上下文改变为由 thisObj 指定的新对象。
        如果没有提供 thisObj 参数，那么 Global 对象被用作 thisObj。
        apply方法：
        语法：apply([thisObj[,argArray]])
        定义：应用某一对象的一个方法，用另一个对象替换当前对象。
        说明：
        如果 argArray 不是一个有效的数组或者不是 arguments 对象，那么将导致一个 TypeError。
        如果没有提供 argArray 和 thisObj 任何一个参数，那么 Global 对象将被用作 thisObj， 并且无法被传递任何参数
        它们的不同之处：
        apply：最多只能有两个参数——新this对象和一个数组 argArray。如果给该方法传递多个参数，则把参数都写进这个数组里面，当然，即使只有一个参数，也要写进数组里面。
              如果 argArray 不是一个有效的数组或者不是 arguments 对象，那么将导致一个 TypeError。
              如果没有提供 argArray 和 thisObj 任何一个参数，那么 Global 对象将被用作 thisObj， 并且无法被传递任何参数。
        call：则是直接的参数列表，主要用在js对象各方法互相调用的时候，使当前this实例指针保持一致,或在特殊情况下需要改变this指针。
              如果没有提供 thisObj 参数，那么 Global 对象被用作 thisObj。
        更简单地说，apply和call功能一样，只是传入的参数列表形式不同：如 func.call(func1,var1,var2,var3)对应的apply写法为:func.apply(func1,[var1,var2,var3])
        call, apply作用就是借用别人的方法来调用,就像调用自己的一样
        */

        var obj = {
            num: 10
        };
        var num = 20;

        function showNum() {
            console.log("this.num = " + this.num);
        }

        showNum(); //20   在window上调用该函数
        //给一个方法 或函数换一个环境执行   这时 函数中的 this 全部指向 call或apply 指向的对象
        //call和apple方法的基本区别:call方法参数(可以是数组)是以逗号","作为分隔符的; apple方法 参数只能是数组
        showNum.call(obj); // 10   在obj对象上调用showNum函数     call 作用 借用 obj对象的属性
        showNum.apply(obj, null); //10  在obj对象上调用showNum函数     apply 作用 借用obj对象的属性
```
### [组合继承] 原型链继承和借用构造函数继承相结合
```js
        function F() {
            this.name = name;
            this.colors = ["red", "green", "blue"];
        };
        F.prototype.getName = function() { //为 F函数添加方法      prototype 添加方法
            console.log(this.name);
        };

        function S(name, age) {
            F.call(this, name); //call 方法 将F函数的name属性 继承 自己使用    call方法  添加属性
            this.age = age;
        };

        S.prototype = new F(); //将 F函数的全部属性 全部 给S函数
        S.prototype.constructor = S;
        S.prototype.getAge = function() {
            console.log(this.age);
        };

        one = new S("zhangsan", 33);
        one.colors.push("black");

        console.log(one);
        console.log(one.colors); //["red", "green", "blue", "black"]
        one.getName();
        one.getAge();

        two = new S("zhangliu", 23);
        console.log(two.colors); //["red", "green", "blue"]

        console.log(typeof one); //object
        console.log(one.constructor); // functionS(){} 得到某个对象是由那个对象生成
```

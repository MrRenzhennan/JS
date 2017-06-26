## 函数

## javascript函数
函数对任何语言来说都是一个核心的概念。通过函数可以封装任意多条语句,而且可以在任何地方、任何时候调用执行。
```js
javascript函数示例:
function sum(arg1,arg2){
  return arg1 + arg2;
}
sum(1,2)
```
### 函数声明:
```js
//函数声明
function fun(){
  console.log("fun....");
}
fun();//函数调用


var fun1 = function(){
  console.log("fun1....");
};
fun1();//函数表达式的调用必须在定义之后

```
## 函数传参
```js
function fun(arg1,arg2){
  console.log(arg1 + arg2);
}
fun(1,2);

其中arg1,arg2为传递的形参，fun(1,2)中的数值为实参
```
## arguments对象
arguments是储存了函数传送过来的实参,并且arguments对象只有函数开始时才可用.  
arguments对象只是与数组类似(它并不是Array的实例),因为可以使用方括号语法访问它的每一个元素  
(即第一个元素argument是[0],第二个元素是argument[1],以此类推),  
使用length属性来确定传递进来多少参数.  
```
function fun(arg1,arg2) {
       console.log(fun.length);
       console.log(arguments.length);
       console.log(arguments[0]);
       console.log(arguments[1]);
   }
fun(1,2);
```
## 函数声明变量提升
1. function函数的作用域里的变量可以使用外层作用域的变量.
2. 在function作用域内,变量的声明被提升了,但是注意:`变量赋值并没有被提升,只是声明被提升了`  
```
var value = 10;
function fun(){
  console.log(value);
  var value = 20;
}
fun();//结果为undefined
```
## 函数的返回值
函数调用一次之后表示运算完毕,使用`return`关键字可以返回结果,同样return可以提前结束函数的运行
```
function fun(arg1,arg2){
  return arg1 + arg2;
  console.log("after return ...");//不会执行
}
fun();//返回计算结果

function fun1(arg1){
  console.log(arg1);
  return;//返回undefined
}
```
## 函数的闭包
闭包是指有权访问另一个函数作用域中的变量的函数,  
创建闭包的常见方式,就是在一个函数内部创建另一个函数
```js
function  fun() {
    var a = 10;
    return function(){
        for (var i = 0; i++; i < 5){
            a++;
        }
        console.log(a);
    };
}
var ret = fun();
ret(); //调用返回的函数，仍热可以访问fun中定义的局部变量a
```
###  函数闭包的特点
**优点:** 可以 减少全局变量的定义,实现变量私有化  
**缺点:** 私有变量会常驻内存,直到该变量使用完毕,会增加内存的消耗

## 函数绑定
函数绑定要创建一个函数,可以在特定的this环境中以指定参数来调用另一个函数,该技巧常常和回调函数与事件处理程序一起使用,  
以便在将函数作为变量传递的同时保留代码执行环境.  
**自定义绑定函数**
```js
        var btn = document.getElementById("btn");
        btn.data = 10;
        var data = 20;

        function handler() {
            console.log(this.data);
        };
        btn.addEventListener("click", handler, false); //10  handler函数在 btn 环境中调用,所以 this 指的是btn   btn.data = 10;

        btn.addEventListener("click", function() {
            console.log(this); //<button id="btn" type="button" name="button">点击</button>
            handler(); //20

            handler.call(btn) //10  call 方法继承btn.data的属性
        }, false)
```
#### **内置的bind方法:**  fun.bind(thisArg[, arg1[, arg2[, …]]])  
**thisArg** 当绑定函数被调用时,该参数会作为原函数运行时的this指向.  
              当使用new操作符调用绑定函数时,该参数无效  
**arg1, arg2, … ** 当绑定函数被调用时,这些参数加上绑定函数本身的参数会按顺序作为原函数运行时的参数  
**返回值**  返回由指定的this值和初始化参数改造的原函数拷贝
```js
var newFn = fn.bind(context, arg1, arg2...);
```
```js
        function fn() {
            console.log("参数的总个数:" + arguments.length);
            //.arguments 返回函数 传入的总参数    并以数组的形式呈现
            for (var i = 0; i < arguments.length; i++) {
                console.log(arguments[i]);
            }
        }
        // fn(1, 2, 3);


        //bind 方法 还可提前给函数传递一些参数  [会在函数调用之前传参]
        var newFn = fn.bind(this, 4, 5, 6, 7, 8);
        newFn(1, 2, 3)

        console.log(" /*************************************/");

        //实现一个完整的bind函数
        function bind(fn, context) {
            //arguments的返回值是一个伪数组,没有slice方法,call方法可以将伪数组变成真数组
            var preArg = Array.prototype.slice.call(arguments, 2); //输出数组下标为2以后的元素
            console.log(preArg); //[1,2,3,4]
            return function() {
                /*concat()方法用于合并两个或者多个数组.此方法不会改变数组,而是返回一个新数组
                concat 方法将创建一个新的数组，然后将调用它的对象(this 指向的对象)中的元素以及所有参数中的数组类型的参数中的元素以及非数组类型的参数本身按照顺序放入这个新数组,并返回该数组.
                concat 方法并不修改调用它的对象(this 指向的对象) 和参数中的各个数组本身的值,而是将他们的每个元素拷贝一份放在组合成的新数组中.原数组中的元素有两种被拷贝的方式:
                      1).对象引用(非对象直接量):concat 方法会复制对象引用放到组合的新数组里,原数组和新数组中的对象引用都指向同一个实际的对象,所以,当实际的对象被修改时,两个数组也同时会被修改.
                      2).字符串和数字(是原始值,而不是包装原始值的 String 和 Number 对象): concat 方法会复制字符串和数字的值放到新数组里.
                语法:var new_array = old_array.concat(value1[, value2[, ...[, valueN]]])
                将old_array数组与多个valueN数组合并*/
                var arg = preArg.concat(Array.prototype.slice.call(arguments, 0));
                //console.log(Array.prototype.slice.call(arguments, 0)); //[5,6,7,8]
                // console.log(arg); //[1,2,3,4,5,6,7,8]
                return fn.apply(context, arg);
            }
        }

        var newFn1 = bind(fn, this, 1, 2, 3, 4);
        newFn1(5, 6, 7, 8)

        //注意伪数组
        function test(arg1, arg2) {

            //arguments 是一个伪数组,没有slice方法
            // console.log(arguments.slice(0));//报错

            //使用call方法,可以将假数组方做真数组使用
            console.log(Array.prototype.slice.call(arguments, 0));
        };
        test(1, 2)
```
## 函数柯里化
与函数绑定紧密相关的主题是函数柯里化(function currying),它用于创建已经设置好了一个或多个参数的函数,  
函数柯里化的基本方法和函数绑定是一样的: 使用一个闭包返回一个函数  
功能:对函数进行柯里化  
@fn:用于计算函数  
@rate:提前传递给fn的参数    
柯里化通常也称为部分求职,其含义是给函数部分作用域传参,每次传递参数后部分应用参数,并返回一个更具体的函数,接收剩下的参数,  
这中间可嵌套多层这样的接受部分参数函数,直至返回最后的结果,因此柯里化的过程是逐步传参,逐步缩小函数的使用范围,逐步求解的过程
```js
        function curry(fn, rate) {
            //call方法 将 arguments返回的伪数组变成真数组   利用分片将参数传递出来
            var preArg = Array.prototype.slice.call(arguments, 1); //0.8
            return function() {
                //concat()将分离的参数进行合并
                var arg = preArg.concat(Array.prototype.slice.call(arguments, 0)); //400
                //不进行this绑定,只是为了得到arg参数
                return fn.apply(null, arg); //count函数在这里被调用   将参数 传给count值    apply(null,arg) 实现了函数的传参,并不敢变函数的作用域
            }
        };

        function count(price) {
            console.log("商品结算价格: " + arguments[0] * arguments[1]);
        }
        var newCount = curry(count, 0.8);
        newCount(400); //调用函数闭包

        newCount = curry(count, 0.5);
        newCount(400);
```
## 函数记忆[函数的缓存]
函数记忆是构建函数的过程,这种函数能够记住之前的计算结果,从而可以避免再次执行已经完成的复杂计算,  
这种方式可以显著的提高代码的性能
```js
        //判断一个函数是否为质数
        function isPrime() {
            if (!isPrime.result) { //如果没有这个对象       !取反
                isPrime.result = {} //定义一个空对象   用于储存 返回的属性值
            }

            if (isPrime.result[num] != null) { //如果传入的参数 能在创建的对象中 找到对应的值 那么
                return isPrime.result[num]; //返回 这个属性对应的值
            }

            console.log("num = " + num);

            var result = true;
            for (var i = 0; i < num; i++) { //质数   能被1或本身整除
                if (num % i == 0) { //如果 num 能被  1--num 之间的数整除  那么 取余数为零 ,,    就不是质数
                    result = false;
                    break;
                }
            }

            return isPrime.result[num] = result; //如多新建的数组中 没有 这个属性,,,,   会将 传入的参数 和 返回的 值     存入到新建的对象中
        }
```
## 高阶函数
高阶函数其实就是传入一个或者多个参数,返回一个函数
```js
        //判断是否为偶数
        function even() {
            return (num % 2 == 0) ? true : false; //三元算法     num%2==0 成立  返回true   不成立返回 false
        }
        console.log(even(20));
        console.log(even(21));



        //not函数用于将原函数的结果给取反
        function not(fn) {
            return function() {
                //.apply(null, arguments)  不改变函数的作用域,并将函数传入even函数
                var ret = fn.apply(null, arguments); //even()函数 在这里调用,  并将闭包函数中的参数传入 even()函数
                return !ret;
            }
        }

        var odd = not(even);
        console.log(odd(3)); //  !false = true
        console.log(odd(4)); //  !true  =  false
```
```js
//实现两个数的和的平方
        $(document).ready(function() {
            $("#btn").click(function() {
                var val = $("#val").val();
                var reg = /(\d*)\+(\d*)/;
                var font1 = parseInt(val.match(reg)[1]);
                var font2 = parseInt(val.match(reg)[2]);

                function sum(a, b) {
                    var c = a + b;
                    return c
                }

                function squ(num) {
                    return function() {
                        var ret = num.apply(null, arguments);
                        return ret * ret;
                    }
                }
                var s = squ(sum);
                var que = s(font1, font2)
                $("p span").text(que);
            })
        })

```
## 定时器节流
JavaScript单线程的本质可能是使用JavaScript创建大规模复杂应用程序最大的陷阱,浏览器中某些计算和处理要比其他的昂贵很多,  
例如:DOM操作比起非DOM交互需要更多的内存和CPU时间,在低版本的IE中使用onresize事件程序的时候容易发生,当调整浏览器大小时,  
该事件会连续触发,在onresize事件处理程序内部,如果尝试进行DOM操作,其高频率的更改可能会让浏览器崩溃,  

为了绕开这个问题,你可以使用定时器对该函数进行节流,函数节流背后的基本思想是指:某些代码不可以在没有间断的情况连续重复执行,  
对一次调用函数,创建一个定时器,在指定的时间间隔之后运行代码,  
当第二次调用该函数时,它会清除前一次的定时器并设置另一个
```js
        $("body").click(function() {
            console.log("click ...");
        });


        /*    //生成100000行数据
          for (var i = 0; i < 10000; i++) {
            $("<tr><td>lisi</td><td>10</td><td>1001</td></tr>").appendTo($("#table"));
          }

        */

        var timer = null;
        var num = 0;

        function fun() {
            $("<tr><td>lisi</td><td>10</td><td>1001</td></tr>").appendTo($("#table"));

            num++;
            if (num == 10000) {
                clearTimeout(timer); //当执行完 任务 ,结束定时器
                return;
            }

            //实现了函数节流，可以保证在插入数据的同时，还可以响应点击事件,
            //间隔事件可以设置的额很短
            timer = setTimeout(fun, 1);
        }

        fun();
```
## 单列模式
单列模式是JavaScript中最基本但是又最有用的模式之一,它提供了一种将代码组织为一个逻辑单元手段,这个逻辑单元中的代码可以通过  
单一的变量进行访问,通过保证单利模式只有一个,就可以确保使用的都是同样的全局资源,  
单列在JavaScript中有许多用途,可以用来划分命名空间,以减少网页中的全局变量的数目,还可以在一种名为分之的技术中用来封装浏览器之间的  
差异,更重要的是借助于单例模式,可以把代码组织的更为有效,从而更容易阅读和维护.  
#### :one: **最简单的单例模式**  
使用对象的字面量创建方式实际上就是一个最简单的单例模式
```js
var obj = {
  name: "lisi",
  age: 10,
  adult: true,
  eat: function(){...},
  drink: function(){...}
};
```
#### :two: **使用匿名函数创建单例模式**  
通过闭包创建包含私有成员的单利对象
```js
        var obj = (function() {
            var privateA = 1;
            var privateB = 2;

            function privateFn1() {
                return privateA
            };

            function privateFn2() {
                return privateB
            };

            return {
                publicA: 3,
                publicB: 4,
                publicFn1: function() {
                    return privateFn1();
                },
                publicFn2: function() {
                    return privateFn2();
                }
            }
        })();
        console.log(obj);
        console.log(obj.publicA);
        console.log(obj.publicB);
        console.log(obj.publicFn1);
        console.log(obj.publicFn2);
```
#### :three: 使用惰性方式创建单列对象
对于资源密集型或者配置开销很大的单利对象，更合理的做法时将其实例化推迟到需要使用的时候。这种技术被成为被成为惰性加载。  
惰性加载的特殊之处就是需要借助一个静态方法，需要检查创建单例对象时，该对象是否已经存在。  
使用惰性加载单例模式的的缺点就是代码稍显复杂，不容易理解。
```js
        var mySingleton = (function() {
            var exist = null;

            function Singleton() {
                var privateA = 10;
                var privateB = 20;

                function privateFn1(value) {
                    privateA = value;
                }

                function privateFn2() {
                    return privateA;
                }

                return {
                    publicA: 30,
                    publicB: 40,
                    setPrivateA: function(value) {
                        privateFn1(value);
                    },
                    getPrivateA: function() {
                        return privateFn2();
                    }
                }
            }
            return {
                getInstance: function() {
                    if (!exist) {
                        exist = Singleton();
                    }
                    return exist
                }
            }
        })();

        console.log(mySingleton);

        //singleOne就是一个全局唯一的单列对象
        //singleTwo 和 singleTwo 是同一个对象
        var singleOne = mySingleton.getInstance();
        var singleTwo = mySingleton.getInstance();

        singleOne.publicA = 300;
        console.log(singleOne);
        console.log(singleTwo);
```
## 工厂模式
在创建对象时常用new关键字和构造函数，而这又会导致两个类之间产生依赖性。  
工厂模式有助于消除两个类之间的依赖性。  
工厂模式是将成员对象的实例化推迟到子类中进行的类。  
工厂模式的主要好处在于消除对象之间的耦合，可以将代码集中一个位置。  
**简单工厂代码**
```js
function PhoneShop(){
}

PhoneShop.prototype = {
    constructor: PhoneShop,
    sellPhone: function(mode){
        return createPhone(mode);
    }
};

function createPhone(mode){
    var phone = null;
    switch (mode){
        case "iphone":
            phone = new Apple();
            break;
        case "huawei":
            phone = new Huawei();
            break;
    }
    return phone;
}
```
**真正的工厂模式**
```js
function Super(){
}

Super.prototype = {
    constructor: Super,
    sellPhone: function(mode){
      var phone = this.createPhone(mode);
      return phone;
    },
    createPhone: function(mode){
        throw new Error("it is a abstract class!");
    }
};

function Sub(){
  Super.call(this);
}
inherit(Super, Sub);
//子类实现自己的方法
Sub.prototype.createPhone = function(mode){
  ....;
}
```




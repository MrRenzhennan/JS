# javascript 语言介绍
JavaScript一种直译式脚本语言，是一种动态类型、弱类型、基于原型的语言，内置支持类型。  
它的解释器被称为JavaScript引擎，为浏览器的一部分，广泛用于客户端的脚本语言，  
最早是在HTML（标准通用标记语言下的一个应用）网页上使用，用来给HTML网页增加动态功能。
# 组成部分
ECMAScript，描述了该语言的基本语法。  
文档对象模型（DOM），描述处理网页内容的方法和接口。  
浏览器对象模型（BOM），描述与浏览器进行交互的方法和接口。  
# 基本特点
JavaScript是一种属于网络的脚本语言,已经被广泛用于Web应用开发,常用来为网页添加各式各样的动态功能,为用户提供更流畅美观的浏览效果。  
通常JavaScript脚本是通过嵌入在HTML中来实现自身的功能的。  
1.是一种解释性脚本语言（代码不进行预编译）。  
2.主要用来向HTML（标准通用标记语言下的一个应用）页面添加交互行为。  
3.可以直接嵌入HTML页面，但写成单独的js文件有利于结构和行为的分离。  
4.跨平台特性，在绝大多数浏览器的支持下，可以在多种平台下运行（如Windows、Linux、Mac、Android、iOS等）  
# javascript 的作用
* 嵌入动态文本于HTML页面。
* 对浏览器事件做出响应。
* 读写HTML元素。
* 在数据被提交到服务器之前验证数据。
* 检测访客的浏览器信息。
* 控制cookies，包括创建和修改等。
* 基于Node.js技术进行服务器端编程。

# javascript的编写
1. 行内样式  
`<button onclick="alert();"></button>`
2. 嵌套样式
```js
<script>
   var btn = document.getElementById("btn");
   btn.onclick = function(event){....};
</script>
```
3. 外部文件
```js
<script src="xxx/yyy.js">此处不要写东西</script>
```
# javascript基本概念
## 严格区分大小写
第一个概念就是 ECMAScript 中的一切(变量、函数名和操作符)都区分大小写。  
这也就意味着,变量名 test 和变量名 Test 分别表示两个不同的变量,而函数名不能使用 typeof ,因为它是一个关键字,  
但 typeOf 则完全可以是一个有效的函数名.
## 标识符
所谓标识符,就是指变量、函数、属性的名字,或者函数的参数。标识符可以是按照下列格式规则  
组合起来的一或多个字符:  
1. 第一个字符必须是一个字母、下划线( _ )或一个美元符号( $ )其他字符可以是字母、下划线、美元符号或数字。
2. 标识符中的字母也可以包含扩展的 ASCII 或 Unicode 字母字符(如 À 和 Æ),但我们不推荐这样做。
3. 按照惯例,ECMAScript 标识符采用驼峰大小写格式,也就是第一个字母小写,剩下的每个单词的首字母大写,  
   例如: firstChild getSelectionText
## 注释风格
1. 单行注释 “//”
`//这里是单行注释 `

2. 多行注释 "/* */"
```js
/*
 这里是多行注释
*/
```
`注意：`不要和python，html中的注释混淆。
## 语句
ECMAScript 中的语句以一个分号结尾;如果省略分号,则由解析器确定语句的结尾, 比如：　
```js
var  value1 = a - b    //不推荐　     
var  value2 = a + b;　 //推荐      
```
使用代码块，让代码看起来更加清晰, 比如：　　
```js
//不推荐
if (value)
    alert("value is ...");

//推荐
if (value) {
   alert("value is ...");
}
```
## 关键字
### 注意:定义标识符时,不要使用关键字和保留字  
可查看ECMA文档
[ECMA中文文档](https://www.ibm.com/developerworks/cn/web/wa-ecma262/)
## jsvascript变量
ECMAScript 的变量是松散类型的,所谓松散类型就是可以用来保存任何类型的数据。  
换句话说,每个变量仅仅是一个用于保存值的占位符而已。定义变量时要使用 var 操作符。　　　　　
比如：
```js
var  a, b;   
var  c = 10, d = "hello";

a = 10; //a开始是数值类型
a = "world"; //重新赋值变为字符串类型，可以，但是不推荐这样做。


function test(){
  var value = 234;// 局部变量,函数调用完毕之后立刻销毁
  test = "string";//定义全局变量
  ....
}
```
## 变量作用域
区分: 全局变量，局部变量
```js
var a = 10; //全局变量
function test(){
  var a = b = 20 ;
  console.log(a);//访问局部变量ａ
}
console.log(b);//错误，无法访问局部变量b
```
## javascript 数据类型
ECMAScript 中有 5 种简单数据类型(也称为基本数据类型): Undefined, Null, Boolean, Number和 String 。  
对一个值使用 typeof 操作符可能返回下列某个字符串:  
* “undefined” ——如果这个值未定义;
* “boolean” ——如果这个值是布尔值;
* “string” ——如果这个值是字符串;
* “number” ——如果这个值是数值;
* “object” ——如果这个值是对象或 null ;
* “function” ——如果这个值是函数。
比如:
```js
var a = "string";
 alert(typeof a); //string

 var b = 123;
 alert(typeof b); //number

 var c = true;
 alert(typeof c);//boolean

 var d;
 alert(typeof d);//undefined

 var f = function(){alert("hello");};
 alert(typeof f);//function

 var e = null;
 alert(typeof e);//object    
```
## 字符串类型
String 类型用于表示由零或多个 16 位 Unicode 字符组成的字符序列,即字符串。  
字符串可以由双引号(")或单引号(’)表示,因此下面两种字符串的写法都是有效的:
```js
var a = "string1";
var b = 'string2';
```
注意:不要混合使用单引号或者双引号，要同一，否则会报错.  
ECMAScript 中的字符串是不可变的,也就是说,字符串一旦创建,它们的值就不能改变。  
要改变某个变量保存的字符串,首先要销毁原来的字符串,然后再用另一个包含新值的字符串填充该变量, 比如：  
`var lang = "java"; lang = "java" + "script"; `  
其他类型转换为字符串的方法toString(), 比如：　
```js
var a = 10;
console.log(a.toString());
console.log(a.toString(2));//转换为２进制，“1010”
console.log(a.toString(8));// “12”
console.log(a.toString(10));// “10”
console.log(a.toString(16));// “a”

var b = false;
console.log(b.toString());
```
在不知道要转换的值是不是 null 或 undefined 的情况下,还可以使用转型函数 String() ,  
这个函数能够将任何类型的值转换为字符串。
```js
var a = null;
console.log(String(a));//null
var b = undefined;
console.log(String(b));//undefined
```
## 布尔类型
boolean 类型是 ECMAScript 中使用得最多的一种类型,该类型只有两个字面值: true 和 false 。　　　　　
```js
var a = true;
var b = false;
```
将一个值转换为其对应的 Boolean 值,可以调用转型函数 Boolean().
```js
var a = 10;
console.log(Boolean(a));

var b = "hello";
console.log(Boolean(b));
```
数据类型|转换为true的值|转换为false的值
------|-----------|-------------
Boolean|trun|false
String|任何非空字符串|""(空字符串)
Number|任何非零数字值(包括无穷大)|0和NaN
Object|任何对象|null
Undefined|!undefined|undefined
```js
var a = 10;
if (a) {
  alert("a is exist ...");
}
```
## 数值类型
最基本的数值字面量格式是十进制整数,除了以十进制表示外,整数还可以通过八进制(以 8 为基数)或十六进制(以 16 为基数)的字面值来表示。  
比如：
```js
var a = 123;
var b = 0123;//8进制使用'0' 开头
var c = 0x123; //16进制，使用"0x"开头
```
## 浮点数
所谓浮点数值,就是该数值中必须包含一个小数点,并且小数点后面必须至少有一位数字,  
比如：　
```js
var a = 10.12;
var b = 0.12;
var c = .123; //不推荐
```
对于那些极大或极小的数值,可以用 e 表示法(即科学计数法)表示的浮点数值表示,   
比如：
```js
var a = 3.5e7; //表示3.5 * 10^7
var b = 3.5e-7; //表示 3.5 * 10^-7;
```
浮点数值的最高精度是 17 位小数,但在进行算术计算时其精确度远远不如整数。  
例如,0.1 加 0.2的结果不是 0.3,而是 0.30000000000000004。  
这个小小的舍入误差会导致无法测试特定的浮点数值。　　　
```js
//if条件不成立
if ((a + b) == 0.3 ) {
  alert("a+b==0.3");
}
```
## NaN
NaN ,即非数值(Not a Number)是一个特殊的数值,这个数值用于表示一个本来要返回数值的操作数未返回数值的情况(这样就不会抛出错误了)。  
ECMAScript 定义了isNaN() 函数。这个函数接受一个参数,该参数可以是任何类型,而函数会帮我们确定这个参数是否“不是数值”。
```js
alert(isNaN(NaN));//true
alert(isNaN(10));//false
alert(isNaN("blue"));//true
alert(isNaN("10"));//false
alert(isNaN(true));//false
```
## 未定义类型
Undefined 类型只有一个值,即特殊的 undefined 。在使用 var 声明变量但未对其加以初始化时,  　　　　　
这个变量的值就是 undefined, 或者显式的进行undefined赋值操作，
比如:  
```js
var a ;
var b = undefined;
console.log(tyepf a);// undefined
console.log(tyepf b);// undefined
```
对于尚未声明过的变量,只能执行一项操作,即使用 typeof 操作符检测其数据类型(对未经声明的变量调用 delete 不会导致错误,  
但这样做没什么实际意义,而且在严格模式下确实会导致错误)。
```js
console.log(c);//出现错误，因为没有定义变量c
console.log(typeof c); //undefined
```
## Null类型
Null 类型是第二个只有一个值的数据类型,这个特殊的值是 null 。  
从逻辑角度来看, null 值表示一个空对象指针,而这也正是使用 typeof 操作符检测 null 值时会返回 “object” 的原因,  
比如：
```js
var a = null;
console.log(typeof  a);//object
```
如果定义的变量准备在将来用于保存对象,那么最好将该变量初始化为 null 而不是其他值,  
然后可以判断变量是否包含对象来做对应的操作，  
比如：
```js
if (a != null) {
  ....
}
```
## Js数值转换
有三个函数可以把非数值转换为数值: Number() 、 parseInt() 和 parseFloat() 。  
**Number()** 即转型函数 Number() 可以用于任何数据类型,而另两个函数则专门用于把字符串转换成数值。　　　　
```
var num1 = Number("Hello world!"); //NaN
var num2 = Number("");//0
var num3 = Number("000011");//11
var num4 = Number(true);//1
```
**parseInt()**  函数在转换字符串时,更多的是看其是否符合数值模式。它会忽略字符串前面的空格,直至找到第一个非空格字符。
如果第一个字符不是数字字符或者负号, parseInt()就会返回 NaN ;也就是说,用 parseInt() 转换空字符串会返回 NaN ( Number() 对空字符返回 0)。　　
如果第一个字符是数字字符, parseInt() 会继续解析第二个字符,直到解析完所有后续字符或者遇到了一个非数字字符。
`例如, “1234blue” 会被转换为 1234,因为 “blue” 会被完全忽略。类似地, “22.5”会被转换为 22,因为小数点并不是有效的数字字符。`
```
console.log(parseInt(""));//NaN
console.log(parseInt("1234abc"));//1234
console.log(parseInt("abc"));//NaN
console.log(parseInt("10.123"));//10
console.log(parseInt("0x12"));//18
console.log(parseInt("070"));//70, 并没有解析为８进制
```
为了消除在使用 `parseInt()` 函数时可能导致的上述困惑,可以为这个函数提供第二个参数:转换时使用的基数(即多少进制)。
```
console.log(parseInt("010", 8));
console.log(parseInt("10", 2));
console.log(parseInt("20",2));//超过范围时，转换为NaN
console.log(parseInt("10", 10));
console.log(parseInt("10", 16));
```
**parseFloat()** 也是从第一个字符(位置 0)开始解析每个字符, 都按照十进制解析。而且也是一直解析到字符串末尾,或者解析到遇见一个无效的浮点数字字符为止。也就是说,字符串中的第一个小数点是有效的,而第二个小数点就是无效的了,因此它后面的字符串将被忽略。　
```
console.log("----parseFloat---------");
console.log(parseFloat("10.234")); //10.234
console.log(parseFloat("10.abc"));//10
console.log(parseFloat("10.23.4"));//10.23
console.log(parseFloat("0x10.234"));//0
console.log(parseFloat("010.234"));//10.234
console.log(parseFloat("abc"));//NaN
```

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

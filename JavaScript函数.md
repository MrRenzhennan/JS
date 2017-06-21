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

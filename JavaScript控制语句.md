# javascript语句
## if语句
if (condition)  
statement1  
else  
statement2  

if (i > 25){  
alert(“Greater than 25.”);//单行代码  
}  
else {  
alert(“Less than or equal to 25.”);//代码块  
}  
```js
var a = 5;
if (a > 5){
  xxxxx;
} else if (a == 5){
  yyyyy;
} else {
  zzzz;
}
```
## while语句
while 语句属于前测试循环语句,也就是说,在循环体内的代码被执行之前,就会对出口条件求值。
```js
while (condition){
  statement
}
```
## for循环
for 语句也是一种前测试循环语句,但它具有在执行循环之前初始化变量和定义循环后要执行的代码的能力。  
以下是 for 语句的语法:
```js
for (initialization; expression; post-loop-expression){
statement
}

for(var i = 0; i < 10; i++){
  alert(i);
}

for(;;){
  //无限循环
}

for (;i < count;){
  //类似while循环
  i++;
}
```

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
## break和continue
break 和 continue 语句用于在循环中精确地控制代码的执行。  
**break**  语句会立即退出循环,强制继续执行循环后面的语句。  
**continue**  语句虽然也是立即退出循环,但退出循环后会从循环的顶部继续执行。
```
for(var i = 0; i < 10; i++){
    if (i == 5){
       break;
     }
    alert(i);
  }

  for (var i = 0; i < 5; i++){
    if (i < 5){
      continue;
    }
    alert(i);
  }
```
## label语句
使用 label 语句可以在代码中添加标签,以便将来使用.  
label 语句的语法:label: statement
```
label-one: for (var i = 0; i < 10; i++) {
              if (i == 5){
                break label-one;
              }
}
```
## with语句
with 语句的作用是将代码的作用域设置到一个特定的对象中,建议少用。  
with 语句的语法如下:with (expression) statement;　 
```
with(location){
  console.log(search.substring(1));//location.search.substring(1)
  console.log(hostname);//location.hostname
}
```
## switch语句
switch 语句与 if 语句的关系最为密切,而且也是在其他语言中普遍使用的一种流控制语句。　　　　　　　　　
switch 语句中使用任何数据类型(在很多其他语言中只能使用数值),无论是字符串,还是对象都没有
问题。其次,每个 case 的值不一定是常量,可以是变量,甚至是表达式。
```
switch(expression) {
  case value1:
       statement
       break;
   case value2:
       statement
       break;
   default:
       statement
       break;
}
//注意break关键字，否则会导致执行多个case语句。
```

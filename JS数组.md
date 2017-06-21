# :exclamation: 数组
数组是值的有序集合，每个值就是一个元素，每个元素在数组中有一个位置，以数字表示，成为索引。　　　　　
javascript数组是无类型，数组元素可以是任意类型，并且同一个数组中的不同元素也可能是不同的类型。　 　　

## :one: 创建数组
**使用数组直接变量进行创建,方括号中使用逗号隔开**
```
var a = [];
var b = [10,2,3];
var c = [1.1,true,'a'];
var d = [1,2,,3];  //其中省略的元素值为undefined
```
**使用Array()创建**
```
var a = new Array();//创建空数组
var b = new Array(10);//创建长度为10的元素
var c = new Array(1,2,3);//创建一个已经包含三个元素的数组
```
## :two: 数组读写操作
```
var a = ["hello"];
var b = a[0];
a[1] = "world";
i = 1;
a[i + 2] = "string";
```
## :three: 数组长度
```
var a = [1,2,3,4];
console.log(a.length); //长度为４

a[999] = 999; //长度为　1000, 稀疏数组的长度大于元素的个数
console.log(a.length);// 长度为1000
```
## :four: 数组元素的添加和删除
```
添加：
直接对新索引赋值:
var a = [];
a[0] = "hello";
a[1] = "word";

使用push方法在数组末尾添加一个或者多个元素:
var a = [];
a.push("hello");
a.push("world","google");
```
```
删除：
直接删除数组元素:
var a = [1,2,3];
delete a[0];//不会改变元素的索引位置
a.length; //数组长度没有发生变化

使用pop,shift方法删除数组的一个元素：
a.pop();//删除最后一个
a.shift();//删除开头一个,会改变元素的索引位置
```
## :fire: 数组的遍历
使用for循环是最常见的遍历数组的方法：
```
var a = [1,2,3,4];
for (var i = 0; i < a.length; i++) {
   console.log(a[i]);
}

//提高效率
for (var i = 0, len = a.length; i <len ; i++) {
   console.log(a[i]);
}

for (var i in a){
  console.log(i);
}
```
## :sos: 数组常用方法
### **join** 方法,连接数组元素  
`array.join([separator = ‘,’])`
```
var a = [1,2,3];
a.join(); //返回　"1,2,3"
a.join("+");//返回　"1+2+3"

var b = new Array(10);
b.join("-");// "---------"
```
### **reverse** 方法,颠倒数组元素顺序
`array.reverse()`
```
var a = [3,10,7];
console.log(a.reverse());// [7,10,3] 直接改变原数组
```
### **sort** 方法,对数组进行排序
`array.sort([comparation])`  
sort方法返回排序之后数组, sort函数无需参数时就按照字母排序排列。
```
var a = [3,8,2];
console.log(a.sort());// [2,3,8]

var b = ["banner", "apple", "purple"];
console.log(b.sort()); // ["apple", "banner", "purple"]

b.sort(function(a,b){
    return a - b;
  });
```
### **concat** 方法,连接数组并返回一个新数组
`array.concat(value1,value2,value3,…)`
```
var num1 = [1, 2, 3];
var num2 = [4, 5, 6];
var num3 = [7, 8, 9];
// 组成新数组[1, 2, 3, 4, 5, 6, 7, 8, 9]; 原数组 num1, num2, num3 未被修改
var nums = num1.concat(num2, num3);



var alpha = ["a", "b", "c"];
var numeric = [1, 2, 3];
// 组成新数组 ["a", "b", "c", 1, 2, 3]; 原数组 alpha 和 numeric 未被修改
var alphaNumeric = alpha.concat(numeric);
```
### **slice** 方法,对数组内容进行浅复制
`array.slice(start,end), start,end 用于指定开始位置和结束位置。`
```
var a = [1,2,3,4,5];
var b = a.slice(0,2);//从0位置到1位置，2个元素
var c = a.slice(); //浅复制数组ａ
var d = a.slice(2); //从2位置开始，一直到最后
var e = a.slice(-2); //从倒数第二位置，一直到最后

var  a1 = {"color":"red", "name":"xiaoming"};
var  a2 = [c,2,3,4];
var  a3 = a2.slice(0,2);
a3[0].color = "green";//slice浅复制，此处修改会影响原先的元素a1
console.log(a1);
```
### **splice** 方法,对数组元素进行替换修改
`array.splice(start, deleteCount[, item1[, item2[, …]]])`    
start, 指定开始位置　　　　　　  
deleteCount, 指定删除的个数 　 　　　　　　  
item, 指定要添加的元素　　  
splice() 方法与 slice() 方法的作用是不同的，splice() 方法会直接对数组进行修改.返回被删除的元素数组　　　　　　
```
var myFish = ["angel", "clown", "mandarin", "surgeon"];

//从第 2 位开始删除 0 个元素，插入 "drum"
var removed = myFish.splice(2, 0, "drum");
//运算后的 myFish:["angel", "clown", "drum", "mandarin", "surgeon"]
//被删除元素数组：[]，没有元素被删除

//从第 3 位开始删除 1 个元素
removed = myFish.splice(3, 1);
//运算后的myFish：["angel", "clown", "drum", "surgeon"]
//被删除元素数组：["mandarin"]

//从第 2 位开始删除 1 个元素，然后插入 "trumpet"
removed = myFish.splice(2, 1, "trumpet");
//运算后的myFish: ["angel", "clown", "trumpet", "surgeon"]
//被删除元素数组：["drum"]
```
### **toString()** **toLocaleString()**
`array.toString()`  
`array.toLocaleString()`
返回一个字符串，表示指定的数组及其元素
```js
var a = [1,2,3,4,5];
console.log(a.toString());//“1,2,3,4,5”

var b = new Date();
var c = [a,b];
console.log(c.toLocaleString());//转换成本地的字符串
```
## :moneybag: ECMA5中数组新方法
:one: `array.forEach(callback[, thisArg])`  
callback 在数组每一项上执行的函数，接收三个参数：  
currentValue, 当前项（指遍历时正在被处理那个数组项）的值。  
index, 当前项的索引（或下标）。  
array, 数组本身。  
thisArg 可选参数。用来当作callback 函数内this的值的对象。  
注意： forEach在遍历完数组元素之前是不会终止的。
```js
var  a = [1,2,3,4,5,6];
var sum = 0;
a.forEach(function(e,i,a){
    sum += e;
});
console.log(sum);
```
:two: `array.map(callback[, thisArg])`    
callback 在数组每一项上执行的函数，接收三个参数：  
currentValue, 当前项（指遍历时正在被处理那个数组项）的值。  
index, 当前项的索引（或下标）。  
array, 数组本身。  
thisArg 可选参数。用来当作callback 函数内this的值的对象。  
返回值： 一个由原数组中的每个元素调用一个指定方法后的返回值组成的新数组  
```js
var a = [1,2,3,4,5];
var result1 = a.map(function(e){
    return e + 1;
});
console.log(result1);
```
:three: `arr.filter(callback[, thisArg])`  
callback 用来测试数组的每个元素的函数。调用时使用参数 (element, index, array)。  
返回true表示保留该元素（通过测试），false则不保留。  
thisArg 可选。执行 callback 时的用于 this 的值。
```
var a = [1,2,3,4,5,6];
var result = a.filter(function(e,i,a){
    if (e % 2 == 0) {
        return true;
    }
});
console.log(result);
```
:four: `array.every(callback[,thisArg])`  
callback 用来测试数组的每个元素的函数。调用时使用参数 (element, index, array)。  
只有所有元素都通过函数测试，才会返回true,否则返回false  
thisArg 可选。执行 callback 时的用于 this 的值。
```
var a = [1,2,3,4];
var ret = a.every(function(e,i,a){
     return i > 3;
  });
console.log(ret);//false
```
:five:  `array.some(callback[,thisArg])`  
callback 用来测试数组的每个元素的函数。调用时使用参数 (element, index, array)。  
只要有一个元素都通过函数测试，会返回true.  
thisArg 可选。执行 callback 时的用于 this 的值。
```js
var a = [1,2,3,4];
var ret = a.every(function(e,i,a){
     return i > 3;
  });
console.log(ret);//true
```
:six: `arr.reduce(callback,[initialValue])`  
callback  执行数组中每个值的函数，包含四个参数         
previousValue   上一次调用回调返回的值，或者是提供的初始值（initialValue）        
currentValue   数组中当前被处理的元素          
index   当前元素在数组中的索引         
array   调用 reduce 的数组             
initialValue  作为第一次调用 callback 的第一个参数。   
返回一个值。   
```js
var a = [1,2,3,4,5];
var sum = a.reduce(function (pre,cur,i,a) {
    return  pre + cur;
}, 0);
console.log(sum);

var mul = a.reduce(function(pre,cur,i,a){
    return pre * cur;
}, 1);
console.log(mul);
```
:seven: `arr.reduceRight(callback,[initialValue])` 从数组的右边开始遍历数组  
callback  执行数组中每个值的函数，包含四个参数         
       previousValue   上一次调用回调返回的值，或者是提供的初始值（initialValue）        
       currentValue   数组中当前被处理的元素          
       index   当前元素在数组中的索引         
       array   调用 reduce 的数组             
initialValue  作为第一次调用 callback 的第一个参数。   
返回一个值。  
```
var a = [2,3,4];
ver ret = a.reduceRight(function(pre,cur,i,a){
      return Math.pow(cur,pre);
  });
//结果：2^(3^4)
```
:eight: `arr.indexOf(searchElement[, fromIndex = 0])`  
searchElement   要查找的元素        
fromIndex     指定开始位置,默认为0      
返回给定元素能找在数组中找到的第一个索引值，否则返回-1。  

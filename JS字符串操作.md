# js 字符串
## 字符串常用方法
### :one: charAt(index) 获取相应位置的字符
```js
var s = "abced";
console.log(s.charAt(0)); //返回字符'a'
```
### :two: charCodeAt(index) 获取相应字符串的编码
```js
var s = "abced";
console.log(s.charCodeAt(0)); //返回字符编码97
```
### :three: indexOf(s[,fromIndex]), 返回指定值在字符串对象中首次出现的位置。从 fromIndex 位置开始查找，如果不存在，则返回 -1。
```js
var a = "abcdef  goh";
console.log(a.indexOf("goh"));
console.log(a.indexOf("Goh"));//区分大小写，返回-1
```
```js
"Blue Whale".indexOf("Blue") !== -1; // true
"Blue Whale".indexOf("Bloe") !== -1; // false
```
### :four:  str.concat(string2, string3[, …, stringN]), 将多个字符串连在一块，返回新的字符串。
```js
var news = s.concat("hello", "world", "google");
console.log(news);// helloworldgoogle
```
### :five:  str.slice(begin[,end])，对字符串进行切片操作，返回新的字符串。从begin开始，但是不包括end。　
```js
var str1 = 'The morning is upon us.';
var str2 = str1.slice(4, -2);
console.log(str2); // OUTPUT: morning is upon u
```
### :six:  str.substr(start[, length]), 返回从start开始的长度为length的字符串。
```js
var str = "abcdefghij";
console.log("(1,2): "    + str.substr(1,2));   // (1,2): bc
console.log("(-3,2): "   + str.substr(-3,2));  // (-3,2): hi
console.log("(-3): "     + str.substr(-3));    // (-3): hij
console.log("(1): "      + str.substr(1));     // (1): bcdefghij
console.log("(-20, 2): " + str.substr(-20,2)); // (-20, 2): ab
console.log("(20, 2): "  + str.substr(20,2));  // (20, 2)
```
### :seven: str.substring(indexStart[, indexEnd]), 功能类似于slice。如果 indexStart 大于 indexEnd，则 substring 的执行效果就像两个参数调换了一样。  
例如:str.substring(1, 0) == str.substring(0, 1)。
```js
var anyString = "Mozilla";

// 输出 "Moz"
console.log(anyString.substring(0,3));
console.log(anyString.substring(3,0));

// 输出 "lla"
console.log(anyString.substring(4,7));
console.log(anyString.substring(7,4));

// 输出 "Mozill"
console.log(anyString.substring(0,6));

// 输出 "Mozilla"
console.log(anyString.substring(0,7));
console.log(anyString.substring(0,10))
```
### :eight: toLowerCase(), toUpperCase() 大小写进行转换
```js
var test = "abc";
var test1 = "ABC";
test.toUpperCase(); //ABC
test.toLowerCase(); // abc
```
### :nine: str.split([separator] [,limit]),对字符串进行分割
```js
var s = "hello world google";
var a = s.split();
console.log(a);

a = s.split(" ");//按照空格分割
console.log(a);

a = s.split(" ", 2);//按照空格分割，限制个数２
console.log(a);
```

# 正则表达式
正则表达式,又称正规表示法,常规表示法  
正则表达式使用单个字符串来描述,匹配一系列符合某个句法规则,在很多编辑器里,正则表达式通常被用来  
检索,替换,那些符合某个模式的文本.  
许多程序设计语言都支持利用正则表达式进行字符串操作,基本规则一致,但是不同的编程语言略有差异

## js中正则表达式的定义方式
1. 直接定义
```js
var pattern = /\d{3,10}/;
var pattern1 = /test/g;
```
2. 使用RegExp类
```js
var pattern = new RegExp(/hello/,'g');
var pattern1 = new RegExp('hello','g');
```
### 常用检测方法
1. **test**方法,匹配成功返回true,失败返回false
```js
var s = "hello world google";
cosole.log(/hello/g.test(s));// true
cosole.log(/world/g.test(s));// true
cosole.log(/me/g.test(s));//false
console.log(/[a-z]/.test(s));//true
console.log(/[A-Z]/.test(s));//true
```
2.  **exec**方法,返回值是一个数组或者null
```
var re = /quick\s(brown).+?(jumps)/ig;
var result = re.exec('The Quick Brown Fox Jumps Ovar The Lazy Dog')
```
3. **replace**方法,字符串的替换方法,返回替换后的新字符串
```js
var s = "Hello world world hello";
var s1 = s.replace(/hello/g, "apple");
console.log(s1);

s1 = s.replace(/hello/, "apple");
console.log(s1);

s1 = s.replace(/hello/i, "apple");
console.log(s1);
```
### 常见的匹配模式
1. 预定义
```js
 . [^\n\r]  除了换行和回车之外的任意字符
 \d [0-9]       数字字符
 \D [^0-9]     非数字字符
 \s [ \t\n\x0B\f\r]  空白字符
 \S [^ \t\n\x0B\f\r]     非空白字符
 \w [a-zA-Z_0-9]         单词字符
 \W [^a-zA-Z_0-9]       非单词字符  
```
2. 取非
```js
[^abc]  匹配abc三个字符以外的字符
[^123]  匹配123三个字符以外的字符
```
3. 连续
```js
[a-zA-Z]  匹配小写和大写字符
[0-9]     匹配所有数字字符
```
4. 边界
```js
^ 会匹配行或者字符串的起始位置(写在[]外边)
$ 会匹配行或字符串的结尾位置

console.log(/^hello$/.test("hello world"));//false
console.log(/^hello$/.test("hello"));//true
```
5. 元字符
```js
*     重复零次或更多   (>=0)
+     重复一次或更多次  (>=1)
?     重复零次或一次   （0||1）  要么有 要么没有
{}    重复多少次的意思   可以有多少个  
{n}   n次
{n,}  重复n次或更多  (x>=n)
{n,m} 重复出现的次数(n<=x<=m)
a|b    一个 a或者b  

当　* 和　+ 后边添加？时可以进行最短匹配
```

```


```

# javaScript 的数据和类型
## 1.0 JavaScript 的各个版本和新名字由来  
ES3： 最早的JavaScript 版本 <br>
ES5： 相对于ES3  有改变 但不多 <br> 
ES6 ：有很多重要的改变   同时还有另外一种名字ECMA2015<br>
ES7, ES8:  有改变 不多 <br>

JavaScript 的另外一种名字的由来<br> 
当年 NetScape  向 ECMA 申报 JavaScript标准  但是 javascript 已经被Netscape公司注册了商标  所以ECMA为JavaScript 取了一个新名字：ECMA Script；<br>



## 2.0 javascript 的数据类型
string number symbol  undefined null object  boolean <br>

那么function 和 array 是什么？ 是object。<br>



### 2.1数字的分类： 
十进制以及表达方式：  1;   1 + ‘0.1’;  1.23e2;<br>
二进制以及表达方式：以0b开头的数  0b11 就是十进制的3  大小写无所谓 <br>
八进制以及表达方式：以0开头 011 就是十进制的9  注意：存以0开头的电话号码 电话号码要以字符串的形式存下来 如果不是以字符串的形式存下来，游览器会自动任务<br>这是一个以0 开头的八进制数字。 
十六进制以及表达方式：以0X 开头  0x11 就是十进制的17<br>

### 2.2字符串
字符串的转义：
例如： var  singlequotes = ‘ ‘ ‘ ; <br>
           这样写游览器不会认为 你要表示的是 单引号 <br>
           游览器 会这样 断句： var  a   = ‘’    ‘ <br>
           报错信息：Uncaught SyntaxError : Invalid or unexpected token；<br>
           那怎么表示 单引号？<br>
           方法一： var singlequotes = “ ‘  ” ；<br>
           如果继续用方法一 怎么表示 一个单引号和一个双引号？<br>
           显然方法一这个方法不能实现。<br>
           这个时候就需要引入 转义符号 来实现了。<br>
           var  a = ‘ \’ ‘; <br>
           这个斜杠告诉游览器 中间的单引号不是结束的引号 想要表达的就是一个单引号 ；<br>
           这个斜杠了就是转义符；<br>
           更多列子：<br>  
           代表回车  var n = ‘  \n ‘ <br>
           用转义符号来 转义 转义符 Var b = "\\"<br>
           多行字符串：不是字符串里有回车<br>
           多行字符串表达方式一：  var  s = ‘123456        \
                                 7890’;<br>
           表达方式二：  var s2 = ‘12345’ + ‘67890’<br>
           相比较方法一 方法二更好 不容易造成误解 <br>
           表达方式方法三： 用ES6  <br>    
             
```
               var s4 =  `12345
               67890`;
               a.length; //--->11 说明 5和6 之间有回车 
```



### 2.3布尔值 
true    or  false <br>
与或非 运算 <br>
与运算（&&）： 两真才真<br>
或运算（||）：一真也行也算真<br>


### 2.4 null and undefined 
类型为null  值为：null <br>
类型为undefined  值为： undefined <br>
都表示 什么都没有 但是 还是有差异：<br>
第一：如果一个变量 没有被赋值   这个变量的值等于 undefined <br>
第二：如果是一个对象  没有被赋值  这个对象的值等于 null;<br>
⚠️： 没有被赋值也分两种情况 ：第一种变量和对象根本没有值；<br>
                          第二种根据程序上下文来看，变量或者对象暂时还不需要被赋值;<br>        
一言以蔽之：null 表示空对象 undefined 表示空非对象<br>



### 2.5 对象 
什么是一个对象?<br> 
怎么正确取得对象的属性?<br>
空字符串可以当对象的属性吗？<br> 
怎么删除一个属性?<br>
怎么循环一个object 里面的所有属性？<br>
怎么知道一个变量的类型？<br>

```
var    name ='apple’；
var    numberOfApples = 5；
var    perApple= ‘¥4’； 

var  todayPayApples  = {
        name:'apple’，
        numberOfApples： 5，
        perApple： ‘¥4’，
        '': 'apples'
}
// todayPayApples 是一个对象 就是简单类的组合
// 每一个属性结束完，都用逗号隔开
// 但是  需要兼容IE 7（包含7）以下的 不能用逗号
// 不过  需要兼容 IE 8 以上的游览器 可以用逗号 
⚠️： 有单引号和没有单引号的差异  
todayPayApples[‘name’] // apple;
todayPayApples[name] //undefined 
todayPayApples['']//apples 
//有单引号就是字符串 没有单引号是一个变量 因为在对象的属性名字默认是一个字符串  
//属性的命名也同样遵守标志符规则 不想遵守的话 命名的时候 最好添加上引号
//前提条件：name 是一个字符串 person['name']等同于person.name.  dot notation 只能接受字符串 braket notation 不仅仅可以接受字符串 多数情况下 用 braket notation 。    
delete todayPayApples ['name'];
todayPayApples.name; // undefined;
'name ' in todayPayApples // false  （no key）
⚠️： 最后的结果 todayPayApples1.name = undefined; 都是undefined 但是差别却很大 
var  todayPayApples1 = {name: 'today'};
todayPayApples1.name = undefined;
‘name’ in  todayPayApples1 // true （no value）
```



```
// 关于循环遍历对象里的属性 
var person = {name:'shannon',age:'18'};
for(var key in person)
{
console.log(key);
} // shannon age 

for(var key in person)
{
console.log(person[key]);
} // shannon age 


for(var key in person)
{
console.log(person.key);
} // undefined  dot notation 的key 是字符串 但是var key 的key 是一个变量  所以是undefined
```


```
var t=1;
typeof t; // “number”
var t=undefined；
typeof t；// "undefined"
var t=null;
typepf t;//'object' 非常特别 重点记忆
function f(){
}
typeof f; //'function' 

```


##  3.0类型转换
###    3.1 number 变 string  用内置的API 
```
 var n=1;
 n.toSting();//"1"
// 除了用内置API 变string 还可以用braket notation 这一特性 
var testObj = {};
testObj['testName'] = test;
testObj[1] = test;
testObj;//{1: 2, testName: 1}
// 1 + ""  与空字符串相加 
"1"
```   

###  3.2 boolean 变 string  用内置的API 
```
var b = true；
b.toString();//"true" 
// 与空字符串相加 
true + ""
"true"
```
    
### 3.3 null 变 string 用内置API 会报错 
```
var b = null；
b.toString();// Uncaught TypeError: Cannot read property"toString" of null 
// ''+null 与空字符串相加
"null"
```

### 3.4  undefined 变 string  用内置API 会报错 

```
var b = undefined；
b.toString()//Uncaught TypeError: Cannot read property"toString" of undefined  
// " " +undefined  与空字符串相加 
" undefined"
```

### 3.5 object 变 string  用内置API 但结果并非所预期的那样

```
var b = {test:'toString'};
b.toString();// [object Object]
// 
obj+""
// [object Object]
```

⚠️： 以上的类型都可以 （除去obj）用加号 转换成为 字符串 <br> 
          为什么呀？<br>
          加号只要发现任一一边有字符串 也会把另外一边变成字符串 <br>
```
1 + ‘1’
“11”； // 这两行代码不好 违背了常识 不同类型的怎么能够相加了？
// 改写一下 
(1).toSting() + '1';
"11";
```
还有其他简单的方法把 对象 数字 布尔值 null undefined  变为字符串吗？ 有  <br>

```
var n = 1;
window.String(1)
"1";
window.String(true)
"true";
window.String(null)
"null";
window.String(undefined)
"undefined";   
var obj = {test:'toString'};
window.String(obj);
"[object Object]" 
```
 
### 3.6 数字 字符串 null undefined 对象 变为布尔值 

```
// 方法一：
Boolean(1);
ture;
Boolean(0);
false;
Boolean("");//空字符串
false;
Boolean(' ');//空格
true;
Boolean(null);
false;
Boolean(undefined);
false;
Boolean({});
true;
Boolean{test:'toString'};
true;
// 方法二：
!true;
false;
!!true;
true;
!!1;
true;
!! 0;
false;
!!'   ';
true;
!!{};
true;
!!{test:'toString'}
true;
!!null;
false;
!![];
true;
!!function(){}
true;
```

记少不记多<br> 
真值太多了<br>
 falsy 值不多 5个  <br> 
```
// 
0 NAN “” null undefined 
```


### 3.7字符串变数字 
```
Number('1');
1;
parseInt('1000',2); // 变二进制 parse 是逐个解析 
8; 
parseFloat('1.23);
1.23 
'1'-0;
1;
+ ‘1’；
1;
```

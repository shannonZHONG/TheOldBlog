# javaScript 的数据和类型
## 1.0 JavaScript 的各个版本和新名字由来  
ES3： 最早的JavaScript 版本 
ES5： 相对于ES3  有改变 但不多  
ES6 ：有很多重要的改变   同时还有另外一种名字ECMA2015
ES7, ES8:  有改变 不多 

JavaScript 的另外一种名字的由来 
当年 NetScape  向 ECMA 申报 JavaScript标准  但是 javascript 已经被Netscape公司注册了商标  所以ECMA为JavaScript 取了一个新名字：ECMA Script；



## 2.0 javascript 的数据类型
string number symbol  undefined null object  boolean 

那么function 和 array 是什么？ 是object。



### 2.1数字的分类： 
十进制以及表达方式：  1;   1 + ‘0.1’;  1.23e2;
二进制以及表达方式：以0b开头的数  0b11 就是十进制的3  大小写无所谓 
八进制以及表达方式：以0开头 011 就是十进制的9  注意：存以0开头的电话号码 电话号码要以字符串的形式存下来 如果不是以字符串的形式存下来，游览器会自动任务这是一个以0 开头的八进制数字。 
十六进制以及表达方式：以0X 开头  0x11 就是十进制的17 

### 2.2字符串
字符串的转义：
例如： var  singlequotes = ‘ ‘ ‘ ; 
             这样写游览器不会认为 你要表示的是 单引号 
              游览器 会这样 断句： var  a   = ‘’    ‘ 
              报错信息：Uncaught SyntaxError : Invalid or unexpected token；
              那怎么表示 单引号？ 
              方法一： var singlequotes = “ ‘  ” ；
              那怎么表示 一个单引号和一个双引号？
              显然方法一这个方法不能实现。
              那就只有引入 转义符号 来实现了。
               var  a = ‘ \’ ‘; 
               这个斜杠告诉游览器 不是  结束的引号 ；
               这个斜杠就是转义符；
               更多列子：  
               var n = ‘  \n ‘  代表回车 
               Var b = ‘ \\   ’ ;   用转义符号来 转义 转义符 
 多行字符串：不是字符串里有回车
              方法一：  var  s = ‘123456          \
                                 7890’;
             方法二：  var s2 = ‘12345’ + ‘67890’
             相比较方法一 方法二更好 不容易造成误解 
             方法三： 用ES6  
```
               var s4 =  `12345
               67890`;
               a.length; //--->11 说明 5和6 之间有回车 
```



### 2.3布尔值 
true    or  false 
与或非 运算 
与运算（&&）： 两真才真
或运算（||）：一真也行也算真 


### 2.4 null and undefined 
类型为null  值为：null 
类型为undefined  值为： undefined 
都表示 什么都没有 但是 还是有差异：
第一：如果一个变量 没有被赋值   这个变量的值等于 undefined 
第二：如果是一个对象  没有被赋值  这个对象的值等于 null;
⚠️： 没有被赋值也分两种情况 ：第一种变量和对象根本没有值；
                                                           第二种根据程序上下文来看，变量或者对象暂时还不需要被赋值；         
一言以蔽之：null 表示空对象 undefined 表示空非对象



### 2.5 对象 
什么是一个对象？ 
怎么正确取得对象的属性？ 
空字符串可以当对象的属性吗？ 
怎么删除一个属性？
怎么循环一个object 里面的所有属性？ 
怎么知道一个变量的类型？ 

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

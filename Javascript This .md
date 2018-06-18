
# This   

## 1.0为什么需要this？

同一段代码有this 和没有this 的差别 

```
// 有this 
 var person = {
    firstName: "Penelope",
    lastName: "Barrymore",
    fullName: function () {
        // 有this：
        console.log(this.firstName + " " + this.lastName)；
    }
}    
// 调用这个fullName：
person.fullName();
====================我是没有this的分割==========================================================================================

 var person = {
    firstName: "Penelope",
    lastName: "Barrymore",
    fullName: function (person) {
        // 无this：
        console.log(person.firstName + " " + person.lastName)
    }
}    

// 调用这个fullName：
person.fullName(person)

```
用this的原因：<br>
如果在这一段代码之前还有 重名的 person ，那么你此时在调用这个person，就会出错误。不仅仅出错，还有很难找出bug.<br>

## 2.0This 的值是由什么决定的
巴蜀地区有很多好吃的，你这次去这些地方要少吃一点。<br> 
南粤地区有很多好吃的，你这次去这些地方要少吃一点。<br>
这次去这些地方 在第一句话中 指代的时巴蜀地区 。<br>
这次去这些地方 在第二句话中 指代的是南粤地区。<br>

这次去这些地方 还可以用在另外一句话里面， 那么随着内容的改变 这次去这些地方 指代的内容也会变化。<br>

圣诞老人的故乡在冬天没有很多好吃的，你这次去这些地方要多吃点。<br>

以上的三个语句，都适用这次去这些地方<br> 
但是句子的含义和这次去这些地方 每次都是完全不一样。<br>
所以它们的具体含义都会随着内容的变化 而变化。<br>

这次去这些地方 和 this  有关系吗？ <br>
有   <br>
这次去这些地方 和 this 的作用都是指代。<br>
this  在javascript里面也会随着场景（context） 的变化而变化 <br>


例子1： 
this 的值是window<br>
或者说 this 指向 window <br>
注意：下列代码不是在严格模式下被执行<br>

```
 var  test = function(){
  console.log(this);
  console.log(this=== window);
}
test();
/*
Window {postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, frames: Window, …}
true
*/
```

例子2 ：
this 的值是myObjbr>
或者说 this 指向  myObj<br>
```

var val =9;
var myObj = {
    val : 10,
    test: function(){
    console.log(this.val);
    console.log(window.val);
    console.log(this === myObj);
    console.log(this);
}
}

myObj.test();

/*
10
9
true
{val: 10, test: ƒ}
*/


```


## 3.0怎么改变this 的指向？
如果需要改变this 的context<br>
可以调用：<br>
function call () <br>
function apply() <br>
function bind() <br>


参考链接：<br>
方应杭，[一次说清楚 this](https://zhuanlan.zhihu.com/p/23804247?refer=study-fe)<br>
阮一峰，[this 关键字 — JavaScript 标准参考教程（alpha）](http://javascript.ruanyifeng.com/oop/this.html)<br>
Dr.Axel Rauschmayer[JavaScript’s this: how it works, where it can trip you up](http://2ality.com/2014/05/this.html)<br>

Dom  

## 1.0 什么是Dom？ 
英文全称：document object model<br>
每一个单词的意思：<br>
从DOM 是一颗树来看：<br>
document： 是由节点们组成的文档并或者说节点最后组成一棵树。<br>
object： 每一个标签都有自己的名字，种类，等属性。 有N 多属性 的这样的一个标签存放在object里面 。<br>
model： document里面每一个标签对应 一个自己的object  这种映射的关系叫做 model <br>
那么怎么实现 CURD 对这些节点？ <br>
通过javascript来操作每一个节点对应的object <br>

## 2 .0  组成DOM的最小节点：（node）
节点是组成 DOM的最小单位。<br>
节点的类型：<br>
* Document：整个文档树的顶层节点 <br>
* DocumentType ： Doctype 标签 <br>
* Element ： 网页的各种HTML标签 <br>
* Attribute ：网页元素的属性 <br>
* Text ：标签之间或标签包含的文本  <br>
* Comment ：注释<br>
* DocumentFragment ：文档的片段 <br>

### 2.0.1  7种类型的属性和方法来自哪里？
原生的节点对象： Node  <br>
就像是 游览器提供Array API等。只要是 array 可以继承Array API 的属性和方法一样。<br>

### 2.0.2  如果DOM 是一棵树， 那么怎么定位节点在哪里？
the “king ” of Dom：  html   < br>
换一种说法： <br>
root node  ： html  <br>
除根节点，每一个节点与另外节点都有三种关系：<br>
举例： <br>
每一个节点名字：apple <br>
* 父节点（parentNode）： apple 直接对应的上级节点 <br>
* 字节点（childNodes）：apple 直接下级节点 <br>
* 同级节点关系（siblings）：和apple 拥有同一个父节点的节点 <br>

#### 2.0.3  如果定位完成，怎么获取与节点有关的节点？
直接调用 游览器提供的API <br>
但是要注意： 即使调用API的最后结果一样，但由于调用的API所属的接口不一样， 故使用API是 一定要分清  这个API 是属于哪个接口。<br>
添加代码  来说明 

### 2.0.4 关于node 接口 常用属性  
#### 2.0.4.1 childNodes 
 不仅仅是包含了 子节点 而且还包含了 文本节点 <br>
```
<html>
<body>
  <div>开始</div>

  <ul>
    <li>所需要的信息</li>
  </ul>

  <div>结束</div>

  <script>
    for (let i = 0; i < document.body.childNodes.length; i++) {
      alert( "to be sure how many nodes the script have" + " "document.body.childNodes[i] ); // 
    }
  </script>
  ...more stuff...
</body>
</html>

```

![](%E4%B8%80%E9%A2%97%E7%94%9F%E9%95%BF%E5%9C%A8%20%E6%B8%B8%E8%A7%88%E5%99%A8%E7%9A%84%E2%80%9C%F0%9F%8C%B2%E2%80%9D%20Dom/127_0_0_1_51066_EventExample_Start_learnjs_html_%E5%92%8C_Walking_the_DOM.jpg)

⚠️：
第一：返回的不是一个数组 而是一个array-like object ; < br>
第二： 只能读这个伪数组，不能更改；<br>
第三： 如果对这个DOM 做了改变，那么 childNodes 也会改变 也就是childNodes 是“活的”；<br>
第四： 要循环这个伪数组 推荐用 for…of   for… in 只能循环搜集 enumerable properties；< br>

#### 2.0.4.2 nodeTage 
这个属性让你知道 这个节点是属于哪个节点类型。<br>

XXX .nodeType == 1 1代表： 元素节点<br>
XXX. nodeType == 3  3代表： 文本节点<br>
XXX. nodeType == 9   9代表：文本对象 <br>


```
<body>
  <script>
  var  ele = document.body; 
  alert(elem.nodeType); // 1 => element
  alert(elem.firstChild.nodeType); // 3 => text
  alert( document.nodeType ); // 9
  </script>
</body> 

```

##### 2.0.4.2 nodeName 与 tag-name 的差别 
tagName 服务对象只能是 元素节点的名字 <br>
nodeName 服务对象不仅仅是 元素节点还有其他的节点<br>

### 2.0.5 inner context  and text context  

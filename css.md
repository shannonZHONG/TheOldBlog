# css float 布局以及其他小技巧总结

这篇博文 前面四个部分是关于css 经典布局  如果你已经知道了 可以直接跳过看第五部分 css 的其他小技巧  

## 1.0 左右居中布局   
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .parent {
            border: 1px solid green;
            margin-left: auto;
            margin-right: auto;
            width:100%;
        }



        .child:nth-child(1) {
            width: 30%;
            background-color: pink;
            
        }

        .child:nth-child(2) {
            width: 70%;
            background-color: crimson;
        }

        .clearfix:after {
            content: "";
            display: block;
            clear: both;
        }

    </style>
</head>

<body>
    <div class="parent clearfix">
        <div class="child" style="float:left">
            a1
        </div>
        <div class="child" style="float:left">a2</div>
    </div>
</body>

</html>
```

## 2.0 左中右布局
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
       
        body,
        html {
            height: 100%;
            padding: 0;
            margin: 0
        }

       
        .left {
            background: lightblue;
            width: 100px;
            float: left;
            height: 10%;
        }

        
        .main {
            background: pink;
            height: 10%;
            margin: 0px 100px 0px 100px;
        }

       
        .right {
            background: lightgreen;
            width: 100px;
            float: right;
            height: 10%;
        }

    </style>
</head>

<body>
    <div class="left">Left</div>
    <div class="right">Right</div>
    <div class="main">Main</div>
</body>

</html>```


```

## 3.0 水平居中
```
 <!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        div {
            border: 1px solid red;
            line-height: 24px;
            padding: 8px 0;
           
        }

    </style>
</head>

<body>
    <div>
    水平居中

    </div>

</body>

</html>
```

## 4.0 垂直居中 （两种方法） 
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>垂直居中第一种方法table自带</title>
    <style>
        .parent {
            border: 1px solid red;
            height: 600px;
        }

        .child {
            border: 1px solid green;
        }

    </style>
</head>

<body>
    <table class="parent">
        <tr>
            <td class="child">
                垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中
            </td>
        </tr>
    </table>
</body>

</html>```

```


```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>垂直居中第二种方法marginautoabsolute</title>
    <style>
        .parent {
            height: 600px;
            border: 1px solid red;
            position: relative;
        }

        .child {
            border: 1px solid green;
            width: 300px;
            position: absolute;
            top: 50%;
            left: 50%;
            margin-left: -150px;
            height: 100px;
            margin-top: -50px;
        }

    </style>
</head>

<body>
    <div class="parent">
    <div class="child">
                垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直居中 垂直
        </div>
    </div>
</body>

</html>

```



## 5.0 水平垂直居中 
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        div {
            border: 1px solid red;
            line-height: 24px;
            padding: 8px 0;
            text-align: center;
        }

    </style>
</head>

<body>
    <div>
        水平垂直居中

    </div>

</body>

</html>
```



## 6.0 其他小技巧   
 6.1 css 有类似javascript 的console.log 的工具吗？
       当然有   用border  
```
div{
border: 1px solid red;
}
```

6.2  为什么明明在数字1和2之间敲两个空格 但是网页显示出来它们之间 只有一个空格 ？ 那是因为你没有添加 &nbsp (no break space)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>你写的bug</title>
</head>
<body>
    <div>
    1&nbsp;&nbsp;2
   </div>
</body>
</html>
```

6.3 为什么只有一个阿拉伯数字且已经设定了 字体大小是20 px 但一旦打开开发者工具：显示的字体大小是 28px ？
因为每一种字体被设计时，为了【好看】，设计师会给每一种字体一个好看系数  默认的字体时pingfang  那么28px /20px =1.4  这个1.4 就是【好看（字体）系数 】每一种字体都有自己的 【好看系数】
如果不想使用字体设计师给你的【好看系数】一定要用自己的  可以添加一行 


```
line-height： 20px；
```

代码如下 
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>test</title>
    <style>
        div{
            border: 1px solid red;
            font-size: 20px;
        }
    </style>
</head>
<body>
    <div>
        1
    </div>
</body>
</html>
```

6.4 为什么分别两个span元素之间 看似什么都没有 但游览器 1 和 2 之间确有空隙 ？
        原因：span元素 之间有tab 有回车等都会造成有空格的情况
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        span{
            border: 1px solid red;
        }
    </style>
</head>
<body>
    <div>
       <span>1</span>
       <span>2</span>
    </div>
</body>
</html>
```


6.5  块级元素的高度怎么确定？
        如果div 里 只有一个内联元素  那么div 的高度是由这个内联元素的行高所决定。
        如果div 里有多行，那么就把每一行的行高加起来算。
     


6.6  姓名怎么和联系方式对齐 ？
      其他的方法：直接用&nbsp ？可以的，不过会受到字体的影响。字体一变， 加的&nbsp 就会变。 
      代码解释：代码如果是内联元素要被改变宽度的话， 一定要先写上display：inline-block 。
      text-align: justify; 当有多行字体时，这句话会让强迫症看了之后 非（两）常（边）舒（对）心 （齐）。
      那只有一行的时候 怎么对齐？看上去是多添加了一行。代码
      如下：
      
```
  span:after{
        content:"";
        display: inline-block;
        width: 100%;
        border: 1px solid pink;
    }
```
       
      6.6.4 全部代码如下：
```
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>JS Bin</title>
</head>
<style>
    div {
        border: 1px solid red;
        font-size: 20px;
    }

    span {
        border: 1px solid green;
        display: inline-block;
        width: 4em;
        text-align: justify;
        line-height: 20px;
        height: 20px;
        overflow: hidden;
    }
   span:after{
        content:"";
        display: inline-block;
        width: 100%;
        border: 1px solid pink;
    }

</style>

<body>
    <div>
        <span>姓名</span><br>
        <span>联系方式</span>

    </div>
</body>

</html>
```
         

6.7  六个内联元素  怎么写才能没有空隙 ？
        添加 float：left 
                 clearFix  

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        ul{
            margin:0; padding: 0; list-style: none;
        }
        
        ul > li{
            border: 1px solid red;
            float: left;
        }
        .clearfix :after{
            content: "";
            display:  block;
            clear: both;
        }
    </style>
</head>
<body>
 <ul class= "clearfix">
     <li>选项1</li>
     <li>选项2</li>
     <li>选项3</li>
     <li>选项4</li>
     <li>选项5</li>
     <li>选项6</li>
 </ul>
</body>
</html>
```


6.8 怎么做 一行和多行文本过长变省略号？
```
//一行 
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        div {
            border: 1px solid red;
         
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

    </style>
</head>

<body>
    <div>
        s d f d f d f s d f s d f d f s d f d f sd f s df d f s df d d f d f d f s d f d f d f d f d f d f d f df d f d f d f df d d s d s d s d s d s d s d s d s d s d s d s d s s d s d s d s d s d s d s d s sd s d s d s sd d v f ef e f e f e f ef ef e f ef e f ef e fe f e f e f e fe f ef e fe f
     </div>
</body>

</html>
```


```
// css multi line text ellipsis

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        div {
            border: 1px solid red;
            display: -webkit-box;
            -webkit-line-clamp:2;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

    </style>
</head>

<body>
    <div>
        s d f d f d f s d f s d f d f s d f d f sd f s df d f s df d d f d f d f s d f d f d f d f d f d f d f df d f d f d f df d d s d s d s d s d s d s d s d s d s d s d s d s s d s d s d s d s d s d s d s sd s d s d s sd d v f ef e f e f e f ef ef e f ef e f ef e fe f e f e f e fe f ef e fe f
     </div>
</body>

</html>
```


6.9 什么情况下margin 会合并以及怎么修改使其正常化？
       如果父元素没有什么东西挡住子元素   那么子元素的边距就会父合并起来 
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
          .son {
            border: 15px solid red;
            padding: 10px;
            margin: 10px;
            }

        .dad {
          outline: 1px solid green;
           margin: 15px;
          }

    </style>
</head>

<body>
    <div class="dad">
        <div class="son">
            111
        </div>
    </div>
</body>
```

怎么修改 ：

第一种添加： 在父元素里添加border -top 和 border - bottom ；
第二种添加：  同样是在 父元素里添加 padding-top  

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        body {
            border: 1px solid black;
        }

        .son {
            border: 15px solid yellow;
            padding: 10px;
            margin: 10px;
           }

        .dad {
            outline: 1px solid green;
            margin: 15px;
            border-top: 11px solid pink;
            border-bottom: 11px solid pink;
          }

    </style>
</head>

<body>
    <div class="dad">
        <div class="son">
            111
        </div>
    </div>
</body>

</html>
```


6.10 怎么break out words？
添加一行代码： word-break: break-all;

```

<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>JS Bin</title>
</head>
<style>
    div {
        border: 1px solid red;
        word-break: break-all;
    }

</style>

<body>
    <div>
        1 apppppppppppppppppppppppppppppppppppppppppppppppppppppppppppppppppppppppple


    </div>
</body>

</html>
```

6.11 怎么脱离文档流 ？
三种方法： 
```
position：absolute；
float： left；
position：fixed；
```

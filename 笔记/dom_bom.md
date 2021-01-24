# 1. bom是什么?

 browser object model(浏览器对象模型)

在浏览器中 `window`指的就是bom对象

~~~js
//网页重定向
// window.location.href="http://www.sina.com"

//浏览器可视区的宽度
console.log(window.innerWidth);
//当前浏览器窗口的宽度
console.log(window.outerWidth);
//浏览器可视区的高度
console.log(window.innerHeight);
//当前浏览器窗口的高度
console.log(window.outerHeight);
~~~

---

# 2. Dom是什么?

document object model(文档对象模型)

~~~shell
window.document: 通过这种方式来获取文档对象
~~~

但是我们的编程是面向浏览器编程,而浏览器对于我们编程来说就是`window`对象;

所以说在实际开发过程中window是可以省略的;

~~~shell
document
~~~

---

# 3. 给浏览器的内容显式区域输出内容

~~~js
document.write("hello world");
~~~

---

# 4. 浏览器的编码问题

~~~html
//浏览器默认使用的编码是根据计算机所在的地区决定了(安装系统时所选择的国家/地区决定)
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- 设置网页的编码-->
    <meta charset="UTF-8">
    <title>输出内容到页面</title>
</head>
<body>

<script>
    document.write("hello world中国你好");
</script>
</body>
</html>

~~~

---

# 5. js获取网页中的元素

## 5.1 根据==ID==获取网页中的元素

~~~js
//根据ID获取网页元素
let p1Element = document.getElementById("p1");
~~~

## 5.2 根据==class名==称获取网页中的元素

~~~js
//根据class名称获取元素,返回的是一个集合
let c1Elements = document.getElementsByClassName("c1")
~~~

## 5.3 根据==标签名==称获取网中的元素

```js
let ps = document.getElementsByTagName("p")
```

---

# 6. 使用选择器获取网页中的元素

~~~js
//querySelector: 只能选择一个元素,如果后面的选择器匹配到了多个元素,则返回第一个
document.querySelector(".c1");
~~~

~~~js
//querySelectorAll: 可以选择多个元素,返回nodeList对象
let elements = document.querySelectorAll(".c1");
~~~

---

# 7. 改变元素的内容

~~~js
s1.innerHTML="<i>你好</i>世界" //会解析其中的标签
s1.innerText = "<i>你好</i>世界"  //会原样输出
~~~

---

# 8. 改变元素的样式(了解)

样式属性和css一样

~~~js
const s1 = document.getElementById("s1")
//如果属性是一个单词组成的,则直接写属性
// s1.style.color="#f00"   

//如果属性是由两个单词组成的,那么把单词去掉 - ,变成小驼峰命名法;
s1.style.backgroundColor = "red"
~~~

---

# 9. js添加属性

~~~js
s1.setAttribute("myname", "admin")
~~~

~~~js
s1.setAttribute("class", "cc")
~~~

---

# 10. 移除属性

~~~js
s1.removeAttribute("class")
~~~

---

# 11. js中的事件

事件的4要素:

- 事件源(谁在**哪个元素上**触发事件)
- 事件的类型  
- 事件的触发时机
- 事件的内容(触发了事件之后要做什么)

## 11.1 绑定事件的方式

```js
<!--通过标签的onclick属性绑定事件-->
<button onclick="doClick()">点我呀</button>

<script>

    //事件触发之后调用的事件函数
    function doClick() {
        console.log("hello")
    }
</script>
```

~~~js
//获取元素
const btn1 = document.getElementById("btn1")

//给元素绑定事件
btn1.onclick =  function () {
    console.log("hello")
}
~~~

---

# 12. 页面加载事件

```js
//页面加载事件(页面加载之后触发onload事件)
onload =  function () {
    const s1 = document.getElementById("s1")
    s1.style.color = "#f00"
}
```

---

# 13. 点击事件与双击事件

~~~html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>点击事件与双击事件</title>
    </head>
    <body>
        <!--绑定点击事件-->
        <button onclick="doClick()">点我呀</button>
        <!--绑定双击事件-->
        <button ondblclick="doClick2()">用力点我呀</button>
        <script type="text/javascript">
            function doClick() {
                console.log("点击事件被触发了")
            }

            function doClick2() {
                console.log("双击事件被触发了")
            }
        </script>
    </body>
</html>
~~~

---

# 14. 鼠标事件

~~~js
let box1 = document.getElementById("box1");

//鼠标划入
box1.onmouseover = function () {
    console.log("onmouseover")
}

//鼠标移动
box1.onmousemove = function () {
    console.log("onmousemove")
}

//鼠标移出
box1.onmouseout = function () {
    console.log("onmouseout")
}

//鼠标按下
box1.onmousedown = function () {
    console.log("onmousedown")
}

//鼠标松开
box1.onmouseup = function () {
    console.log("onmouseup")
}
~~~

---

# 15. 键盘事件

```js
<input type="text"  onkeydown="keyDown()" onkeyup="keyUp()"   placeholder="请输入杨幂最喜欢的人">
    <script>
    function keyDown() {
    console.log("按键按下")
}

function keyUp() {
    console.log("按键松开")
}
</script>
```

---

# 16. 操作改变的事件

~~~js
<select onchange="change(this)">
    <option value="admin1">admin1</option>
    <option value="admin2">admin2</option>
    <option value="admin3">admin3</option>
    <option value="admin4">admin4</option>
</select>

<script>
    function change(obj) {
        console.log(obj.selectedIndex)
    }
</script>
~~~

---

# 17. 鼠标的焦点事件

~~~js
<input id="ipt" type="text" placeholder="请输入名称">

    <script>
    let ipt = document.getElementById("ipt")

ipt.onfocus = function () {
    console.log("获取焦点")
}


ipt.onblur = function () {
    console.log("失去焦点")
}
</script>
~~~

# 18. 表单事件

~~~js
<form action="#"  onsubmit="login()">
    <input type="text" placeholder="请输入用户名">
    <input type="text" placeholder="请输入密码">
    <input type="submit" value="登录">
</form>


<script>
    function login() {
            console.log("表单提交了...")
    }
</script>
~~~

---

# 19. js操作元素

## 19.1 创建节点与添加子节点与添加属性

~~~js
let box = document.getElementById("box")

//创建一个节点  h1
let h1 = document.createElement("h1")

//添加属性
h1.setAttribute("name","admin")

//创建文本节点
let textNode = document.createTextNode("好好学习");

//给h1追加文本节点
h1.appendChild(textNode)

//给box追加h1节点
box.appendChild(h1)
~~~

---

## 19.2 节点与属性的移除

~~~js
//调用节点的remove方法直接移除元素
h1.remove()
~~~

~~~js
//移除属性
h1.removeAttribute("name")
~~~

---

## 19.3 节点内容的修改

~~~js
innerText: 给里面追加文本(不会解析标签)
innerHTML:给里面追加文本(会解析标签)
~~~

## 19.4 获取节点的值

~~~js
let d1 = document.getElementById("d1")
let btn = document.querySelector("#btn");
btn.onclick = function () {
    //标签对象.value  获取值
    console.log(d1.value)
}
~~~

---

# 20. 作业

省市联动

![image-20210123153338359](upload/image-20210123153338359.png)
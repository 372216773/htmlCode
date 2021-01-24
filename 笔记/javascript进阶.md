# 1. js中的数组

数组: 可以存储多个数据的一个集合;

## 1.1 数组的创建

~~~js
var ages = new Array(10, 20, 30, 40);  /*定义数组时直接初始化*/
console.log(ages);

var ages1  =  new Array(3);  /*传递一个参数代表的是数组的长度*/
console.log(ages1);

var ages2 =  [];  /*数组的定义,定义一个空数组,建议使用这种方式*/
console.log(ages2);
~~~



## 1.2 修改数组中的元素

~~~js
var ages = [];
ages[2] = 20;
ages[2] = 10;  /*使用下标修改数组元素*/
~~~

---

## 1.3 数组的遍历

~~~js
//使用while进行遍历
var len = ages.length;
var tmp = 0;
while (tmp < len) {
    console.log(ages[tmp++]);
}
~~~

~~~js
//使用for循环来进行数组的遍历
for (var i = 0; i < ages.length; i++) {
    console.log(ages[i]);
}
~~~

~~~js
//使用for..in的方式进行遍历
for (var index in ages) {
    console.log(ages[index]);
}
~~~

## 1.4 数组实现映射

```js
var mapData = [];
mapData["name"] = "admin";
mapData["age"] = 20;
mapData[0] = 100;
//数组的遍历   不能使用普通的for循环和while进行遍历
for(i in mapData){
console.log(mapData[i]);
}
```

## 1.5 二维数组

~~~js
var data = [[10, 20, 30], [40, 50, 60]];
//二维数组的遍历
for(i in data){
    for(j in data[i]){
        console.log(data[i][j]);
    }
}
~~~

注意: 数组一般到二维,如果二维数组还解决不了你的问题,那就要改变解决问题的思路了;

---

## 1.6 数组实现栈(FIEO)

~~~js
//push: 尾部追加
data.push(10, 20, 30);
data.push(40)

//尾部移除
data.pop()
console.log(data);
~~~

---

## 1.7 数组实现队列(FIFO)

~~~js
var data = [];
//push: 尾部追加
data.push(10, 20, 30);
data.push(40)
console.log(data);

//shift: 首部移除
data.shift();
console.log(data);
~~~

---

# 2. js中的自定义对象

~~~js
var name = "admin";
//对象的定义
var obj = {
    name,
    age: 20,
    sex: '男'
};

//给对象动态的添加属性
obj.address = "陕西省西安市"

//对象属性的访问
console.log(obj.address);
~~~

# 3. js中的函数

## 3.1 函数的定义

~~~js
function 函数名称(形参列表){
    函数体
}
~~~



## 3.2 匿名函数

- 函数是可以没有函数名称的;

- 把没有函数名称的函数称为 "匿名函数"

- js中的函数也是`对象`

- 匿名函数一定要先定义再使用

  ~~~js
  //匿名函数
  var func2 = function () {
      console.log("匿名函数");
  }
  
  //匿名函数的调用
  func2();
  ~~~

- 函数也可以作为对象的属性

  ~~~js
  var obj = {
      name: "admin",
      age: 20,
      //对象的属性也可以是函数对象
      say: function () {
          console.log(this.name + "::" + this.age);
      }
  }
  
  //对象属性的调用
  obj.say();
  ~~~

  ---

  # 4. 字符串的操作

  ~~~js
  var str = "hello xzy";
  //截取指定位置的字符
  console.log(str.charAt(1));
  //字符串的拼接(原来的str这个字符串是不会发生变化的)
  var str1 = str + "java大数据"
  //判断是否以指定的字符结尾  返回boolean类型
  console.log(str.endsWith("1xzy"));
  //判断是否以指定的字符串开头
  str.startsWith("he");
  //字符串的长度
  console.log(str.length);
  //去掉字符串首尾的空格
  console.log(str.trim().length);
  //指定字符在字符串中首次出现的位置
  console.log(str.indexOf("l"));
  //指定字符在字符串中最后一次出现的位置
  console.log(str.lastIndexOf("l"));
  //字符串的截取
  console.log(str.substr(2, 2));
  //转换为小写
  console.log(str.toLowerCase());
  //转换为大写
  console.log(str.toUpperCase());
  //字符串的替换
  console.log(str.replace("h", "rr"));
  ~~~

---

# 4. 正则表达式

就是用来进行字符串的匹配;

## 4.1 正则对象的创建

~~~js
1)  var regexp=  new RegExp("表达式");
2)  var regexp =  /表达式/;
~~~

## 4.2 正则表达式的范围表示

~~~js
[]: 表示范围
[a-z]:  a到z之间的所有字母
[3-9]:  3-9之间的所有数字
~~~

## 4.3 通配符的表示

~~~js
\d: 匹配所有的数字
\D: 所有的非数字
\s: 所有的空白字符
\S: 所有的非空白字符
\w: 所有的字母 数字 下划线
\W:所有 非(字母 数字 下划线的)
.: 代表任意字符
~~~

---

## 4.4 正则表达式的量词

~~~shell
{m}: 匹配具体的m个数
{m,n}: 匹配最少m个最多n个
{m,}: 至少匹配m个
*: ===>{0,}
+:===>{1,}
?:===>{0,1}
~~~

---

## 4.5 正则表达式开始和结尾

~~~shell
^: 表示字符串的开始
$: 表示字符串的结尾
~~~

---

## 4.6 子表达式

~~~shell
(): 子表达式
~~~

## 4.7 正则表达式的计算

~~~shell
| :或
~~~

## 4.8 正则表达式的转义符号

~~~shell
\
~~~

## 4.9 匹配qq邮箱或者163邮箱

~~~shell
手机号好@qq/163.com
~~~

~~~js
var str = "13991813302@qq.com";
var regexp = /^1[3-9]\d{9}@((qq)|(163))\.com$/

let ret = regexp.test(str);
console.log(ret);
~~~

# 5. js中的闭包(了解)

- 外部函数内部定义了一个内部函数
- 外部函数的返回值是内部函数对象
- 内部函数中使用了外部函数的参数

**符合以上三个条件函数就是闭包函数;**

~~~js
//外部函数
function outter(a, b) {
    //内部函数
    function inner() {
        console.log("a+b=" + (a + b));
    }
    //外部函数的返回值是"内部函数对象"
    return inner;
}

//调用外部函数,返回内部函数对象
var innerFunc = outter(10, 20)
//调用内部函数
innerFunc();
~~~

# 6. 柯里化(了解)

在以上的闭包函数中,调用起来很麻烦,我们可以这样来调用

~~~shell
outter(10,20)();
~~~

# 7. 函数对象作为函数的参数

~~~js
//相当于我写好了一个接口
function calculate(a, b, optFuc) {
    return optFuc(a, b)
}

//相当于实现
var ret = calculate(10, 20, function (i, j) {
    return i + j;
})
console.log(ret);
~~~

---

# 8. EcmaScript6中新增的内容

## 8.1 变量及其常量的定义

~~~shell
let a = 10;//定义变量a
const b="hello";//定义常量
~~~

---

## 8.2 es6中新增了箭头函数

~~~shell
let func = (新参列表) => {函数体}
~~~

- 定义箭头函数其 `定义的返回值是一个函数对象func`
- 调用箭头函数,函数的返回值函数体中的最后一行语句的结果
- 函数体中只有一行语句  {}  可以省略
- 函数的形参只有一个参数,那么函数形参的 () 可以省略

~~~shell
箭头函数中的this指的不是其调用的对象,而是其定义的顶层对象;
普通的匿名函数中的this指的是定义的对象
~~~

---

## 8.3 es6中的模块化编程

在原生的js并没有模块化编程,但是随着前端的项目越来越复杂,而且团队之间需要很好的写作,原生的src引入其他脚本的方式显得不是很OK,那咋办?有一些大牛就提出来了一些模块化的规范,这些规范中被大家广泛接受的有两个, commonjs和es6两种模块化的规范;

> 大家现在还无法使用下面的这些语法,先把语法记下来

普通方式暴露接口:

~~~js
export {变量名称}  //普通方式暴露变量可以暴露多个变量出去
~~~

默认暴露方式:

~~~js
export default {变量名称}  //默认的暴露变量全局只能暴露一个出去
~~~

导入变量的方式:

~~~js
import {变量名称,...} from "路径"   //导入普通方式暴露的变量
~~~

默认的导入变量的方式:

~~~shell
import 随便写一个名称  from "路径"  //导入default暴露的变量
~~~

---

## 8.4 es6中的扩展运算符

扩展运算符可以进行字符串转数组,对象的复制,**数组的合并**;

~~~js
let array1 = [10, 20, 30, 40]
let array2 = [50, 90, 80]

//es6数组元素的合并,返回新数组(兼容性差)
let ret =  [...array1,...array2]

//es5中的数组的合并(兼容性好)
let array3 = array1.concat(array2)
console.log(array3);
console.log("....");
console.log(ret);
~~~


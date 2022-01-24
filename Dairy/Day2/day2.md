# JavaScript

- 使用 **window.alert()** 弹出警告框。
- 使用 **document.write()** 方法将内容写到 HTML 文档中。
- 使用 **innerHTML** 写入到 HTML 元素。
- 使用 **console.log()** 写入到浏览器的控制台



**document.getElementById("demo")** 是使用 id 属性来查找 HTML 元素的 JavaScript 代码 。

**innerHTML = "段落已修改。"** 是用于修改元素的 HTML 内容(innerHTML)的 JavaScript 代码。

# 语法

JavaScript 使用关键字 **var** 来定义变量

var 关键词来声明变量

未声明的变量赋值作为全局变量

## 约束验证 DOM 方法

| checkValidity() | 如果 input 元素中的数据是合法的返回 true，否则返回 false。 |
| --------------- | ---------------------------------------------------------- |
|                 |                                                            |

------

let 命令使得变量只在所在的代码块 **{}** 内有效

const 用于声明一个或多个常量，声明时必须进行初始化，且初始化后值不可再修改（不能先声明再使用）

# JSON

##### 语法规则

- 数据为 键/值 对。
- 数据由逗号分隔。
- 大括号保存对象
- 方括号保存数组

JSON转化为JavaScript

```javascript
var text = '{ "sites" : [' +
    '{ "name":"Runoob" , "url":"www.runoob.com" },' +
    '{ "name":"Google" , "url":"www.google.com" },' +
    '{ "name":"Taobao" , "url":"www.taobao.com" } ]}';
    
obj = JSON.parse(text);
document.getElementById("demo").innerHTML = obj.sites[1].name + " " + obj.sites[1].url;


```

# 异步线程

```javascript
setTimeout(function () {    document.getElementById("demo").innerHTML="RUNOOB!"; }, 3000);
```

# DOM

查找HTML元素

- 通过 id 找到 HTML 元素
- 通过标签名找到 HTML 元素
- 通过类名找到 HTML 元素
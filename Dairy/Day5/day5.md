# el挂载点

el是用来设置Vue实例挂载（管理）的元素

el命中的元素内部

# data数据对象

Vue中用到的数据定义在data中

data中可以写复杂类型的数据

遵循js语法

# method方法

提供一个方法

# Vue指令

#### v-text简写（{{}}）

1. 设置标签的内容

2. ```html
   <div id="app">
           <h2 v-text="message">深圳</h2>
           <h2 v-text="info">深圳</h2><!--这两种会直接覆盖-->
           <h2>{{message}}深圳</h2>
       </div>
       <!-- 开发环境版本，包含了有帮助的命令行警告 -->
       <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
       <script>
           var v = new Vue({
               el:"#app",
               data: {
                   message:"wije" ,
                   info:"weqe"
               }
           })
       </script>
   ```

   默认写法会替换全部内容，使用差值表达式{{}}可以替换指定内容

#### v-html

内容中有html结构会被解析为标签

#### v-on

为元素绑定事件

#### v-show显示与隐藏

#### v-if

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="app">
        <input type="button" value="切换显示" @click="change"><br>
        <span v-if="isShow">156161</span>
    </div>
    <!-- 开发环境版本，包含了有帮助的命令行警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
    <script>
        var a =new Vue({
            el:"#app",
            data:{isShow:false},
            methods:{
                change:function(){
                    this.isShow = !this.isShow
                },
            }
        })
    </script>
</body>
</html>
```

![image-20220121143330639](C:/Users/Ljm/AppData/Roaming/Typora/typora-user-images/image-20220121143330639.png)

#### v-bind设置元素属性（简写 :属性）

#### v-for根据数据生成列表结构

```html
<li v-for="(it,index) in 数组名"</li>//数组
<li v-for="item in 字典名"</li>
```





```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body {
            text-align: center
        }

        div {
            width: 400px;
            height: 600px;
            border: 1px solid rgb(0, 0, 0);
        }

        li {
            text-align: left;
            width: auto;
            white-space: nowrap;
        }

        button {
            height: auto;
            width: auto;
        }
    </style>
</head>

<body>
    <div>
        <h1><B>TODO</B></h1>

        <ul id="mainlist">
            <input v-model="inputvalue" type="text" placeholder="请输入事件" @keyup.enter="add">
            <li v-for="(item,index) in list">

                <runoob-input v-model="list[index]"></runoob-input>

                <button class="destroy" @click="remove(index)">删除</button>
            </li>

        </ul>

    </div>
    <!-- 开发环境版本，包含了有帮助的命令行警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
    <script>
        Vue.component('runoob-input', {//实现修改功能
            template: `
    <p>   <!-- 包含了名为 input 的事件 -->
      <input
       ref="input"
       :value="value" 
       @input="$emit('input', $event.target.value)"
      >
    </p>
    `,
            props: ['value'], // 名为 value 的 prop
        })
        var a = new Vue({
            el: "#mainlist",
            data: {
                list: ["a", "b"],

            },
            methods: {
                add: function () {//增加
                    this.list.push(this.inputvalue)
                },
                remove: function (index) {//删除
                    this.list.splice(index)
                },
            }
        })
    </script>

</body>

</html>
```

效果图

![image-20220121214203199](C:/Users/Ljm/AppData/Roaming/Typora/typora-user-images/image-20220121214203199.png)

```html
var text = '{ "sites" : [' +
    '{ "name":"Runoob" , "url":"www.runoob.com" },' +
    '{ "name":"Google" , "url":"www.google.com" },' +
    '{ "name":"Taobao" , "url":"www.taobao.com" } ]}';
    
obj = JSON.parse(text);
document.getElementById("demo").innerHTML = obj.sites[1].name + " " + obj.sites[1].url;

```

```html
a:link {color:#FF0000;} /* 未访问的链接 */
a:visited {color:#00FF00;} /* 已访问的链接 */
a:hover {color:#FF00FF;} /* 鼠标划过链接 */
a:active {color:#0000FF;} /* 已选中的链接 */
```

# KNN

```python
#KNN算法
import random
#读取
import csv#读取工具
with open('Prostate_Cancer.csv','r') as file:#打开文件，只读
    reader=csv.DictReader(file)#以字典的形式读取文件
    datas = [row for row in reader]

random.shuffle(datas)#打乱顺序
n=len(datas)//3#分组：训练集和测试集(2/3)

test_set=datas[0:n]
train_set=datas[n:]

#距离(欧式距离)
def distance(d1,d2):
    res=0

    for key in ("radius","texture" ,"perimeter","area" , "smoothness",	"compactness","symmetry","fractal_dimension"):
        res+=(float(d1[key])-float(d2[key]))**2#d1,d2数据中相同属性的距离
    return res**0.5


k=5
def knn(data):
    #1.距离
    res=[
        {"results":train['diagnosis_result'],"distance":distance(data,train)}
        #计算训练集中的每一个数据与测试的那个数据的距离
        for train in train_set
    ]

    #2.排序--按照distance升序
    res=sorted(res,key=lambda item:item['distance'])#排序，便于后面的权重计算
    #3.取前k个
    res2=res[0:k]


    #加权平均
    result={'B':0,'M':0}#记录权重占比

    #总距离（用来计算权重）
    sum=0
    for r in res2:
        sum+=r['distance']
    for r in res2:
        result[r['result']]+=1-r['distance']/sum

    if result['B']>result['M']:
        return 'B'
    else:
        return 'M'

#测试阶段
correct=0
for test in test_set:
    result=test['diagnosis_result']
    result2=knn(test)

    if result==result2:
        correct+=1
print("准确率:{:.2f}".format(100*correct/len(test_set)))
```

# Vue

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


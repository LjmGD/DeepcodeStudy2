###### 用Python编写函数：输⼊变量n，输出形如{1:1, … ,n: n*n} 的字典。例如当n=8时，输出{1: 1，2: 4, 3: 9, 4: 16, 5:25, 6: 36, 7: 49, 8: 64}

```python
def caluate(n):
    res = {}
    for i in range(1,n):
            res.update({i:i*i})
    return res
print(caluate(8))
```

# 矩阵的秩

计算一个矩阵的秩，通过化到最简得到阶梯形矩阵，这个阶梯形矩阵中非零行的个数就是原来原来矩阵的秩。

1. 当系数矩阵的秩≠增广矩阵的秩时，方程无解
2. 当系数矩阵的秩＝增广矩阵的秩时，方程有解，当系数矩阵的秩＝未知量的个数时，有唯一解。当系数矩阵的秩＜未知量的个数时，有无穷多解。

###### 求解以下非齐次线性方程组![微信图片_20220120205343](D:\图片\微信图片_20220120205343.jpg)

###### 求矩阵的逆![微信图片_20220120205355](D:\图片\微信图片_20220120205355.jpg)

###### 求解t![微信图片_20220120205401](D:\图片\微信图片_20220120205401.jpg)

# 闵氏距离

公式：![img](https://bkimg.cdn.bcebos.com/formula/5461915cb8cdb80332251b27ecb23270.svg)

1. 当p=1时,得到绝对值距离，也叫曼哈顿距离，即计算两点之间的直角边距离，相当于城市中出租汽车沿城市街道拐直角前进而不能走两点连接间的最短距离。
2. 当p=2时，得到欧式距离



# KNN算法

 原理：寻找离新数据最近的点来预测新数据

通用步骤：

1. 计算距离
2. 升序排列
3. 取前k个
4. 加权平均

K的选取：

欧氏距离

二维空间两个点的欧式距离计算公式如下：

![二维空间欧式距离](https://img2018.cnblogs.com/blog/1011838/201811/1011838-20181105210120839-1494903025.jpg)

多维空间：

![多维空间欧式距离](https://img2018.cnblogs.com/blog/1011838/201811/1011838-20181105210113366-1125611006.jpg)

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


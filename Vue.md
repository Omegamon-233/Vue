# Vue

```vue
Vue.config.productionTip=false  //阻止vue启动时生成生产提示
```

## 初始Vue

1. 想让Vue工作，就必须创建一个Vue实例，且要传入一个配置对象
2. app容器里的代码依然符合html规范，只不过混入一些特色的Vue语法
3. app容器里的代码被称为【Vue模板】
4. Vue实例和容器是一一对应
5. 真实开发中只有一个Vue实例，并且会配合着组件一起使用
6. {{xxx}}中的xxx要写js表达式，且xxx可以自动读取data中的所有属性
7. 一旦data中的数据发生改变，那么页面中用到该数据的地方也会自动更新

## 注意区分：js表达式和js代码

1. 表达式：一个表达式会生成一个值，可以放在任何一个需要值的地方：(1). a

   (2). a+b

   (3).demo(1)

   (4).x == y ? 'a' : 'b'

2. js代码（语句）

   (1). if(){}

   (2). for(){}

## Vue模板语法有两大类

1. 插值语法：

   功能：用于解析标签内容

   写法：{{xxx}},xxx是js表达式，且可以直接提取到data中的所有属性

2. 指令语法：

   功能：用于解析标签（包括：标签属性，标签体内容、绑定事件......）

   举例：v-bing:href="xxx" 或简写为：:href="xxx"，xxx同样要写js表达式且可以直接读取到data中			的所有属性

   备注：Vue中有很多的指令，且形式都是：v-???，此处只是拿v-bing举例子

## Vue中的2种数据绑定的方法

1. 单向绑定(v-bing)：数据只能从data流向页面

2. 双向绑定(v-model)：数据不仅能从data流向页面，还可以从页面流向data

   备注：

   		1. 双向绑定一般都应用在表单类元素上（如：input、select等）
   
     		2. v-model:value 可以简写为v-model，因为v-model默认收集的就是value值

v-model只能用在表单类元素（输入类元素）上

## data与el的2种写法

1. el有两种写法

   (1). new Vue时候配置el属性

   (2).先创建Vue实例，随后再通过vm.$mount('#app')指定el值

2. data有两种写法

   (1). 对象式

   (2). 函数式

   如何选择：目前哪种写法都可以，以后学习到组件时，data必须使用函数式，否则会报错

3. 一个重要原则

   由Vue管理的函数：一定不要写箭头函数，一旦写了箭头函数，this就不再是Vue实例了

## MVVM模型

1. M：模型（Model）：对应data中的数据

2. V：视图（view）：模板

3. VM：视图模型（ViewModel）：Vue实例对象

   观察发现

   1. data中所有的属性，最后都出现在了vm身上
   2. vm身上所有的属性及Vue原型上所有的属性：在Vue模板中都可以直接使用

## Vue中的数据代理

数据代理：通过一个对象代理对另一个对象中属性的操作（读/写）

1.Vue中的数据代理：通过vm对象来代理data对象中属性的操作（读/写）

2.Vue中数据代理的好处：更加方便的操作data中的数据

3.基本原理：

​	通过Object.defineProperty()把data对象中所有属性添加到vm上

​	为每一个添加到vm上的属性，都指定一个getter/setter

​	在getter/setter内部去操作（读/写）data中对应的属性
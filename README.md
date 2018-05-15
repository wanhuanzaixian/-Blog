1、vue 理解：
1、使用vue不必担心布局更改和类名重复导致的js重写，因为它是靠数据驱动双向绑定，底层是通过Object.defineProperty()定义的数据 set、get 函数原理实现。
2、组件化开发，让项目的可拓展性、移植性更好，代码重用性更高，就好像农民工建房子，拿起自己的工具包就可以开工。项目经理坐等收楼就好。
3、单页应用的体验零距离接触安卓原生应用，局部组件更新界面，让用户体验更快速省时。
4、js的代码无形的规范，团队合作开发代码可阅读性更高。

2、mvvm模式的理解：
  m:moder； 数据业务层
  v：view ：页面模板；
  vm：viewmoder ： 两者的链接桥梁；将数据业务层提供的数据转换为页面；

模块：按照项目业务内容来划分大模块；
组件：按照一些小功能的通用性和可复用性来抽象组件；

3、vue生命周期理解：
总共分为8个阶段创建前/后，载入前/后，更新前/后，销毁前/后。
创建前/后： 在beforeCreated阶段，vue实例的挂载元素$el和数据对象data都为undefined，还未初始化。在created阶段，vue实例的数据对象data有了，$el还没有。
载入前/后：在beforeMount阶段，vue实例的$el和data都初始化了，但还是挂载之前为虚拟的dom节点，data.message还未替换。在mounted阶段，vue实例挂载完成，data.message成功渲染。
更新前/后：当data变化时，会触发beforeUpdate和updated方法。
销毁前/后：在执行destroy方法后，对data的改变不会再触发周期函数，说明此时vue实例已经解除了事件监听以及和dom的绑定，但是dom结构依然存在

4、vue组件之间数据交互/通信方式：
a、父子组件通信用props
b、非父子组件通信同样也可以用Vue.$emit自定义事件来解决
c、跨组件通信使用Vuex状态管理；
vuex最大的作用就是把部分父子组件之间频繁的通信过程简单化，所以，对于一些父子组件通信并不频繁的情况来说，并不应该使用vuex

5、路由：vue-router：
    1、怎么实现嵌套路由：在 VueRouter 的参数中使用 children 配置
    2、他是一个映射关系（path：component）请求一个路径得到一个组件；使用router-link传递参数；（还有一种传递方式 $router）
路由大致步骤：
①、下载路由模块 npm vue-router
②、创建Router，映射路由路径；
③、使用v-link指令跳转到指定路径；
④、使用<router-view></router-view>标签，它用于渲染组件；
⑤、启动路由； router.start；（S大特）

   3、动态指定路由：
   在router目录下的index.js文件中，对path属性加上/:id。
   使用router对象的params.id。


6、双向数据绑定原理：
利用了 Object对象defineProperty() 这个方法重新定义了对象获取属性值(getter)和设置属性值(setter)的操作来实现的。
Object.defineProperty() 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性， 并返回这个对象；

a、强制绑定：v-bind  （简写：：两个冒号）-》需要实现动态数据的时候使用；
b、事件监听：v-on   （简写：@）；
c、v-if：判断是否隐藏；
     v-for：数据循环出来；
     v-bind:class：绑定一个属性；
     v-model：实现双向绑定

c、计算属性：computed  ：
    ①、当需要数据是有data中的某个/些属性数据来确定的时候      get 
    ②、当这个数据变化时，data中的数据也要随之变化                  set

需要监视对象内部所有的属性数据时 需要用到 深度监视。

d、什么时候用methods？什么时候用computed? 什么时候用watch？
      1、methods：methods是个方法，比如你点击事件要执行一个方法，这时候就用methods；
      2、computed：computed是计算属性，实时响应的，比如你要根据data里一个值随时变化做出一些处理，就用computed。
      3、watch：数据变化响应的时候 ，需要监听数据变化的时候。
总结：methods里面定义的函数，是需要主动调用的，而和watch和computed相关的函数，会自动调用,完成我们希望完成的作用。

e、 事件修饰符:
     .prevent : 阻止事件的默认行为 event.preventDefault()
     .stop : 停止事件冒泡 event.stopPropagation()

f、什么是自定义指令：
使用 Vue.directives()定义指令，然后在标签中使用  v-指令 调用    （德来克德）

j：请说下封装 vue 组件的过程？
       ①、使用Vue.extend方法创建一个组件构造器；
       ②、然后使用Vue.component方法注册组件。
       ③、props中接受定义子组件需要数据。而子组件修改好数据后，想把数据传递给父组件。可以采用emit方法。

e、vuex怎么用？
     State：（SD他）是一个数据源。
     Getters： 通过Getters派生出新的状态。（判断一个符合条件的数据）
     Mutations： 更改Vuex中的store中的状态唯一方法是提交mutations （修改数据状态）
     Actions： 提交mutation，里面可做异步操作；
     modules：管理规范。





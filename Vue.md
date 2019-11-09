1. 什么是生命周期？

   - Vue实例从创建到销毁的过程，就是生命周期。从开始创建、初始化数据、编译模板、挂载DOM->渲染、更新->渲染、销毁等一系列过程，称之为Vue的生命周期。

   - ①boreCreate：创建前，在数据观测和初始化事件还未开始

     ②created：创建后，获取data里面数据，没有DOM

     ③beforeMount：载入前，相关的render首次被调用，把data里面的数据和模板生成HTML，但并没有挂在到页面上

     ④mounted：载入后，用上面编译好的html内容替换掉el所指向的DOM对象，此过程中进行ajax操作

     ⑤beforeUpdate：更新前，在数据更新之前调用，发生虚拟DOM渲染之前

     ⑥uodated：更新后，组件DOM已经更新，可以执行依赖于DOM的操作

     ⑦beforeDestroy：销毁前，在实例销毁之前调用

     ⑧destroyed：销毁后，所有的事件监听都会被移出

2. 组件传值分类

   - ①父传子:子元素通过props方法接受数据
   - ②子传父:$emit方法传递参数,页面一上来触发了beforeCreate、created、beforeMount、mounted四个方法
   - 兄弟：创建一个new Vue 实例，用它来传递和接受数据

3. v-if/v-show区别

   - v-if，是否渲染这个标签
   - v-show，display控制none/block

4. vue怎么封装组件

   - 建立组件的模板；props接受外部数据；处理数据；数据输出；案例；面包屑的封装

5. 路由守卫，路由钩子函数

   - 当路由发生变化的时候，我们想要做的事情：全局守卫；组件内局部；路由独享的守卫

6. 解释一下vue的双向数据绑定

   - 表单控件上添加v-model，视图改变驱动数据改变

7. vue的双向数据绑定的原理

   - VUE实现双向数据绑定的原理就是利用了 Object.defineProperty() 这个方法重新定义了对象获取属性值(get)和设置属性值(set)的操作来实现的。

8. 你对mvvm开发模式的理解

   - 在mvvm架构下，view和model并没有直接联系，而是通过ViewModel进行交互，Model和ViewModel之间的交互是双向的，因此view和model的数据变化会同步。
   - M--model,数据模型，可以定义数据修改和操作的业务逻辑
   - V--view，UI组件，视图区域
   - VM--监听模型数据的改变和控制视图区域的行为，是一个同步view和model的对象

9. vue有哪些指令

   - v-for；v-if；v-bind简写 ‘：’；v-show；v-else；v-on 简写:@

10. vue-router怎么配置路由

    - router-link制作导航；设置容器 router-view；
      - 1. 导入 vue-router
        2. 导入业务模块
        3. 路由注册 ： Vue.use(VueRouter)
        4. 创建路由对象，配置路由new VueRouter({routes : [{},{},{}]})
        5. 在Vue实例中挂载路由

11. 怎么解决spa首屏加载慢的问题

    - 懒加载--这种优化，就是将每个组件的js代码独立出来，在使用到这个组件时，才向服务器请求文件，并且请求过一次后就会缓存下来，再次使用到这个组件时，就会使用缓存，不再发送请求
    - CDN引入依赖文件

12. 配置路由没有问题，但是组件没有渲染出来有几种原因

    - router-view 容器没写；template没有一个根标签；路由未挂载

13. vue全家桶是什么

    - Vue-cli 项目构建工具；vue-router 路由；vuex 状态管理；axios http请求工具；webpack 项目打包工具，

14. vue和jQuery有什么区别

15. vue的核心特性

16. 路由之间怎么进行跳转

17. 说说你对vuex的了解

18. vuex有哪几种属性

19. 说一下vue项目为什么用axios，不使用jQuery的$ajax和原生ajax

20. 说一下computed和methods以及watch的区别

21. 说说你在vue中踩过的坑

22. 你是怎么考虑vue不利于seo优化问题的

23. 你用vue里面的过滤器实现了什么功能

24. vue为什么在new实例化的时候data是一个对象，在组件中是一个函数

25. 说一下MVVM和MVC的区别

26. 谈谈你对webpack配置的理解

27. vue-router路由的两种实现模式，但是vue-router默认的是hash模式

28. vue怎么实现组件缓存

29. axios怎么实现同步的请求

30. vue的项目文件结构有什么

31. vue-router是干什么的，原理是什么

32. vue打包出现空白index.html怎么解决

33. vue怎么实现跨域
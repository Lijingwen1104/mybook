<!-- 1. 项目经历
2. vue
生命周期 作用 created mouted 区别
父子组件通信
跨级组件通信
项目复杂后管理数据
vuex 原理
异步操作
data 函数 不是对象
自定义指令
vue react 优缺点
vue 封装组件
vue 原理
vdom 的原理
defineProperty 
3. 判断对象类型

4. 闭包及应用
var fun1 = function() {
    var a = 1;
    return function() {
        a = a +1
        return  a
    }
}
var a = fun1()
5. 原型是怎么回事 手写原型链的继承
6. 定时器哪几种 区别用法 执行时机
7. settimeout 实现 setintervel  缺点
8. 事件循环 队列 宏任务  微任务
9. this 指向 如何改变this 指向 
call apply bind 三种方法 apply call 实现bind
10. 数组常用方法
11. 实现Array.reduce
12. 判断是不是数组
13. 斐波那契数列 
14. dom常见操作方法
15. 事件冒泡 事件捕获 事件代理 手写事件代理
16. ajax 调用过程 XHR 
17. get post 区别 
18. 常用状态码 200 204  304 302 301 404 502 500 504 
200成功 ；204无内容； 301页面转移至新的url；302暂时转移至新的url ；304命中协商缓存，从缓存中读取； 404找不到页面 ；500服务器错误 ；502； 504网关超时；
19. 跨域有哪几种方式

20. jsonp 的原理
21. 浏览器缓存怎么做 那几个header 确定
22. 项目性能优化
23. webpack gulp 区别
24. 模块化含义 用法
25. 图片懒加载
26. 节流防抖
27. es6特性
28. let var const 
29. 解构 let {name,age} = person 数组解构 let [a,b] = [1,2,3]
30. ...
31. 装饰器
32. 导入导出 import export 
33. 箭头函数
34. class 原型链 区别 静态属性
25. promise 为什么可以链式调用 常见方法 异常的捕获 用来解决什么问题的 执行顺序
26. generator 进行异步转同步
27. async wait 和上两个的关系
28. Symbol
29. 数组去重
30. url 查询字符解析
31. 移动端兼容性问题 适配  各种居中
32. 定位有什么区别
33. 浮动 文档流 清除浮动
34. 等高布局
35. BFC 相关
36. 动画
37. transition animation 
38. nodejs express koa 中间件
39. WebSocket


var age = 2
var person = function() {
    var age = 1 
}
person.say = function(){
    console.log(age)
}
person.say()


var fun1 = function() {
    var a = 1;
    return function() {
        a = a +1
        return  a
    }
}
var a = fun1()



// this
var fun1 = function() {
    var a = 1;
    return function() {
        a = a +1
        return  a
    }
}
var a = fun1()


Object.keys() 与 for in 

class 中的this 

class extends 的关系

class B class extends  A  B 的属性不能继承A 

class constructor 中的 this.name 不会被继承，  方法会被继承 super 和 this

    * [第五话 数组方法的实现](javascript/array.md)
    * [闭包及其应用](javascript/closure.md)
    * [容易混淆的字符串、数组方法](javascript/methods.md)
    * [正则表达式基本语法](javascript/reg.md)
* [css](css/css3.md)
    * [css3](css/css3.md)
    * [less基本语法](css/less.md)
    * [sass基本语法](css/sass.md)
* [nvm&nrm](front/nvm&nrm.md)
* [浏览器内部工作原理](front/browserswork.md)
* [MongoDB基本语法](front/mongodb.md)
* [git基本语法](front/git.md)
* [vue](vue/vue生命周期.md)
    * [生命周期](vue/vue生命周期.md)



-->
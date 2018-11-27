### Object.create 与 new 的区别

首先我们先来了解下这两种操作具体是干啥的

#### new

new 是一个运算符，用来创建一个对象类型的实例。

```js
function A () {

}
var a = new A();
```
那么在以上代码中，new到底做了些啥呢？

```
// 1. 创建一个空对象 o

var o = new Object();

// 2. 将o的原型设置为A 
o.__proto__ = A.prototype;

// 3. 更改A的this值，指向新创建的空对象

A.call(o);

```

#### create

Object.create()方法是 ECMAScript 5中新增的方法，这个方法用于创建一个新对象。被创建的对象会继承另一个对象的原型，在创建新对象时还可以指定一些属性。


```js
function A() {

}
var a = Object.create(A)
```
1. 创建一个空构造函数F， 
2. 将A作为F的原型对象
3. 返回这个构造函数的实例


对于a来说，他是F的实例

a.__proto__ === F.prototype

F.prototype === o

所以

a.__proto__ === Person


区别于  prototype.md !!

```
Object.create =  function (o) {
    var F = function () {};
    F.prototype = o;
    return new F();
}
```

a instanceof A  // false 

instance 判断的是 a.__proto__ 指向的是A 与 A.prototype 不相等，所以判断为false

mdn :  instanceof 运算符用来检测 constructor(A).prototype 是否存在于参数 object(a) 的原型链上。



### Object.create 与 new 的区别

首先我们先来了解下这两种操作具体是干啥的

#### new

new 是一个运算符，用来创建一个对象类型的实例。

```js
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



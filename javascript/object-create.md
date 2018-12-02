# 第三话 Object.created 与new的区别

[第二话 new到底干了些什么？](new.md)

## Object.create

> Object.create()方法是 ECMAScript 5中新增的方法，这个方法用于创建一个新对象。被创建的对象会继承另一个对象的原型，在创建新对象时还可以指定一些属性。


```js
function A() {

}
var a = Object.create(A)
```

那么Object.create(A)实际上做了哪些操作呢？ 我们模拟一个Create。

```js
function A() {

}
Object.myCreate =  function (A) {
    // 1. 创建一个空构造函数F， 
    var F = function () {};
    // 2. 将A作为F的原型对象
    F.prototype = A;
    // 3. 返回这个构造函数的实例
    return new F();
}
var a = Object.myCreate(A)
```

a 是myCreate函数内部的F的实例，

a.__proto__ => F.prototype

F.prototype => A


> Object.create(A) 方法用来创造一个原型为A 的实例。
```js
a.__proto__ === Person // true
```
那么通过 Object.create 新建的实例可以通 instanceof 来判断原型吗？ 

```js
a instanceof A  // false 
```

[第一话中关于instanceof的说明 ](原型.html#instanceof)

instance 判断的是 a.__proto__ 与 A.prototype 是否相等。所以***不能***使用instanceof来判断Object.create新建的实例的原型。

这里就需要 ```Object.isPrototypeOf```方法来判断a 的原型是谁了。

eg.
```js
A.isPrototypeOf(a) // true
``` 


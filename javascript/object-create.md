# 第三话 Object.created 与 new 的区别

[第二话 new到底干了些什么？](new.md)

## Object.create

> Object.create()方法是 ECMAScript 5中的方法，这个方法用于创建一个新对象。被创建的对象会继承另一个对象的原型，在创建新对象时还可以指定一些属性。

Object.create(A) 方法用来创造一个原型为A 的实例。

```js
function Person() {

}
var xiaoming = Object.create(Person)

// ⬇ xiaoming的原型 直接指向了Person，而不是像通过构造函数一样，指向Person.prototype。没有中间商赚差价。
xiaoming.__proto__ === Person //true

```
那么Object.create(Person)实际上做了哪些操作呢？ 我们模拟一个Create。

```js
function Person() {

}
Object.myCreate =  function (Person) {
    // 1. 创建一个空构造函数F， 
    var F = function () {};
    // 2. 将A作为F的原型对象
    F.prototype = Person;
    // 3. 返回这个构造函数的实例
    return new F();
}
var xiaoming = Object.myCreate(Person)
```

xiaoming 是myCreate函数内部的F的实例，并不是Person的实例。


```
xiaoming.__proto__ => F.prototype

F.prototype => Person
```

这里就需要 ```Object.isPrototypeOf```方法来判断a的原型是谁了。

不能使用 instanceof 判断
eg.
```js
A.isPrototypeOf(a) // true
``` 

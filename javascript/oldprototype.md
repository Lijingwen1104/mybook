<!-- ### JavaScript 第一话 原型

👌 先来搞明白什么是原型链

#### 构造函数 Pserson 与 实例 xiaoming

首先我们来搞一个函数

```js
var Person = function () {

}
```

我们来看下这个Person都有些啥属性

``` js
Person.prototype  instanceof Object // true

```
Person 有一个 prototype 属性, 指向了一个对象。这个对象是干啥用的呢？ 先不要着急，我们先把这个函数，当做构造函数，new一个实例出来。

``` js
var xiaoming = new Person()

```
xiaoming 有哪些属性呢？ 

```js
xiaoming.__proto__ === Person.prototype // true

```

划重点： Person  和 xiaoming 各有两个属性，指向了同一个对象，这个对象，叫做 xiaoming 的 【原型】。


我们就是通过这个原型的东西，来模拟其他面向原型的语言的

番外1： 


```js
var xiaohong = new Pserson()
xiaohong.__proto__ === xiaoming.__proto__  // true
```

不管多少个实例，共享同一个原型


#### 构造函数 Person 与 原型 

上面我们说到， 构造函数 Person 有一个 prototype属性， 指向了xiaoming的原型。

相反的呢，原型上有一个 constructor 属性，指向了 构造函数 Person

```js
Person.prototype.constructor === Person
```


#### 实例 xiaoming 与 原型

我们来给Person增加一个性别属性sex

```js
Person.prototype.sex = "男"
xiaoming.sex // "男"
```

👌 我们可以发现~ 我们并没有给xiaoming 设置性别，然而xiaoming.sex 还是输出了 sex 。 

划重点： 我们读取实例属性的过程中，如果没有该属性，会沿着原型链，一直找到最顶层为止。

好的，前面番外1中我们提到，所有的属性共享同一个原型，所以

```js
xiaohong.sex // "男"
```
😂 xiaohong说我是个吕孩子，👌

```js
xiaohong.sex = "女"

xiaohong.sex // "女"
```

这样我们就可以直接读取实例中的属性，不会找到原型。

#### 判断原型的方法

来整理下所有判断原型的方法，以及他们的原理：


```js
xiaoming instanceof Person // true

xiaoming.__proto__ === Person.prototype 

xiaoming.constructor === Person
```
注释： 对于 xiaoming.constructor === Person ， xiaoming 并没有 constructor 属性，然鹅，找到了xiaoming 原型上的 constructor, 原型的 constructor 指向了 Person 👌 


```js
function instance_of(L, R) {//L 表示左表达式，R 表示右表达式
 var O = R.prototype;// 取 R 的显示原型
 L = L.__proto__;// 取 L 的隐式原型
 while (true) { 
   if (L === null) 
     return false; 
   if (O === L)// 这里重点：当 O 严格等于 L 时，返回 true 
     return true; 
   L = L.__proto__; 
 } 
}
```

其实是判断的是 xiaoming 的 __proto__ 与 Person.prototype 是否向相等


#### 

### JavaScript 第二话 new 到底干了些什么？ 

this.md 作为构造函数构造函数中的this 指向的是 实例

```js
var Dog = function() {
  this.say = function  () {
    console.log('my name is'+ this.name)
  }
}
var dog = new Dog()
dog.name = '旺财'
dog.say()

// 模拟 new 的操作

var dog2 = {name: '来福'}

dog2.__proto__ = Dog.prototype 

Dog.call(dog2)

dog2.say()
```
1. 
```js
var Person = function() {
}
var xiaoming = new Object()

xiaoming.__proto_ = Person.prototype

Person.call(xiaoming)
```

然而 __proto__并不是标准的属性， 所以推荐使用 es6中的新语法

```js

Object.setPrototypeOf


``` 
来为对象设置原型 -->
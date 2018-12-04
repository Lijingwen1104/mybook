# 第五话 class

## 第一节 new class() 

从 babel 转义可以看出来， class 可以看做是

```js
var Person = class{
  
  
}
var xiaoming = new Person()
```

babel转义后

```js
"use strict";
// 以下babel转义忽略改函数

function _classCallCheck(instance, Constructor) { 
  //  xiaoming inxtanceof Person 
  if (!(instance instanceof Constructor)) { 
    throw new TypeError("Cannot call a class as a function"); 
  } 
}

var Person = function Person() {
  // this 指向 xiaoming
  // 判断 xiaoming 和 Person 的关系
  _classCallCheck(this, Person);
};
var xiaoming = new Person();
```

## 第二节 constructor

constructor 是class的构造函数， 在new一个实例的时候，会自动调用构造函数。

constructor 默认返回实例对象，可以手动返回新的对象

```js
class Person{
  constructor(config) {
    if (config && config.age) {
      this.age = config.age
    }
  }
  
}
var xiaoming = new Person({age: 12})

```
babel转义： 

```js
var Person = function Person(config) {
  _classCallCheck(this, Person);

  if (config && config.age) {
    this.age = config.age;
  }
};
var xiaoming = new Person({ age: 12 });
```

## 第三节 class 中的方法

类的所有方法都定义在类的prototype属性上面。在类的实例上面调用方法，其实就是调用原型上的方法。

```js
var Person = class{
  constructor(config) {
    if (config && config.age) {
      this.age = config.age
    }
  }
  toSay() {
    console.log('I am ' + this.age +' years old')
  }
}
var xiaoming = new Person({age: 12})
xiaoming.toSay() // my age is

Person.prototype.toSay
// ƒ toSay() {
//     console.log('my age is'+ this.age)
//   }

```
----
前三节讨论了class 与 原型的关系，下面看下class其他的知识点。

## 第四节 私有方法和私有属性

所有类上的方法，其实本质上都是挂在在原型上。
如第三节中的代码，还是可以通过Person.prototype.toSay()来调用这个方法。
所以在ES6中，并没有私有变量和私有属性的说法，有其他迂回的实现方式可以参考[阮一峰的ES6入门](http://es6.ruanyifeng.com/#docs/class#%E7%A7%81%E6%9C%89%E6%96%B9%E6%B3%95%E5%92%8C%E7%A7%81%E6%9C%89%E5%B1%9E%E6%80%A7)

## 第五节 extends 继承

```js
class Person{

}
class Student extends Person {

}
var xiaoming = new Student()

// ⬇ Person 是 Student 的原型
Object.getPrototypeOf(Student) === Person // true


// ⬇ xiaoming.__proto__ === Student.prototype 
Object.getPrototypeOf(xiaoming)=== Student.prototype // true

```

👌 我们可以大胆猜测， extends 是通过类似 ```var Student = Object.create(Person)``` 的方法来实现的。


## 第五节 静态方法

并不能通过实例调用的方法，静态方法中的this指向class。

```js
class Person {
  static toSay () {
    
    console.log('toSay')
  }
}
Person.toSay() // toSay
var xiaoming = new Person()
xiaoming.toSay // undefined
```

## new.target 属性

> new是从构造函数生成实例对象的命令。ES6 为new命令引入了一个new.target属性，该属性一般用在构造函数之中，返回new命令作用于的那个构造函数。如果构造函数不是通过new命令调用的，new.target会返回undefined，因此这个属性可以用来确定构造函数是怎么调用的。


## super对象 

super 代表的是父类的构造函数，在实例化子类的时候，会自动调用父类的构造函数。

通过super调用的父类constructor 中，this 既不指向实例， 也不指向父类，而是指向子类。

```js
class Person{
  constructor() {
    console.log(this)
    console.log(new.target.name)
  }
  toSay() {
    console.log('I am ' + this.age + ' years old Person')
  }
}
class Student extends Person {
  constructor(config) {
    super()
    this.age = config.age
  }
  toSay() {
    super.toSay()
    console.log('I am ' +  this.age +  ' years old Student')
  }
}

var xiaoming = new Student({age: 12})
xiaoming.toSay()
// Student {}
```

## class 实现单例模式

> 单利模式保证一个类仅有一个一个实例，并提供一个访问它的全局访问点
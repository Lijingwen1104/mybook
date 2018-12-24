# 第二话 new到底干了些什么？

上一话用了这样的代码

```js
var Person = function() {

}
var xiaoming = new Person()
```

那么new到底干了些什么呢？
我们稍微来改造下Person 这个构造函数，来理解下new到底干了些什么？ 

```js
var Person = function() {
  this.say = function () {
    console.log('my name is ' + this.name)
  }
}
var person = new Person()
person.name = xiaoming
person.say() // my name is xiaoming 
```

下面里模拟new 实现的代码： 

```js 
// 声明构造函数
var Person = function() {
  this.say = function () {
    console.log('my name is ' + this.name)
  }
}
// 声明实例
var person = {name: 'xiaoming'}

// 手动绑定 person 原型
person.__proto__ = Person.prototype 

// 更改构造的this指向
Person.call(person)

person.say()
```

然而 ```__proto__```并不是标准的属性， 所以推荐使用 es6中的新语法

```js
Object.setPrototypeOf(person, Person.prototype)

``` 
来为对象设置原型
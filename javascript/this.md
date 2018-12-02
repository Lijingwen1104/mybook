# 第三话 this的指向

1. 
在函数中，指向全局变量
```
var x = 1;
function test() {
   console.log(this.x);
}
test();  // 1

```
2. 
作为对象的方法调用，指向当前对象
var dog = {
  name :"wangcai"
  say: fucntion() {
    console.log(this.name)
  }
}
dog.say()

3. 
作为构造函数，指向当前new 出来的实例 

var Dog = function() {
  this.name = 'wangcai'
}
var dog = new Dog()
dog.name

4. 
使用 Call apply bind等改变


# 闭包

变量作用域分为全局和局部作用域。
在函数内部可以直接读取全局变量，函数外无法访问函数内局部变量。
如果需要读取函数内部的变量，可以再外层嵌套一层函数，把变量挂在外层函数中，这样就可以在内层函数中访问该变量。
闭包就是能够读取其他函数内部变量的函数。

```js
function f1(){

　　　　var n=999;

　　　　function f2(){
　　　　　　alert(n);
　　　　}

　　　　return f2;

　　}

　　var result=f1();

　　result(); // 999

```
f2就是闭包，是将函数内部和函数外部连接起来的一座桥梁。

```js
function f1(){
　　　　var n=999;
　　　　nAdd=function(){n+=1}
　　　　function f2(){
　　　　　　alert(n);
　　　　}
　　　　return f2;
　　}
　　var result=f1();
　　result(); // 999
　　nAdd();
　　result(); // 1000
```
思考一下两个闭包：

```js
  var name = "The Window";
　　var object = {
　　　　name : "My Object",
　　　　getNameFunc : function(){
　　　　　　return function(){
　　　　　　　　return this.name;
　　　　　　};
　　　　}
　　};

　alert(object.getNameFunc()());
　var name = "The Window";
　　var object = {
　　　　name : "My Object",
　　　　getNameFunc : function(){
　　　　　　var that = this;
　　　　　　return function(){
　　　　　　　　return that.name;
　　　　　　};
　　　　}
　　};

　alert(object.getNameFunc()());
```
闭包作用：一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。

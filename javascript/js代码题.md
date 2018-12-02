# apply 实现bind


var fun1 = function(a, b){
    console.log(this.num)
    console.log(a)
    console.log(b)
}
fun1.myBind = function(that, opts) {
    return function() {
        fun1.apply(that,opts)
    }
}
var fun2 = fun1.myBind({num: 1}, [2, 3])

# call 实现bind

var fun1 = function(a, b){
    console.log(this.num)
    console.log(a)
    console.log(b)
}
fun1.myBind = function() {
    const opts = arguments
    console.log('opts: ', opts)
    return function() {
        fun1.call(...opts)
    }
}
var fun2 = fun1.myBind({num: 1}, 2, 3)



var fun2 = fun1.myBind({num: 1}, 2, 3)
```
# 实现reduce
```js
var  a  = [1,2,3]

Array.prototype.myReduce = function(fn, start){
    var result = null
    for (let i = 0; i < this.length; i++) {
        if (i === 0) {
            result = fn(start, this[i],i,this)
        } else {
            result = fn(result, this[i],i,this)
        }
    }
    return result
}

a.myReduce(function(pre, next, index, array) {
    return pre + next
}, 0)
``
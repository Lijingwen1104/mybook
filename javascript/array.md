# 第四话 数组方法的实现



#### forEach
[在线演示](https://babeljs.io/repl/#?babili=false&browsers=&build=&builtIns=false&code_lz=DYUwLgBAhgTjEF4IG0BEVUBoKoEZZwGNUBdAKAEE4oBPAOgAcYB7MVmhkOgWxoDFmMAKJRCAC0QQAZgFcAdoTABLZnIgAKWXICUEAN5kIR6YI0A3WBCWSADAG4rEADwQwYpQGc6oOQHM3DkoA1EG6BsYR0vLqbp7ISiTYStixHtp2hsYAvmQ5sDA8_IIi4pryiipq6hbAMiBJcgAmIAAe2Pm0YZlGhKoezKDezL7VULX1Vk2t7dQ02rnpRkA&debug=false&circleciRepo=&evaluate=true&lineWrap=true&presets=es2015%2Cstage-2&prettier=false&targets=&version=6.26.0)
```js
let arr = ["a", "b", "c"]
Array.prototype.myForEach = function (fun) {
    for (var i = 0; i < this.length; i++) {
        fun(this[i], i, this);
    }
}
arr.myForEach(function (value, index, array) {
    console.log(value, index, array)
}); 
``` 
#### map
[在线演示](https://babeljs.io/repl/#?babili=false&browsers=&build=&builtIns=false&code_lz=DYUwLgBAhgTjEF4IG0BEVUBoKoEZZwGNUBdAKAEE4oBPAOgAcYB7MVmhkOgWxoFkoDRBABmAVwB2hMAEtmEiAApxEgJQQA3mQgQAbrAi9YMWsOQkA3NtHN4i_fBnCADBYhOAPBDAALGQGc6UAkAc183GQBqSPUtHR0janoGMX8fZUlFXwDkGRJsGWxs_1VVKx0AX2sYcDEYBUSTGisqhwgJEAB3Y2FjHn5BDKlZeSV9YDEQAokAExAAD2xjWljq2vq9KAmQCEicACZUFtUyQnl_ZlAg5hDFDu64MrIgA&debug=false&circleciRepo=&evaluate=true&lineWrap=true&presets=es2015%2Cstage-2&prettier=false&targets=&version=6.26.0)
```js
let arr = ["a", "b", "c"]
Array.prototype.myMap = function (fun) {
  var myarray = [];
  for (var i = 0; i < this.length; i++) {
    myarray.push(fun(this[i], i, this));
  }
  return myarray;
}
var newarr = arr.myMap(function (value, index, array) {
  return value + "2";
})
console.log(newarr);
```

#### every
[在线链接](https://babeljs.io/repl/#?babili=false&browsers=&build=&builtIns=false&code_lz=DYUwLgBAhgTjEF4IG0BEVUBoKoEZZwGNUBdAKAEE4oBPAOgAcYB7MVmhkOgWxoFEAbiBg1EEAGYBXAHaEwAS2bSIACinSAlBADeZCPogDYEXrmbNgYsDEkgA3HoPjm8FUfjyxABjsRPAHggwAAt5AGc6UGkAcxDfeQBqBK1dAwNHNP1Tc0skbIsIADJCiRkVEPDkeRJseWwKsI0MiABfZphwSRhlfOAyNvcIMwKkWBgefiERNRk5RWU3KGBbWukAExAAD2wx2hT2zu7DJdsIAEIkVE3UX36mwiUwiy5gZmiVYeANOyA&debug=false&circleciRepo=&evaluate=true&lineWrap=true&presets=es2015%2Cstage-2&prettier=false&targets=&version=6.26.0)
```js
let arr = ["a", "b", "c"]
Array.prototype.myEvery = function (fun) {
    var mybool = true;
    for (var i = 0; i < this.length; i++) {
      
        mybool = mybool && fun(this[i], i, this)
    }
    return mybool
}
var bool = arr.myEvery(function (value, index, array) {
    return value != "x"; 
})
console.log(bool);
```


#### some

[在线链接](https://babeljs.io/repl/#?babili=false&browsers=&build=&builtIns=false&code_lz=DYUwLgBAhgTjEF4IG0BEVUBoKoEZZwGNUBdAKAEE4oBPAOgAcYB7MVmhkOgWxoGVm3EIggAzAK4A7QmACWzSRAAUEyQEoIAbzIRdEAG6wIvXM2bARoqMADOIANw69o5vCWH4skQAZ7ELwA8EGAAFrI2dKCSAOahfrIA1Aka2nppEAD0GcY0sDC0jOI2ISpSSqHhyLIkmLKYFTZqao7peiZmFkjt5hAAPr1iZQ1VNf7YDc1OugC-UxAw4OIwit3AjrMeEKbmAEwieTz8giCl0nIKyobA4iDYspIAJiAAHth5tClzC2BLilc3iCQ6FQ6zUZEIChs5i4wGY0SU22AOzUQA&debug=false&circleciRepo=&evaluate=true&lineWrap=true&presets=es2015%2Cstage-2&prettier=false&targets=&version=6.26.0)
```js
let arr = ["a", "b", "c"]
Array.prototype.mySome = function (fun) {
    var mybool = false;
    for (var i = 0; i < this.length; i++) {
        // myarray.push(fun(this[i],i,this));
        mybool = mybool || fun(this[i], i, this);
    }
    return mybool;
}
var bool2 = arr.mySome(function (value, index, array) {
    return value == "a";
})
console.log(bool2)
```

#### filter

[在线链接](https://babeljs.io/repl/#?babili=false&browsers=&build=&builtIns=false&code_lz=G4QwTgBOYEwQvBA2gRgAwBoIpVlMBdAbgCgBBMMEATwDoAHMAewBdXr6BTWgW2oDEAlgBsWnSIgBmAVwB2AYxaCmsiAAoZsgJQQA3iQiGIoSH2g0EyYgaOSmkNSYiDLaIs4gAeCCwAWggGdaYU5ZAHM_d0EAamidfSNE50l1TTU_QKRBAixBLAyArXibJKSzShoGaQDfdP8ArIItEqSAXxb2xLBOFmkwVXKqalJ2p1lOAHdoOERp3gERMTANOUVlVUcQYWlOXNkAE04ADyxzamKunr7VUG3OCAA-bDcSVub5FQCmEOCmMLVxlNKDAtEQgA&debug=false&circleciRepo=&evaluate=true&lineWrap=true&presets=es2015%2Cstage-2&prettier=false&targets=&version=6.26.0)
```js
let arr2 = [10, 11, 12];
Array.prototype.myFilter = function (fun) {
    var myarray = [];
    for (var i = 0; i < this.length; i++) {
        if (fun(this[i], i, this)) {
            myarray.push(this[i])
        }
    }
    return myarray;
}
let newarr2 = arr2.myFilter(function (value, index, array) {
    return value > 10;
})
console.log(newarr2);
```

#### reduce 
[在线链接](https://babeljs.io/repl/#?babili=false&browsers=&build=&builtIns=false&code_lz=DYUwLgBAhgTjBMEC8EDaBGADAGgu9u68AugNwBQAgnFAJ4B0ADjAPZhu2Mj0C2tASiAAmAVwDGIZBABmIgHZiwASxZyIACllzcSuUuVRgASggBvchEsQAbrGgRsSilYhLpG3fqWGkv-UJBpXWETcxcXKCkwAAslAGdUTDILcMslJHRnKwBfCBBgOMkw1PsUTwNgLNT0zCqIbJTLaRYYdVIlAB4Y-PpQOQBzGPaAamGjYtSoFC11KGxuhKViR3nYuKM6hpcYcBEYNSgKBtsYCHYwQylYBF4BYXEQTXlFFTV1ZhBcORAADzAdOQBH64a50UKNCA7MB7NQfCDDCDfP5HXCYIzkMSqOIsUC9Fj9dTnQwbIA&debug=false&circleciRepo=&evaluate=true&lineWrap=true&presets=es2015%2Cstage-2&prettier=false&targets=&version=6.26.0)
```js
let arr2 = [10, 11, 12];
Array.prototype.myReduce = function (fun, initial) {
    var a ,i;
    if (initial===undefined) {
        a = this[0];
        i=1;
    } else {
        a = initial;
        i=0;
    }
    for(;i<this.length;i++){
        a= fun(a,this[i],i,this);
    }
    return a;
}
var total = arr2.myReduce(function (pre, next, index, array) {
    return pre + next;
}, 0)
console.log(total);
```

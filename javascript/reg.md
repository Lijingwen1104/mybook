### 正则表达式基本语法
- 正则表达式的实例化方法

    - 字面量 var reg =/\bis\b/g;（g代表全文搜索）  在JavaScript中/需要转译。写作//

    - 构造函数方式  var reg=new RegExp('\\bis\\b','g')

- 修饰符
    - g：global全文搜索，不添加，搜索到第一个匹配停止
    - i：ignore case忽略大小写，大小写皆匹配
    - m：multiple lines多行搜索

- 元字符

    - 正则表达式由两种基本字符类型组成

        - 原义文本字符（表示字符本身含义）

        - 元字符（在正则表达式中有特殊含义的非字母字符） . * + ？ $ ^. | \ ( ) { }

        ![图片1](./../imgs/reg1.png)


- 字符类
    - [  ]来构建类。指符合某些特性的对象，一个泛指，而不是某个特定字符。每个元字符之间是或的关系。

    - 字符类取反，在[  ]内部第一个添加^,各个元字符之间是与的关系

- 范围类
    - [  a-zA-Z  ]来构建范围类。每一个小范围间是或的关系。在范围外的  -  被解析为普通元字符（如[0-9-]）。

- 预定义类

    - 用来匹配常见字符类

    ![图片2](./../imgs/reg2.png)

- 边界
    - \b 单词边界  \B非单词边界   以^ 啥开始  以啥$ 结束

- 量词
    - ？出现零次或者一次（最多出现一次）
    - ```+ 出现一次或者多次（至少出现一次）```
    - ```*  出现零次或者多次（出现任意次）```
    - {n}出现n次
    - {n,m}出现n到m次
    - {n,}至少出现n次
    - {0,m}至多出现m次

- 贪婪模式与非贪婪模式

    - 默认为贪婪模式，尽可能的多的匹配。

    - 非贪婪模式，在量词后添加？如{3,5}?

- 分组
    - ( ) 使量词作用域分组，不作用于紧挨的

- 或
    - |  两个分组的或关系

- 反向引用

    - 用$n来匹配第n个分组

    - 分组如果需要忽略要在分组的最后？：

- 前瞻（JavaScript不支持后顾）

    - 正向前瞻

        - 在正则表达式匹配到规则的时候，检查是否符合断言
        - exp(?=assert)

    - 负向前瞻

        - 在正则表达式匹配到规则的时候，检查是否不符合断言
        - exp(?!assert)

- 对象属性

    - 正则对象的属性：只读
    - global是否全文搜索
    - ignore case是否大小写敏感
    - multiline多行搜索
    - lastIndex当前表达式匹配内容的最后一个字符的下一个位置
    - source正则表达式的文本字符串
- test 和 exec
    - reg.test("string")

        - 用来测试字符串中是否存在匹配正则表达式的字符串，返回true或者false

        - 每次test后，都会把lastIndex属性中的值作用与该正则表达式上。类似于指针的感觉。

        - 所以每次test的值都不一定相同
    - reg.exec("string")

        - 使用正则表达式模式对字符串进行搜索，并将更新全局RegExp对象的属性以反映匹配结果。

        - 返回null或结果数组

            - 数组有额外的属性：index声明匹配文本的第一个字符的位置；input存放被检索的字符串String

        - 非全局调用时，返回的数组：

            - 第一个元素：与正则表达式相匹配的文本

            - 第二个元素：与上一个子表达式匹配的文本
            - n……

- 正则小demo

```js
function reset(str){
    //my-name-is-lee 和 myNameIsLee之间互相转换
    if(-1<str.indexOf('-')){
        return str.replace(/-[a-z]/g,function(a){
            return a.toUpperCase().replace('-','')
        })
    }else{
        return str.replace(/[A-Z]/g,function(a){
            return '-'+a.toLowerCase()
        })
    }
} 
function getString(str){
    //返回字符串中数字的位置
    var reg=/[0-9]/g;
    var arr=[]
    let bool=true;
    while(bool){
        var value=reg.exec(str)
        bool=!!value
        if(bool){
            arr.push(value.index)
        }
    }
    return arr;
}
var email='/^(\w)+(\.\w+)*@(\w)+((\.\w{2,3}){1,3})$/'
var idcard='/^(\d{15}$|^\d{18}$|^\d{17}(\d|X|x))$/'
var phone='/^[134|135|136|137|138|139|147|150|151|152|157|158|159|172|178|182|183|184|187|188|130|131|132|145|155|156|171|175|176|185|186|133|149|153|173|177|180|181|189|179]\d{8}$/'
var cannull='/(^$)|\w+/'
console.log(getString('my 0 name is 2 ljw'));
```
### less基本语法
- 变量：

    - 变量声明：@color:#ffffff;

    - 变量使用：@color

    - 变量定义时可以使用其他变量：@a:"123" ;  @b:'a' ;  调用：@@b 返回123

    - 作用域：块级作用域，可以后声明。闭包：可以调用外部变量。

- 混合：（Minxins）

    - 抽象出通用属性为.public{}

    - 调用：.child{    .public       }

    - 注意：变量也会带到当前作用域

- 带参数混合：

    - 声明：
    ```less
    .border-radius(@radius){
        border-radius:@radius;
        -moz-border-radius:@radius;
        -webkit-border-radius:@radius;
    }
    ```
    - 使用：.border-radius(6px);

    - 带默认值的声明：
    ```less
    .border-radius(@radius：5px){
        border-radius:@radius;
        -moz-border-radius:@radius;
        -webkit-border-radius:@radius;
    }
    ```
    - 使用：.border-radius;

- 多参数混合

    - 声明：.name(1,2,3;red,blue)

    - 注：声明可以被重载。有多个同名声明被调用时， 会调用强制要求需要对应实参个数的声明。
- @arguments变量

    - 表示所有传递的参数，可以再混合声明表达式中使用
- @rest变量

    - 在混合中不限制参数的数量
- !important 关键字

    - 作用：用来筛选非IE浏览器

    - 使用方法：混合声明不变。混合调用时：.minxin(1) !important;

    - 会在每一个属性后添加！important

- 模式匹配

    - 作用：通过参数控制mixin行为

    - 声明：
    ```less
        .minx(dark,@color){
            color:darken(@color,10%)
        }
        .minx(light,@color){
            color:lighten(@color,10%)
        }
    ```
    ↓接收所有参数
    ```less
        .minx(@_,@color){
            display:block;
        }
    ```
    - 调用：
        ```less
            @switch:light;
            .class{
                .mixin(@switch,#888888) ;
            }
        ```
    - 得到：
        ```less
            .class{
                color:#a2a2a2;
                display:block;
            }
        ```
- Guards（when后面的表达式）

    - 作用：通过表达式（expressions）控制minx行为
    - ↓实例：判断color的亮度，大于50%时背景色为黑，小于时背景色为白色

    - 声明：
    ```less
        . mixin ( @ a ) when ( lightness ( @ a ) >= 50% ){
            background-color : black;
        }
        . mixin ( @ a ) when ( lightness ( @ a ) < 50% ){
            background-color : white ;
        }
        . mixin ( @ a ) {
            color:@a;
        }
    ```
    - 调用：
    ```less
        .class1{  .minx ( #ddd )  }
        .class2{  .minx ( #555 )  }
    ```
    - 得到：
    ```less
        .class1 {
            background-color : black;
            color:#ddd;
        }
        .class2 {
            background-color : white;
            color:#555;
        }
    ```
    - 注意：可以参数之间作比较。可以检查传入的参数类型。或者检查传入值（数字）的单位。

    - 用 , 分隔表示逻辑或，用and 表示逻辑与， 用not表示否定

- 嵌套

    - 用类似DOM结构的格式嵌套样式
    - &：可以用来表示到此为止的嵌套的样式
    - &可以用在后面，来嵌套外面的一层

- 函数
    - less有许多自定义的函数，可以用来处理颜色等等

- 命名空间

    - 作用：可以把混合封装起来，然后在调用时像调用对象的属性一样调用

    - 声明：
    ```less
        # bundle｛
        　. button ( ) {
                display : block ;
                border : 1px solid black;
                background - color : gery;
                &：hover { background-color : white  }
            }
            . tab {  ... }
            .citation { ... }
        }
    ```
    - 调用 ：
    ```less
        # header a{
            color :orange;
            #bundle > . button ;
        }
    ```
- 作用域：

    - 找不到的变量会向上查找

- 导入（Import）

    - 说明：可以导入css或者less，css 处理吧语句提前至@charset中。less处理：包含与被包含的文件共享所有的结构。

    - 使用：@improt "";

- 字符串差值

    - 说明：可以在字符串中插入变量

    - 使用：
    ```less
        @base-url : " http://localhost:8080 "
        background-imge : (  " @ { base-url }  /images / bg.png " )
    ```
- 避免编译
    - ~" 各种字符串 "

- 选择器插值

    - 说明：在选择器中使用less变量

    - 使用：
    ```less
        @name：blocked；
        . @ { name }{
            color : black ;
        }
    ```
- JavaScript求值

    - 使用：
在less中使用   `   来使用JavaScript  `
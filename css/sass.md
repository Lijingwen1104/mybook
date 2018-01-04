### sass基本语法

- 导入
    - @improt "a.scss" 导入后会将scss文件合并成一个css文件。导入可以忽略后缀名。_开头的文件可以不写下划线。

    - 如果导入css样式，不会编译，而是@import形式存在

- 注释
    - //单行注释不输入到css
    - /**/
    - /*! 重要注释不会在压缩时被删除*/

- 变量

    - 声明变量， 可以再全局范围内使用。
        - $a:1;

    - 声明带默认值的变量，覆盖方法在默认值之前重新声明
        - $a:1 !default;

    - 普通变量引用
        - $a;

    - 在用于属性值或者字符串中的变量引用时
        - #{$a}

    - 多值变量list

        - 声明：$px: 5px 10px 20px 30px;

        - 使用：$px;

        - 函数：取值nth($px,$2)。更多函数http://sass-lang.com/documentation/Sass/Script/Functions.html搜索 list function

    - 多值变量map

        - 声明：$map:{key1:value1,key2:value2}

        - 使用：map-get($map ,$key)取值

        - 遍历：@each $k,$v in $map{
    $k;p
    $v;
}

    - 全局变量

        - 声明$a:1 !global;

- 嵌套

    - 选择器嵌套：&表示父级

    - 属性嵌套:表示border-left这样的属性（然而并没什么卵用）
        - border:{
  left:{
  }
  right:{
  }
}

    - 跳出嵌套 @at-root

        - 跳出普通嵌套，变成父级平级
.parent{
    @at-root .child{
    }
    @at-root{
        .child1{
        }
        .child2{
        }
    }
}

        - 跳出@media嵌套不跳出父级
@media print{
    @at-root(without:media){
        .child{
        }
    }
}

        - 跳出@media嵌套和父级
@media print{
    @at-root(without:all){
        .child{
        }
    }
}

        - 利用&在子元素中嵌套父元素
.child{
    @at-root .parent &{


    }
}

        - 应用于keyframes
.parent{
    @at-root{
        @keyframes notion{
         }
    }
}

- 混合 @mixin

    - 声明：
    - @mixin name($a:1){
}

    - 使用：
@include name(2);

    - 可以有多个参数，参数可有默认值

    - 多组值混合：（如box-shadow等可以有多个参数）
声明 @minx name($a...){
}

    - @conten
        - conten可以接收一块样式，用来适应CSS中的@media

        - 定义：
@mixin max-screen($res){
  @media only screen and ( max-width: $res ) {
      @content;
  }
}
@include max-screen(480px) {
    body {
       color: red;
    }
}

        - 生成：
@media only screen and (max-width: 480px) {
    body { color: red }
}

- 继承：

    - 选择器继承
        - a{}
        - .b{@extend a ;}

    - 选择占位器%

        - 不调用不产生多余css文件，被调用的a不会被编译

        - 声明：
%a{
}

        - 调用：
b{
    @extend %a;
}

- 函数http://sass-lang.com/documentation/Sass/Script/Functions.html

- 运算 运算符前后留空格

- 条件判断及循环
    - @if判断
        - @if $a==200px

    - 三目判断

        - 输出最大值 if($a>$2,$a,$b)
    - @for 循环
        - @for $i from 1 through
   .item-#{$i} { width: 2em * $i; }
}包括最后一个
        - @for $i from 1 to 3{
   .item-#{$i} { width: 2em * $i; }
}不包括最后一个
    - @each遍历

        - 单个字段list数据循环
            - @each $val in $list {
   $val;
}

        - 多个字段list数据循环
            - $list :(1,2,4),(2,3,4)；
@each $a $b $c in $list {
     $a ;$b;$c;
}

        - 多个字段map数据循环
            - $map:{key1:value1,key2:value2,key3:value3};
@each $key,$value in $map{
    $key;$value;
}
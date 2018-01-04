### css3

#### @keframes 动画
- @keyframes mykef{

               from{   }
               to{  }
               或者是
               0%{   }
               20%{    }
          }

- 可以用来 过渡css样式

- 需要在该元素的样式中添加animation:mykef 5s;用来绑定函数

- 在元素样式中添加：
animation-fill-mode:forwards;元素保持动画最后的样子。

#### transform 2D 旋转

- transform:translate(50px,100px)

    - 元素从本来的位置从位移，相当于设置left  和 top
- transform:rotate(30deg)

    - 顺时针旋转，负值为逆时针旋转

    - 单位为度
- transform:scale(2,4)

    - 根据元素的高度放大宽，高倍数
- transform:skew(45deg,45deg)

    - 参数一：围绕x轴旋转。实现效果：宽不动，高逆时针旋转。

    - 参数二：围绕y轴旋转。实现效果：高不动，宽顺时针旋转。

#### Transition 过度
- transtion:width 2s，height 2s。

    - 用来过渡长和宽的变化。

    - 可以结合 div:hover设置不同的长度，transtion 要写在div 的样式中
    - http://www.w3school.com.cn/tiy/t.asp?f=css3_transition2

#### Transform:3D旋转

- transform:rotateX(120deg)

    - 围绕其 X 轴以给定的度数进行顺时针旋转。
- transform:rotateY(120deg)

    - 围绕其Y轴以给定的度数旋转。
- transform:ratateZ（120deg）

    - 围绕其Z轴以给定的度数旋转，相当于2D旋转。


### 容易混淆的字符串、数组方法

####  splice slice split 


1. splice( start, num, ...[newArray] )

    ```js
    var arr = [1,2,3,4]

    arr.splice(1,1, ...[5,6,7]) // [2]

    arr // [1,5,6,7,3,4]

    ```

2. slice( start, end )

    ```js
    var arr = [1,2,3,4]

    arr.slice(1,2) // [2]

    arr.slice(-2) // [3,4]

    arr.slice(1) // [2,3,4]

    arr // [1,2,3,4]

    ```

3. split( str, num )

    ```js
    var str = "1,2,3,4"

    str.split(",") // [1,2,3,4]

    str.split(",", 2) // [1,2]
    ```
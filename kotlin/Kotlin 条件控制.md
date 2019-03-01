## 1，IF 表达式
一个 if 语句包含一个布尔表达式和一条或多条语句。
``` kotlin
// 传统用法
var max = a 
if (a < b) max = b

// 使用 else 
var max: Int
if (a > b) {
    max = a
} else {
    max = b
}
 
// 作为表达式
val max = if (a > b) a else b
```
我们也可以把 IF 表达式的结果赋值给一个变量。
``` kotlin
val max = if (a > b) {
    print("Choose a")
    a
} else {
    print("Choose b")
    b
}
```
这也说明我也不需要像Java那种有一个三元操作符，因为我们可以使用它来简单实现：
``` kotlin
val c = if (condition) a else b
```
- 使用区间
使用 in 运算符来检测某个数字是否在指定区间内，区间格式为 x..y ：
``` kotlin
fun main(args: Array<String>) {
    val x = 5
    val y = 9
    if (x in 1..8) {
        println("x 在区间内")
    }
}
//输出结果为：
//x 在区间内
```

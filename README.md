> [Google正式支持Kotlin啦~](https://blog.jetbrains.com/kotlin/2017/05/kotlin-on-android-now-official/)
>
> Java 8推广不及预期，Java 9争议颇多，来试试Kotlin吧!

[![Maintenance](https://img.shields.io/badge/Maintained%3F-no-red.svg)](https://bitbucket.org/lbesson/ansi-colors)

# Kotlin语法一览

## Hello world

```kotlin
// 最简版
fun main(args: Array<String>) {
  println("Hello, world!")
}
```

```kotlin
// 面向对象版
class Greeter(val name: String) {
  fun greet() {
    println("Hello, $name")
  }
}

fun main(args: Array<String>) {
  Greeter(args[0]).greet()
}
```

## 可变和不可变类型

```kotlin
// var的内容来自变量。它可以随时改变。
var answer = 12
answer = 13 // 编译通过
```

```kotlin
// val的内容来自值。初始化之后不能改变。
val age = 18
age = 19 // 编译错误
```

## 可为空类型

```kotlin
var a: String? = "abc"
a = null // 编译通过

var b: String = "abc"
b = null // 编译错误
```

## 数据类型
```kotlin
// 整数类型
val answer: Int = 42
// 1.1版本开始支持类似swift的下划线分隔
val oneMillion = 1_000_000

// 浮点类型
val yearsToCompute = 7.5e6

// 字符类型
val question = "The Ultimate Question of Life, the Universe, and Everything"
```

## 输入输出

```kotlin
// 字符串模板
val $name = 'world'
println("Hello, $name!")
```

```kotlin
// 大括号内可以是kotlin表达式
fun main(args: Array<String>) {
  if (args.size > 0) {
    println("Hello, ${args[0]}!")
  }
  
  println("Hello, ${if (args.size > 0) args[0] else "someone"}!")
}
```


## 函数
```kotlin
// 常规定义
fun max(a: Int, b: Int): Int {
  return if (a > b) a else b
}
```

```kotlin
// 把函数当成表达式
fun max(a: Int, b: Int): Int = if (a > b) a else b
```

```kotlin
// 使用命名参数
fun <T> joinToString(
  collection: Collection<T>,
  separator: String,
  prefix: String,
  postfix: String
): String {
  val result = StringBuilder(prefix)
  
  for ((index, element) in collection.withIndex()) {
    if (index > 0) result.append(separator)
    result.append(element)
  }
  
  result.append(postfix)
  return result.toString()
}

joinToString(collection, separator = " ", prefix = " ", postfix = ".")
```

```kotlin
// 使用参数默认值（实现类似于重载的功能）
>>> val list = listOf(1, 2, 3)
>>> println(list)
[1, 2, 3]

fun <T> joinToString(
  collection: Collection<T>,
  separator: String = ", ",
  prefix: String = "",
  postfix: String = ""
): String {
  val result = StringBuilder(prefix)
  
  for ((index, element) in collection.withIndex()) {
    if (index > 0) result.append(separator)
    result.append(element)
  }
  
  result.append(postfix)
  return result.toString()
}

>>> joinToString(list, ", ", "", "")
1, 2, 3
>>> joinToString(list)
1, 2, 3
>>> joinToString(list, "; ")
1; 2; 3
```

## 扩展函数
*扩展函数是定义在类外部，但却能够以类的成员函数的方式进行调用的函数。*
```kotlin
package strings

fun String.lastChar(): Char = this.get(this.length - 1)
```

## 控制结构

## 类
```kotlin
// 定义一个类
class Person(val name: String)

// 定义类属性
class Person(
  val name: String,
  var isMarried: Boolean
)

// 定义类方法
class Person(
  val name: String,
  var isMarried: Boolean
) {
  fun sayHello() {
    println("hello $name")
  }
}

// 创建类实例
>>> val person = Person("Bob", true)
>>> println(person.name)
Bob
>>> person.sayHello()
hello BOb
```

## 类的访问修饰符
|修饰符 | 对应的成员 | 备注 |
|-------|-----------|-----|
| `final` | 不能被覆盖 | 类成员的默认修饰符 |
| `open`  | 可以被覆盖 | 必须显式的指定 |
| `abstract` |必须被覆盖| 只能在抽象类中使用，抽象成员不能有实现 |
| `override` | 在一个子类中覆盖一个成员 | 如果没有被标记为`final`，覆盖的成员默认是开放的。 |

## 类的可见性修饰符

|修饰符 | 对应的成员 | 顶层声明 |
|-------|-----------|-----|
| `public(默认可见性)` | 所有地方可见 | 所有地方可见 |
| `internal` | 模块内可见 | 模块内可见 |
| `protected` | 子类内部可见 | 不可见 |
| `private` | 类内部可见 | 在文件中可见 |

## 枚举类
```kotlin
enum class Color {
  RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET
}
```

## 接口

```kotlin
// 定义接口
interface Clickable {
  fun click()
  fun showOff() = println("I'm clickable!") // 接口可以有默认的实现
}

// 实现接口
class Button : Clickable {
  override fun click() = println("I was clicked")
}

```

## 对象声明
```kotlin
// 定义对象
object Payroll {
  val allEmployees = arrayListOf<Person>()
  
  fun calculateSalary() {
    for (person in allEmployees) {
      ...
    }
  }
}

// 使用对象
Payroll.allEmployees.add(Person(...))
Payroll.calculateSalary()
```

## 伴生对象
```kotlin
// 定义伴生对象
class A {
  companion object {
    fun bar() {
      println("Companion object called")
    }
  }
}

// 调用伴生对象
>>> A.bar()
Companion object called
```
## Lambda表达式
```kotlin
>>> val sum = { x: Int, y: Int -> x + y } // 定义lambda表达式
>>> println(sum(1, 2))
3
```
![lambda syntax](https://panxl6.gitbooks.io/kotlin-in-action-in-chinese/content/assets/5.1.jpg)

## 类型系统

## 操作符重载

## 标注

## 反射

## 泛型

## traits

## 集合

## 异常处理

```kotlin
fun readNumber(reader: BufferedReader): Int? {
  try {
    val line = reader.readLine()
    return Integer.parseInt(line)
  }
  catch (e: NumberFormatException) {
    return null
  }
  finally {
    reader.close()
  }
}
```

## 文件操作

## 函数式支持

*如果你对函数式编程不是特别了解，可以看一看[《函数式编程思维》](https://www.amazon.cn/%E5%9B%BE%E4%B9%A6/dp/B014SCOQA0)*

**filter**
```kotlin
>>> val list = listOf(1, 2, 3, 4)
>>> list.filter { it % 2 == 0 }
[2, 4]
```

![图5.3](http://osimdjby7.bkt.clouddn.com/5.3.png)


**map**
```kotlin
>>> val list = listOf(1, 2, 3, 4)
>>> list.map { it * it }
[1, 4, 9, 16]
```

![图5.4](http://osimdjby7.bkt.clouddn.com/5.4.png)

**all**
```kotlin
val canBeInClub27 = { p: Person -> p.age <= 27 }

>>> val people = listOf(Person("Alice", 27), Person("Bob", 31))
>>> println(people.all(canBeInClub27))
false
```

**any**
```kotlin
val canBeInClub27 = { p: Person -> p.age <= 27 }

>>> val people = listOf(Person("Alice", 27), Person("Bob", 31))
>>> println(people.any(canBeInClub27))
true
```

**count**
```kotlin
>>> val people = listOf(Person("Alice", 27), Person("Bob", 31))
>>> println(people.count(canBeInClub27))
1
```

**find**
```kotlin
>>> val people = listOf(Person("Alice", 27), Person("Bob", 31))
>>> println(people.find(canBeInClub27))
Person(name=Alice, age=27)
```

## 领域特定语言

## 常用函数

## IDE快捷键


# Kotlin-in-action中文翻译

更方便的阅读模式请移步[gitbook项目](https://www.gitbook.com/book/panxl6/kotlin-in-action-in-chinese)


---
## 相关资源：

1. [Awesom-kotlin](https://github.com/mcxiaoke/awesome-kotlin)
2. [Belarus Kotlin User Group](https://github.com/KotlinBy/awesome-kotlin)
3. [Programming in kotlin电子书](http://download.csdn.net/download/u011433684/9743120)

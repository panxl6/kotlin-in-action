# Kotlin语法一览

## Hello world

```
fun main(args: Array<String>) {
  println("Hello, world!")
}
```

## 可变和不可变类型
`var`的内容来自变量。它可以随时改变。
```
var answer = 12
answer = 13 // 编译通过
```

`val`的内容来自值。初始化之后不能改变。
```
val age = 18
age = 19 // 编译错误
```

## 可为空类型

## 数据类型

整数类型：`val answer: Int = 42`

浮点类型：`val yearsToCompute = 7.5e6`

字符类型: `val question =
"The Ultimate Question of Life, the Universe, and Everything"`

## 输入输出
字符串模板
```
val $name = 'world'
println("Hello, $name!")
```

大括号内可以是kotlin表达式
```
fun main(args: Array<String>) {
  if (args.size > 0) {
    println("Hello, ${args[0]}!")
  }
  
  println("Hello, ${if (args.size > 0) args[0] else "someone"}!")
}
```


## 函数
```
fun max(a: Int, b: Int): Int {
  return if (a > b) a else b
}
```

`fun max(a: Int, b: Int): Int = if (a > b) a else b`

## 控制结构

## 类

## 接口

## traits

## 扩展函数

## 集合

## 异常处理
```
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

## 领域特定语言

## 函数式支持

## 枚举类
```
enum class Color {
  RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET
}
```

## 常用函数

## IDE快捷键


# Kotlin-in-action

Kotlin in action 一书的中文翻译

更方便的阅读模式请移步[gitbook项目](https://www.gitbook.com/book/panxl6/kotlin-in-action-in-chinese)

ebook目录下是原文原版电子书和书中源码

亲，如果你觉得这个项目不错，请为我star一下~

ebook store in `ebook` directory, download or star is welcomed


---
## 相关资源：

1. [Awesom-kotlin](https://github.com/mcxiaoke/awesome-kotlin)
2. [Belarus Kotlin User Group](https://github.com/KotlinBy/awesome-kotlin)
3. [Programming in kotlin电子书](http://download.csdn.net/download/u011433684/9743120)

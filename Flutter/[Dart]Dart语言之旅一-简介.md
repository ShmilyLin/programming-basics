# [Dart]Dart语言之旅<一>：简介

我们假定你已经知道如何用另一种语言编程，《Dart语言之旅》将向你展示了如何使用每个主要的Dart特性——从变量和运算符到类和库。

要了解有关Dart核心库的更多信息，请参阅[Dart图书馆之旅](https://www.dartlang.org/guides/libraries/library-tour)。

> **提示：** 你可以使用DartPad运行这些功能中的绝大部分（[了解更多](https://www.dartlang.org/tools/dartpad)）。
> 
> [打开DartPad](https://dartpad.dartlang.org/)

无论何时，只要你想了解有关Dart语言的更多详细信息，请参阅[Dart语言规范](https://www.dartlang.org/guides/language/spec)。

## 一个基本的Dart程序

下面的代码使用了许多Dart最基本的功能：

```dart
// Define a function.
printNumber(num aNumber) {
  print('The number is $aNumber.'); // Print to console.
}

// This is where the app starts executing.
main() {
  var number = 42; // Declare and initialize a variable.
  printNumber(number); // Call a function.
}
```

以下是适用于所有（或者说是几乎所有）的Dart应用程序的语法：

* **// This is a comment.**

  使用`//`表示改行的后面部分是注释。或者也可以使用`/* ... */`。更多详细内容，请看[注释](#)

* **num**

  一种内置类型，其他的内置类型是String，int和bool。

* **42**

  数字。数字在编译时是常量。

* **print()**

  一个方便的输出显示方式。

* **`'...'` (或 `"..."`)**

  字符串。

* **_\$variableName_ (或 _${expression}_)**

  字符串插值：在字符串中包含一个变量或表达式的字符串。有关更多信息，请参阅[字符串](#)。

* **main()**

  应用程序执行的开始，是一个特殊的，必需的顶级函数。有关更多信息，请参阅[main()函数](#)。

* **var**

  一种不指定类型的声明变量的方法。
  
> **注意：** 我们的代码遵循[Dart风格指南](https://www.dartlang.org/guides/language/effective-dart/style)中的约定。例如，我们使用双空格缩进。

## 重要概念

当你学习Dart语言时，记住这些事实和概念：

* 你可以放在变量中的所有东西都是一个 _object_，每个对象都是一个 _class_ 的实例。偶数，函数和`null`都是对象。所有对象都继承自[Object](https://api.dartlang.org/stable/dart-core/Object-class.html)类。

* 指定静态类型（例如前面示例中的`num`）可以阐明你的意图并启用静态工具检查。 （你可能会注意到当你调试代码时，没有指定类型的变量会获得特殊类型：`dynamic`。）在Dart 1.x中指定静态类型是可选的，但是Dart正朝着类型安全的语言发展。

* 在强模式（strong mode）下，静态和运行时会检查确保你的代码是类型安全的，帮助你在开发中而不是运行时就捕获错误。在Dart 1.x中强模式是可选的，但在Dart 2中不可选。

* 在运行之前，Dart会解析所有的代码。你可以向Dart提供提示（例如，通过使用类型或编译时常量）来捕获错误或使你的代码更快地运行。

* Dart支持顶级函数（如`main()`），以及与类或对象绑定的函数（分别为 _static_ 和 _instance_ 方法）。你也可以在函数中创建函数（_嵌套函数_或_局部函数_）。

* 同样，Dart支持顶级变量以及绑定到类或对象（静态变量和实例变量）的变量。实例变量有时称为字段或属性。

* 与Java不同，Dart没有`public`，`protected`和`private`关键字。如果标识符以下划线（_）开头，则它是私有的。有关详细信息，请参阅[库和可见性](https://www.dartlang.org/guides/language/language-tour#libraries-and-visibility)。

* 标识符可以以字母或_开头，然后是这些字符和数字的任意组合。

* 有时候重要的是某件事是一种_表达（expression）_还是一种_陈述（statement）_，所以我们会对这两个词做精确的描述。

* Dart工具可以报告两种问题：警告和错误。警告只是表明你的代码可能无法正常工作，但它们不会阻止你的程序执行。错误可以是编译时错误或运行时错误：编译时错误导致代码无法执行，运行时错误导致代码执行时引发异常。

* Dart 1.x有两种运行模式：生产和检查。我们建议你在检查模式下开发和调试，然后在生产模式部署。生产模式是Dart程序的默认运行模式，它针对速度进行了优化。生产模式会忽略断言语句和静态类型。检查模式是一种开发友好模式，可帮助你在运行时捕获某些类型的错误。例如，如果你将一个非数字变量传入一个`num`类型的值，则检查模式会抛出一个异常。

> **Dart 2的提示：** Dart 2中移除了检查模式。更多信息请看[Dart 2升级](https://www.dartlang.org/dart-2)。

### 关键字

下表列出了Dart语言会特别处理的词语。

| | | | |
|:---:|:---:|:---:|:---:|
| abstract<sup>1</sup> | deferred<sup>1</sup> | if | super |
| as<sup>1</sup> | do | implements<sup>1</sup> | switch |
| assert | dynamic<sup>1</sup> | import<sup>1</sup> | sync*<sup>2</sup> |
| async<sup>2</sup> | else | in | this |
| async*<sup>2</sup> | enum | is | throw |
| await<sup>2</sup> | export<sup>1</sup> | library<sup>1</sup> | true |
| break | external<sup>1</sup> | new | try |
| case | extends | null | typedef<sup>1</sup> |
| catch | factory<sup>1</sup> | operator<sup>1</sup> | var |
| class | false | part<sup>1</sup> | void |
| const | final | rethrow | while |
| continue | finally | return | with |
| covariant<sup>1</sup> | for | set<sup>1</sup> | yield<sup>2</sup> |
| default | get<sup>1</sup> | static<sup>1</sup> | yield*<sup>2</sup> |

<sup>1</sup> 带上标 **1** 的单词是**内置标识符**。避免使用内置标识符作为你自己的自定义标识符。如果你尝试为类或类型名称使用内置标识符，则会发生编译时错误。

<sup>2</sup> 带有上标 **2** 的单词是Dart 1.0版本之后添加的与异步支持相关的更新，有限的保留字。你不能使用`async`，`await`或`yield`作为你自己的自定义标识符，也不能在任何函数体中使用`async`，`async *`或`sync *`标记。有关更多信息，请参见[异步支持](https://www.dartlang.org/guides/language/language-tour#asynchrony-support)。

关键字表中的所有其他字都是保留字。你不能使用保留字作为标识符。

--- 

NEXT

[[Dart]Dart语言之旅<二>：变量](https://juejin.im/post/5aa2655b6fb9a028d566b605)

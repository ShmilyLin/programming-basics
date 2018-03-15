# [Flutter]编写你的第一个Flutter应用

这是创建你的第一个Flutter应用程序的指南。如果你熟悉面向对象的代码和基本编程概念（如变量，循环和条件），则可以开始学习本教程。你不需要有使用过Dart或移动编程的经验。

### 你会创建什么

你将创建一个为创业公司生成名称建议的简单的移动应用程序。用户可以选择和取消选择名称，并且可以保存他看中的最好的名称。代码会一次生成十个名称。用户滚动列表时，会成批的生成新的名称。用户可以点击应用栏右上方的列表图标查看收藏过的名称。

动画GIF显示完成的应用程序的工作方式。

![](https://flutter.io/get-started/codelab/images/startup-namer-app.gif)

> **你将学会：**
>
> * Flutter应用程序的基本结构。
> * 查找和使用包来扩展功能。
> * 使用热重载加快开发周期。
> * 如何实现有状态的组件。
> * 如何创建一个无限的，延迟加载的列表。
> * 如何创建并导航到第二个屏幕。
> * 如何使用主题更改应用程序的外观。


> **你将会用到：**
> 
> 你需要安装以下内容：
>
> * Flutter SDK
>
>   Flutter SDK包括Flutter的引擎、框架、组件、工具和Dart SDK。 这个代码库需要v0.1.4或更高版本。
>
> * Android Studio IDE
>   
>   该代码库包含有Android Studio IDE，但你也可以使用其他IDE，或者从命令行直接运行。
>
> * 你的IDE的插件
>
>   必须为您的IDE单独安装Flutter和Dart插件。除了Android Studio之外，Flutter和Dart插件也可用于VS Code和IntelliJ IDE。
>
> 关于如何配置你的开发环境，请查看[Flutter的安装和配置](https://juejin.im/post/5a96661ff265da4e7a788905)。


## 第一步：创建并运行Flutter应用程序

参考[开始运行你的第一个Flutte应用程序](https://flutter.io/get-started/test-drive/#create-app)来创建一个简单的模板化Flutter应用程序。项目名称为**startup_namer**（代替文章中的`myapp`）。你将通过修改这个应用来完成最终的应用程序。

在这个代码库中，你将主要修改Dart代码所在的`lib/main.dart`文件。

> **提示：**将代码复制粘贴到应用程序中时，缩进可能会变形。 您可以使用Flutter工具自动修复此问题：
>
> * Android Studio / IntelliJ IDEA：右键单击dart代码，然后选择**Reformat Code with dartfmt**。
> * VS Code：右键单击dart代码，然后选择**Format Document**。
> * Terminal：运行`flutter format <文件名称>`。

1. 替换`lib/main.dart`。
   删除`lib/main.dar`文件中的所有代码。使用下面的代码替换，然后将会在屏幕中间显示“Hello World”。
```dart
import 'package:flutter/material.dart';

void main() => runApp(new MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new MaterialApp(
      title: 'Welcome to Flutter',
      home: new Scaffold(
        appBar: new AppBar(
          title: new Text('Welcome to Flutter'),
        ),
        body: new Center(
          child: new Text('Hello World'),
        ),
      ),
    );
  }
}
```

2. 运行应用，你将会看到如下内容。

![Hello World](https://user-gold-cdn.xitu.io/2018/3/7/161fe9c9a33f15af?w=350&h=689&f=png&s=33704)

### 注意

* 本示例创建一个Material应用程序。 [Material](https://material.io/guidelines/)是一种视觉设计语言，在移动设备和网络上保持一个标准。Flutter提供了一套丰富的Material小部件。
* main方法指定使用箭头函数（`=>`）表示法，它是用于单行函数或方法的简写。
* 该应用程序扩展了使应用程序本身成为组件的StatelessWidget。在Flutter中，大多数情况下看到的都是一个个组件，包括对齐，填充和布局。
* Material库中的Scaffold组件提供了默认应用程序栏、标题和包含主屏幕组件树的body属性。组件子树可能会相当复杂。
* Widget的主要工作是提供一个`build()`方法，该方法描述如何根据其他较低级别的组件来显示这个Widget。
* 此示例的组件树由包含Text组件的Center组件组成。Center组件的作用是将其组件子树对齐到屏幕中心。

## 第二步：使用第三方库

在这一步中，你将开始使用一个开源的叫做**english_words**的第三方库，它包含了数千个最常用的英文单词以及一些实用功能。

你可以在[pub.dartlang.org](https://pub.dartlang.org/flutter/)上像找到其他第三方开源库一样轻松的找到这个**english_words**库。

1. pubspec文件管理一个Flutter应用成语的资源。在`pubspec.yaml`文件中，给dependencies列表中添加**english_words**（3.1.0或更高版本），如下所示：
```yaml
dependencies:
  flutter:
    sdk: flutter

  cupertino_icons: ^0.1.0
  english_words: ^3.1.0
```
2. 在Android Studio编辑器视图中查看pubspec时，单击右上角的**Packages get**。将该包拉入您的项目，您应该在控制台中看到以下内容：
```
flutter packages get
Running "flutter packages get" in startup_namer...
Process finished with exit code 0
```
3. 在`lib/main.dart`文件中，添加关联**english_words**，如下所示：
```dart
import 'package:flutter/material.dart';
import 'package:english_words/english_words.dart';
```
在你输入时，Android Studio会为你提供有关库导入的建议。输入完成后它将你刚才输入的导入字符串呈现为灰色，以便让你知道导入的库尚未使用（到目前为止）。

4. 使用英文单词库生成的文本替代之前的字符串“Hello World”。
> **提示：**“Pascal case”（即“驼峰命名法”）的意思是字符串中的每个单词（包括第一个单词）都以大写字母开头。所以，“uppercamelcase”变成“UpperCamelCase”。

改动后，代码如下所示：
```dart
import 'package:flutter/material.dart';
import 'package:english_words/english_words.dart';

void main() => runApp(new MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final wordPair = new WordPair.random();
    return new MaterialApp(
      title: 'Welcome to Flutter',
      home: new Scaffold(
        appBar: new AppBar(
          title: new Text('Welcome to Flutter'),
        ),
        body: new Center(
          //child: new Text('Hello World'), // Replace the highlighted text...
          child: new Text(wordPair.asPascalCase),  // With this highlighted text.
        ),
      ),
    );
  }
}
```

5. 如果应用程序正在运行，请使用热重载按钮（闪电图标）更新正在运行的应用程序。每次单击热重载或保存项目时，你都会在正在运行的应用程序中看到随机选择的一个不同的单词。这是因为这个单词是在build方法内部生成的，每次MaterialApp需要渲染时或者在Flutter Inspector中切换平台时都会运行。

![](https://user-gold-cdn.xitu.io/2018/3/7/161feb99622bdb85?w=350&h=688&f=png&s=33038)

### 有问题？

如果您的应用程序没有正常运行，请查找错别字。如果需要，请使用以下链接中的代码重新开始。

* [**pubspec.yaml**](https://gist.githubusercontent.com/Sfshaza/bb51e3b7df4ebbf3dfd02a4a38db2655/raw/57c25b976ec34d56591cb898a3df0b320e903b99/pubspec.yaml)（**pubspec.yaml**文件不会再更改。）
* [**lib/main.dart**](https://gist.githubusercontent.com/Sfshaza/bb51e3b7df4ebbf3dfd02a4a38db2655/raw/57c25b976ec34d56591cb898a3df0b320e903b99/main.dart)


## 第三步：添加一个状态组件

无状态的组件是不可改变的，这意味着它们的属性不能改变——所有的值都是最终的。

有状态的组件会保持状态，这个状态在组件的生命周期中可能会改变。实现一个有状态的组件至少需要两个类：1）一个StatefulWidget类，它创建一个2）一个State类的实例。 StatefulWidget类本身是不可变的，但State类在整个构件的生命周期中保持不变。

Stateful widgets maintain state that might change during the lifetime of the widget. Implementing a stateful widget requires at least two classes: 1) a StatefulWidget class that creates an instance of 2) a State class. The StatefulWidget class is, itself, immutable, but the State class persists over the lifetime of the widget.

在这一步中，你将添加一个有状态的组件RandomWords，它创建它的State类——RandomWordsState。State类将最终维护组件的建议和最喜欢的单词对。

In this step, you’ll add a stateful widget, RandomWords, which creates its State class, RandomWordsState. The State class will eventually maintain the proposed and favorite word pairs for the widget.

1. 将有状态的RandomWords组件添加到`main.dart`。它可以在MyApp之外的文件中的任何位置使用，但最好将它放在文件的底部。RandomWords组件除了创建State类之外几乎没有其他任何作用：
```dart
class RandomWords extends StatefulWidget {
  @override
  createState() => new RandomWordsState();
}
```
2. 添加RandomWordsState类。应用程序的大部分代码都会放在该类中，该类保持RandomWords组件的状态。这个类将保存随着用户滚动而无限增长生成的单词对，以及用户最喜欢的单词对，用户通过切换心形图标来将它们从列表中添加或删除。

你会一步一步地建立这个类。首先，通过下面的文本创建一个最基础的mini类：
```dart
class RandomWordsState extends State<RandomWords> {
}
```
3. 在添加State类后，IDE会抱怨该类缺少构建方法。接下来，你将添加一个基本构建方法，该方法将单词生成代码从MyApp移动到RandomWordsState中来生成单词对。

将构建方法添加到RandomWordState中，如下面的文本所示：
```dart
class RandomWordsState extends State<RandomWords> {
  @override
  Widget build(BuildContext context) {
    final wordPair = new WordPair.random();
    return new Text(wordPair.asPascalCase);
  }
}
```
4. 按照下面的方式从MyApp中删除单词生成代码：
```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final wordPair = new WordPair.random();  // 删除这一行

    return new MaterialApp(
      title: 'Welcome to Flutter',
      home: new Scaffold(
        appBar: new AppBar(
          title: new Text('Welcome to Flutter'),
       ),
        body: new Center(
          //child: new Text(wordPair.asPascalCase), // 将这一行代码变为下一行
          child: new RandomWords(),
        ),
      ),
    );
  }
}
```
重新启动应用程序。如果你尝试使用热重载，则可能会看到警告：
```
Reloading...
Not all changed program elements ran during view reassembly; consider
restarting.
```
这可能是误报，但为了确保您的更改反映在应用的用户界面中，还是请重新启动应用。

应用程序应该像以前一样运行，每次热重载或保存应用程序时都会显示一个单词对。

![](https://user-gold-cdn.xitu.io/2018/3/7/161fecdfb4e9c51e?w=350&h=688&f=png&s=33207)

### 有问题？

如果您的应用程序没有正常运行，请使用以下链接中的代码重新开始。

* [**lib/main.dart**](https://gist.githubusercontent.com/Sfshaza/d7f13ddd8888556232476be8578efe40/raw/329c397b97309ce99f834bf70ebb90778baa5cfe/main.dart)

## 第四步：创建一个无限滚动ListView

在这一步中，你将扩展RandomWordsState以生成并显示单词对列表。当用户滚动时，ListView组件中显示的列表将无限增长。ListView的构造器的工厂构造函数允许你根据需要懒加载列表视图。

1. 将一个\_suggestions列表添加到RandomWordsState类用以保存建议的单词对。 该变量以下划线（_）开头——在第一个字符前加上一个带有下划线的标识符，在Dart语言中是强调私有。

另外，添加一个`biggerFont`变量来使字体变大。

```dart
class RandomWordsState extends State<RandomWords> {
  final _suggestions = <WordPair>[];

  final _biggerFont = const TextStyle(fontSize: 18.0);
  ...
}
```

2. 将一个_buildSuggestions()函数添加到RandomWordsState类。此方法创建ListView，并显示单词对。

ListView类提供了一个构建器属性——`itemBuilder`，一个指定为匿名函数作为回调函数的工厂构建器。传递给函数两个参数——`BuildContext`和行迭代器`i`。迭代器从0开始，每调用一次函数就会增加一次，对于每个单词对都会执行一次。该模型允许列表在用户滚动时无限增长。

按照下面的内容写：

```dart
class RandomWordsState extends State<RandomWords> {
  ...
  Widget _buildSuggestions() {
    return new ListView.builder(
      padding: const EdgeInsets.all(16.0),
      // The itemBuilder callback is called once per suggested word pairing,
      // and places each suggestion into a ListTile row.
      // For even rows, the function adds a ListTile row for the word pairing.
      // For odd rows, the function adds a Divider widget to visually
      // separate the entries. Note that the divider may be difficult
      // to see on smaller devices.
      itemBuilder: (context, i) {
        // Add a one-pixel-high divider widget before each row in theListView.
        if (i.isOdd) return new Divider();

        // The syntax "i ~/ 2" divides i by 2 and returns an integer result.
        // For example: 1, 2, 3, 4, 5 becomes 0, 1, 1, 2, 2.
        // This calculates the actual number of word pairings in the ListView,
        // minus the divider widgets.
        final index = i ~/ 2;
        // If you've reached the end of the available word pairings...
        if (index >= _suggestions.length) {
          // ...then generate 10 more and add them to the suggestions list.
          _suggestions.addAll(generateWordPairs().take(10));
        }
        return _buildRow(_suggestions[index]);
      }
    );
  }
}
```
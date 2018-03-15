# [Flutter]启动：调试运行

本页介绍如何“调试运行”Flutter：从我们提供的模板创建一个新的Flutter应用程序，运行它，并学习如何使用Hot Reload（热重载）进行更改。

Flutter是一个灵活的工具包，所以请首先选择您的开发工具来编写，构建和运行您的Flutter应用程序。

---
## Android Studio 

**Android Studio**：为Flutter提供完整的集成IDE体验。

### 创建新的应用程序

1. 选择**File > New Flutter Project**
2. 选择**Flutter application**作为项目类型，然后选择下一步
3. 输入项目名称（如：`myapp`），然后选择下一步
4. 点击**Finish**
5. 等待Android Studio安装SDK，并创建项目工程。

上述命令创建了一个名为`myapp`的Flutter项目目录，其中包含一个使用[Material Components](https://material.io/guidelines/)的简单应用程序示例。

在项目目录中，你的应用程序的代码在`lib/main.dart`下。

### 运行应用程序

1. 找到主要的Android Studio工具栏：

![Android Studio工具栏](https://flutter.io/images/intellij/main-toolbar.png)

2. 在**target selector**中选择一个Android设备来运行应用程序。如果没有列出可用的，可以在**Tools>Android>AVD Manager**中创建一个。更多信息，查看[管理AVD](https://developer.android.com/studio/run/managing-avds.html)。
3. 在工具栏中点击**运行图标**，或者选择菜单中的**Run > Run**。
4. 如果一切正常，您应该在您的设备或模拟器上看到您的第一个应用程序：

![第一个应用程序](https://flutter.io/images/flutter-starter-app-android.png)

### 尝试热重载（hot reload）

Flutter基于**热重载（hot reload）**提供了一个非常快速的开发周期，可在实时运行的应用中重新加载代码而无需重新启动而导致丢失应用状态。只需对源代码进行更改，然后告诉你的编辑器或命令行工具你需要热重载（hot reload），然后在模拟器、仿真器或设备中就可以看到你的更改。

1. 将字符串`'You have pushed the button this many times:'`更改为`'You have clicked the button this many times:'`
2. 不要按“停止”按钮，请让你的应用继续运行。
3. 想要查看你的更改，请保**存所有文件**（`cmd-s` / `ctrl-s`），或者点击**Hot Reload 按钮**（带有闪电图标的按钮）。

您在运行的应用程序中应该几乎立即看到字符串的更新。

---
## VS Code

**VS Code**：轻量级编辑器，支持Flutter运行和调试。

### 创建新的应用程序

1. 启动VS Code
2. 调用**View>Command Palette…**
3. 输入“flutter”，然后选择“**Flutter: New Project**”执行
4. 输入一个项目名称（例如：`myapp`），然后按下Enter键
5. 指定放置项目的位置，然后选择蓝色的确认按钮
6. 等待项目创建，并显示`main.dart`文件

上述命令创建了一个名为`myapp`的Flutter项目目录，其中包含一个使用[Material Components](https://material.io/guidelines/)的简单应用程序示例。

在项目目录中，你的应用程序的代码在`lib/main.dart`下。

### 运行应用程序

1. 确保在VS Code的右下角选择了目标设备
2. 按下键盘上的F5按钮，或者调用**Debug>Start Debugging**
3. 等到应用加载启动
4. 如果一切正常，在应用程序建成后，您应该在您的设备或模拟器上看到您的第一个应用程序：

![第一个应用程序](https://flutter.io/images/flutter-starter-app-android.png)

### 尝试热重载（hot reload）

Flutter基于**热重载（hot reload）**提供了一个非常快速的开发周期，可在实时运行的应用中重新加载代码而无需重新启动而导致丢失应用状态。只需对源代码进行更改，然后告诉你的编辑器或命令行工具你需要热重载（hot reload），然后在模拟器、仿真器或设备中就可以看到你的更改。

1. 在您最喜欢的Dart代码编辑器中打开文件`lib/main.dart`
2. 将字符串`'You have pushed the button this many times:'`更改为`'You have clicked the button this many times:'`
3. 不要按“停止”按钮，请让你的应用继续运行。
4. 想要查看你的更改，请保**存所有文件**（`cmd-s` / `ctrl-s`），或者点击**Hot Reload 按钮**（绿色的圆形箭头按钮）。

您在运行的应用程序中应该几乎立即看到字符串的更新。

--- 
## Terminal + editor

**Terminal + editor**：Your editor-of-choice combined with Flutter’s terminal tool for running and building.

### 创建新的应用程序

1. 使用`flutter create`命令创建一个新的项目：

```
$ flutter create myapp
$ cd myapp
```

上述命令创建了一个名为`myapp`的Flutter项目目录，其中包含一个使用[Material Components](https://material.io/guidelines/)的简单应用程序示例。

在项目目录中，你的应用程序的代码在`lib/main.dart`下。

### 运行应用程序

* 检查是否有一个Android设备正在运行中。如果没有显示，请查看[设置]()。

```
$ flutter devices
```

* 使用`flutter run`命令运行应用程序：

```
$ flutter run
```

* 如果一切正常，在应用程序建成后，您应该在您的设备或模拟器上看到您的第一个应用程序：

![第一个应用程序](https://flutter.io/images/flutter-starter-app-android.png)

### 尝试热重载（hot reload）

Flutter基于**热重载（hot reload）**提供了一个非常快速的开发周期，可在实时运行的应用中重新加载代码而无需重新启动而导致丢失应用状态。只需对源代码进行更改，然后告诉你的编辑器或命令行工具你需要热重载（hot reload），然后在模拟器、仿真器或设备中就可以看到你的更改。

1. 打开`lib/main.dart`文件
2. 将字符串`'You have pushed the button this many times:'`更改为`'You have clicked the button this many times:'`
3. 不要按“停止”按钮，请让你的应用继续运行。
4. 想要查看你的更改，请保**存所有文件**（`cmd-s` / `ctrl-s`），或者点击**Hot Reload 按钮**（带有闪电图标的按钮钮）。

您在运行的应用程序中应该几乎立即看到字符串的更新。

---
## Next

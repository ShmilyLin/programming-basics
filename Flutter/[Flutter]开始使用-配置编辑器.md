# [Flutter]开始使用：配置编辑器

您可以把任意的文本编辑器与命令行工具结合使用来构建Flutter应用程序。不过，我们建议使用我们提供的任意一个编辑器插件以获得更好的体验。通过我们的编辑器插件，您可以获得代码自动补全，语法高亮，组件编辑辅助，运行和调试支持等等。

按照之前的步骤为Android Studio、IntelliJ或VS Code添加编辑器插件。 如果你想使用不同的编辑器，那没关系，直接跳到下一步：创建并运行你的第一个应用程序。

---
## 配置Android Studio

**Android Studio**：为Flutter提供完整的集成IDE体验。

### 安装Android Studio

* [Android Studio](https://developer.android.com/studio/index.html)，3.0版本或更新版本。

或者，您也可以使用IntelliJ：

* [IntelliJ IDEA Community](https://www.jetbrains.com/idea/download/), 2017.1版本或更新版本。
* [IntelliJ IDEA Ultimate](https://www.jetbrains.com/idea/download/), 2017.1版本或更新版本。

### 安装Flutter和Dart插件

Flutter由两个插件支持：

* `Flutter`插件支持Flutter开发人员工作流程（运行，调试，热重载等）。
* `Dart`插件提供了代码分析（代码验证，键入代码，完成代码等）。

安装这些：

1. 启动Android Studio.
2. 打开plugin preferences（macOS中是**Preferences>Plugins**，Windows & Linux中是**File>Settings>Plugins**）。
3. 选择Browse repositories…，然后选择Flutter插件并点击 `install`.
4. 当提示安装Dart插件时，请单击`Yes`。
5. 出现提示时单击`Restart`。

---
## 设置Visual Studio Code（VS Code）

**VS Code**：轻量级编辑器，支持Flutter运行和调试。

### 安装VS Code

* [VS Code](https://code.visualstudio.com/)，1.20.1版本或更新版本。

### 安装Dart代码插件

1. 启动VS Code
2. 调用**View>Command Palette…**
3. 输入“install”，然后选择**“Extensions：Install Extension”**操作
4. 在搜索框中输入`dart code`，在列表中选择“Dart Code”，然后点击**Install**
5. 选择“OK”以重新加载VS Code

### 通过Flutter Doctor验证您的设置

1. 调用**View>Command Palette…**
2. 输入“doctor”，然后选择**“Flutter: Run Flutter Doctor”**操作
3. 查看“OUTPUT”栏中的输出是否有问题


---
## Next

[[Flutter]启动：调试运行]([Flutter]启动-调试运行.md)
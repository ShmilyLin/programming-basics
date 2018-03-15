# [Flutter]开始：在macOS上安装

## 系统要求

想要安装并运行Flutter，你的开发环境必须满足以下最低要求：

* 操作系统：macOS（64-bit）
* 硬盘空间：700 MB（不包括Xcode或Android Studio的磁盘空间）。
* 工具：Flutter依赖于你系统环境中的这些可用的命令行工具。
  * `bash`, `mkdir`, `rm`, `git`, `curl`, `unzip`, `which`

## 获取Flutter SDK

要获取Flutter，需要使用`git`克隆仓库，然后添加`flutter`到你的PATH中。运行`flutter doctor`会显示你还需要安装的剩余依赖项。

### 克隆仓库

如果这是你第一次在这台机器上安装Flutter，请克隆仓库的`dev`分支，然后将`Flutter`添加到你的PATH中：

```
$ git clone -b beta https://github.com/flutter/flutter.git
$ export PATH=`pwd`/flutter/bin:$PATH
```

上述命令为当前的终端窗口设置临时PATH变量。要将Flutter永久添加到PATH中，请参阅[更新你的PATH](#更新你的PATH)。

要更新现有版本的Flutter，请参阅[升级Flutter]()。

### 运行flutter doctor

运行以下命令查看是否需要安装一些依赖项以完成安装：

```
$ flutter doctor
```

该命令将检查你的环境并在终端窗口中显示报告。Dart SDK是与Flutter捆绑在一起的，所以没有必要单独安装Dart。 仔细检查显示出来的报告中是否提示需要安装其他软件或执行其他任务（以粗体显示）。

例如：

```
[-] Android toolchain - develop for Android devices
    • Android SDK at /Users/obiwan/Library/Android/sdk
    ✗ Android SDK is missing command line tools; download from https://goo.gl/XxQghQ
    • Try re-installing or updating your Android SDK,
      visit https://flutter.io/setup/#android-setup for detailed instructions.
```

第一次运行flutter命令（如`flutter doctor`）时，它会下载自己的依赖关系并自行编译。后续运行应该将会快得多。

以下各节将介绍如何执行这些任务并完成设置过程。如果你选择使用IDE，你会看到`flutter doctor`会显示可用于IntelliJ IDEA、Android Studio和VS Code的插件。请参阅[配置编辑器]([Flutter]开始使用-配置编辑器.md)以了解安装Flutter和Dart插件的步骤。

你安装了所有缺失的依赖关系后，请再次运行`flutter doctor`命令来验证你是否已经设置正确。

`flutter`使用Google Analytics来匿名报告功能使用情况统计和基本崩溃日志。 这些数据用于帮助改进`flutter`。 分析数据不会在第一次运行或运行任何涉及`flutter config`时发送，因此你可以在发送任何数据之前退出分析。 如果要禁用报告，请输入`flutter config --no-analytics`；如果需要显示当前设置，请输入`flutter config`。 请参阅Google的隐私政策：[www.google.com/intl/zh-CN/policies/privacy](https://www.google.com/intl/en/policies/privacy/)。

### 更新你的PATH

你在命令行中只能更新当前会话的PATH变量，就像[Clone the Flutter repo](https://flutter.io/setup-macos/#clone-the-repo)中展示的那样。如果你想永久的改变这个变量，以便于你在任何一个终端会话中运行`flutter`命令。

永久改变所有终端会话的这个属性的操作是对于本机有效的。
Typically you add a line to a file that is executed whenever you open a new window. For example:

1. 确定放置Flutter SDK的目录。你将在步骤三中需要这个。
2. 打开（或创建）`$HOME/.bash_profile`。这个文件的路径或名称在你的机器上可能略有不同。
3. 添加下面几行，并将`[PATH_TO_FLUTTER_GIT_DIRECTORY]`更改为你克隆Flutter的git仓库的路径：

```
$ export PATH=[PATH_TO_FLUTTER_GIT_DIRECTORY]/flutter/bin:$PATH
```

4. 运行`source $HOME/.bash_profile`来刷新当前窗口。
5. 运行下面命令来验证`flutter/bin`目录是否在你的PATH中：

```
echo $PATH
```

更多详细内容，请看[StackExchange question](https://unix.stackexchange.com/questions/26047/how-to-correctly-add-a-path-to-path)。

## 编辑器设置

使用`flutter`命令行工具，你可以使用任何编辑器来开发Flutter应用。在提示中输入`flutter help`可以查看可用工具。

我们建议在编写、运行、调试Flutter应用时使用我们的插件以获得[丰富的IDE体验](https://flutter.io/using-ide/)。查看[配置编辑器]([Flutter]开始使用-配置编辑器.md)获得更多详细步骤。

## 平台设置

macOS支持开发iOS和Android两个平台的Flutter应用。现在完成两个平台中至少一个平台的设置步骤，以便能够构建并运行你的第一个Flutter应用。

## iOS设置

### 安装Xcode

想要开发iOS平台的Flutter应用，你需要一个安装了7.2或更新版本的Xcode的Mac：

1. 安装Xcode 7.2或更新版本（可以通过[网络下载](https://developer.apple.com/xcode/)安装或从[Mac App Store](https://itunes.apple.com/us/app/xcode/id497799835)中安装）。
2. 通过从命令行运行`sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer`来配置Xcode命令行工具以使用新安装的Xcode版本。

   当你想使用最新版本的Xcode时，大多数情况下，上面的路径都是正确的。如果你需要使用其他的版本，请改为指定该路径。

3. 确保之前打开过一次Xcode并签署通过了Xcode许可协议，可以从命令行运行`sudo xcodebuild -license`来确认。

使用Xcode，你可以在iOS设备或模拟器上运行Flutter应用。

### 设置iOS模拟器

要准备在iOS模拟器上运行并调试你的Flutter应用，请按以下步骤操作：

1. 在Mac上，通过Spotlight或使用以下命令找到模拟器：

```
$ open -a Simulator
```

2. 通过检查模拟器的**Hardware > Device**菜单中的设置，以确保你的模拟器正在使用64位设备（iPhone 5s或更高版本）。
3. 根据你的开发机器的屏幕大小，高屏幕密度的iOS模拟设备可能会在你的屏幕上溢出。在模拟器的**Window > Scale**菜单下设置设备比例。
4. 通过运行`flutter run`来启动你的应用。

### 部署到iOS设备

要将你的Flutter应用部署到真实的iOS设备（以下简称“真机”）上，你需要一些额外的工具和一个Apple帐户。你还需要在Xcode中对物理设备部署进行设置。

1. 安装[homebrew](http://brew.sh/)。
2. 打开终端并运行这些命令来安装用于将Flutter应用部署到iOS设备的工具。

```
$ brew update
$ brew install --HEAD libimobiledevice
$ brew install ideviceinstaller ios-deploy cocoapods
$ pod setup
```

如果这些命令中的任何一个失败并出现错误，请运行brew doctor并按照说明解决问题。

3. 遵循Xcode签名流程来配置你的项目：
    1. 从你的Flutter项目目录中的终端窗口中运行`ios/Runner.xcworkspace`来打开你的项目默认的Xcode工作空间。
    2. Xcode中，从左侧导航面板中选中`Runner`项目。
    3. `Runner` target设置页面，确保在**General > Signing > Team**下你的开发团队是被选中的。当你选择一个团队，Xcode会创建并下载开发证书，并在你的账号中注册你的设备，然后创建并下载一个描述文件（如果需要的话）。
        * 要开始你的第一个iOS开发项目，你可能需要使用你的Apple ID登录Xcode。
![设置开发团队](https://user-gold-cdn.xitu.io/2018/3/1/161e0630a728a48d?w=720&h=384&f=png&s=83179)
任何Apple ID都支持开发和测试。如果你想将你的应用上架到App Store，则需要注册Apple开发者计划才可以。查看[不同Apple会员类型之间的区别](https://developer.apple.com/support/compare-memberships)。
        * 当你第一次使用其他的物理设备进行iOS开发时，你需要同时在设备上信任Mac和开发证书。首次将iOS设备连接到Mac时，会弹出一个对话框，在对话框中选择信任即可。
![信任Mac](https://user-gold-cdn.xitu.io/2018/3/1/161e068732a383db?w=341&h=250&f=png&s=95278)
然后去iOS设备上设置应用程序，**General > Device Management**下选择信任你的证书。
        * 如果Xcode中的自动签名失败，请验证项目中的**General> Identity> Bundle Identifier**下的值是否唯一。
![](https://user-gold-cdn.xitu.io/2018/3/1/161e06bc737a25b1?w=720&h=464&f=png&s=113336)
    2. 运行`flutter run`来启动你的应用。

## Android设置

### 安装Android Studio

要为Android开发Flutter应用，你可以使用Mac，Windows或Linux（64位）机器。

Flutter需要安装并配置Android Studio：

1. 下载并安装[Android Studio](https://developer.android.com/studio/index.html)
2. 启动Android Studio，然后执行“Android Studio安装向导”。这将安装最新的Android SDK，Android SDK平台工具和Android SDK构建工具，这是Flutter开发Android应用时所必备的。

### 设置你的安卓设备

要准备在Android设备上运行并测试你的Flutter应用，你需要运行Android 4.1（API级别16）或更高版本的Android设备。

1. 在你的设备上启用**开发人员选项**和**USB调试**。详细说明可在[Android文档](https://developer.android.com/studio/debug/dev-options.html)中找到。
2. 使用USB线将手机与电脑链接。如果你的设备出现提示，请授权你的计算机访问你的设备。
3. 在终端中，运行`flutter devices`命令以验证Flutter识别你连接的Android设备。
4. 运行`flutter run`来启动你的应用。

默认情况下，Flutter使用`adb`工具所基于的Android SDK版本。如果你希望Flutter使用安装的其他的Android SDK，则必须将`ANDROID_HOME`环境变量设置为该安装目录。

### 设置Android模拟器

要准备在Android模拟器上运行并测试你的Flutter应用，请按照以下步骤操作：

1. 在你的机器上启用[VM加速](https://developer.android.com/studio/run/emulator-acceleration.html)。
2. 启动**Android Studio>Tools>Android>AVD Manager**，然后选择**Create Virtual Device**。
3. 选择一个设备定义并选择**Next**。
4. 为要模拟的Android版本选择一个或多个系统映像，然后选择**Next**。 建议使用*x86*或*x86_64*映像。
5. 在仿真性能下，选择**Hardware - GLES 2.0**以启用[硬件加速](https://developer.android.com/studio/run/emulator-acceleration.html)。
6. 验证AVD配置是否正确，然后选择**Finish**。

   有关上述步骤的详细信息，请参阅[管理AVD](https://developer.android.com/studio/run/managing-avds.html)。

7. 在Android虚拟设备管理器中，单击工具栏中的**Run**。模拟器启动并显示所选操作系统版本和设备的默认画布。
8. 运行`flutter run`来启动你的应用。连接的设备名称是`Android SDK built for <platform>`，其中`platform`是芯片系列，如x86。

---
## Next

[[Flutter]开始使用：配置编辑器]([Flutter]开始使用-配置编辑器.md)
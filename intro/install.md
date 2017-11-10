# 安装SDK

推荐优先使用工具自动安装SDK。

注意：由于众所周知的原因，在中国大陆使用以下工具安装可能会失败。如果你无法突破网络封锁，请尝试[手动安装](/intro/manual.md)。

## windows系统

### 方式一

安装windows下的包管理器：[Chocolatey](https://chocolatey.org/) ，然后在命令行下执行

```bash
choco install dart-sdk -version <版本号>
```

### 方式二

使用社区维护的安装器：[www.gekorm.com/dart-windows](http://www.gekorm.com/dart-windows/)

## mac系统

使用包管理器 [homebrew](https://brew.sh/) 安装

```bash
# 安装
$ brew tap dart-lang/dart
$ brew install dart            // 安装稳定版
$ brew install dart --devel    // 安装dev版

# 更新
$ brew update
$ brew upgrade dart
$ brew cleanup dart

# 查看安装路径等信息
$ brew info dart
```

## linux系统

ubuntu/debian使用apt-get安装，其他linux请[手动安装](/intro/manual.md)。

```bash
# 安装
$ sudo apt-get update
$ sudo apt-get install apt-transport-https
$ sudo sh -c 'curl https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'
$ sudo apt-get update
$ sudo apt-get install dart

# 如果需要dev版，则使用以下指令替换上面的第四步
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_unstable.list > /etc/apt/sources.list.d/dart_unstable.list'

# 设置环境变量
$ export PATH=/usr/lib/dart/bin:$PATH
```

# 手动安装SDK

不能使用工具安装SDK时，可以手动安装。

## 下载SDK

SDK下载链接模板:

[https://storage.googleapis.com/dart-archive/channels/&lt;stable/dev&gt;/release/&lt;release&gt;/sdk/dartsdk-&lt;platform&gt;-&lt;architecture&gt;-release.zip](https://storage.googleapis.com/dart-archive/channels/<stable/dev>/release/<release>/sdk/dartsdk-<platform>-<architecture>-release.zip)

按照以下规则构造下载地址：

* &lt;stable/dev&gt; - 选择稳定/开发版，可选项：stable，dev

* &lt;release&gt; - 版本号，比如：1.16.1, 1.16.0-dev.1.0

* &lt;platform&gt; - 平台，可选项：windows, macos, linux

* &lt;architecture&gt; - 系统架构，32位或64位，可选项：ia32，x64

地址示例：

> [https://storage.googleapis.com/dart-archive/channels/stable/release/1.11.1/sdk/dartsdk-windows-ia32-release.zip](https://storage.googleapis.com/dart-archive/channels/stable/release/1.11.1/sdk/dartsdk-windows-ia32-release.zip)
>
> [https://storage.googleapis.com/dart-archive/channels/stable/release/1.12.0/sdk/dartsdk-macos-x64-release.zip](https://storage.googleapis.com/dart-archive/channels/stable/release/1.12.0/sdk/dartsdk-macos-x64-release.zip)
>
> [https://storage.googleapis.com/dart-archive/channels/dev/release/1.13.0-dev.0.0/sdk/dartsdk-linux-ia32-release.zip](https://storage.googleapis.com/dart-archive/channels/dev/release/1.13.0-dev.0.0/sdk/dartsdk-linux-ia32-release.zip)

## 安装

下载解压后，将sdk的bin文件夹添加到系统环境变量即可。

# 编辑器

使用具备Dart插件的编辑器，能让开发事半功倍；下面列举了部分Dart官网推荐的编辑器/IDE。

笔者使用较多的是VS Code。

## Jetbrains家族

[Jetbrains](https://www.jetbrains.com/)公司的IntelliJ IDEA、WebStorm、PhpStorm等，可以安装Jetbrains的[Dart](https://plugins.jetbrains.com/plugin/6351-dart)插件

## VS Code

来自微软Visual Studio团队的[VS Code](https://code.visualstudio.com/)，配合[Dart Code](https://marketplace.visualstudio.com/items?itemName=DanTup.dart-code)插件

## Atom

Github出品的[Atom](https://atom.io/)编辑器，配合[dartlang](https://github.com/dart-atom/dartlang/)插件

## Vim

Linux下常用的老牌编辑器[Vim](http://www.vim.org/)，配合[dart-vim-plugin](https://github.com/dart-lang/dart-vim-plugin)插件



# Hello World

按照惯例，编写一个Hello World。

## 确认SDK安装成功

在命令行中输入以下指令

```bash
$ dart --version
```

如果输出以下类似信息，则表面SDK安装成功

```
Dart VM version: 1.24.2 (Thu Jun 22 08:42:17 2017) on "macos_x64"
```

# 运行Hello World

与C语言等类似，dart文件的入口是`main`函数。

在编辑器中新建一个hello.dart文件，并输入以下代码

```dart
main() {
  // print是全局打印函数，类似于JavaScript的console.log和Java的System.out.print
  print('Hello World!');
}
```

在命令行中执行它

```
$ dart hello.dart
Hello World!
```

成功执行则表明最基本的Dart开发环境已配置完成。


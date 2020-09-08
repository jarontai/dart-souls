# 准备

本节讲解最基础的准备工作，包括安装 Dart SDK，选择编辑器，以及编写最简单的 Hello World 等。

## 安装 SDK

推荐优先使用工具自动安装 SDK。

注意：由于众所周知的原因，在中国大陆使用以下工具安装可能会失败。如果失败，请尝试[手动安装](#手动安装-sdk)。

### Windows 系统

#### 方式一

安装 windows 下的包管理器：[Chocolatey](https://chocolatey.org/) ，然后在命令行下执行

```bash
choco install dart-sdk // 安装
choco upgrade dart-sdk // 更新
choco uninstall dart-sdk // 卸载
```

#### 方式二

使用社区维护的安装器（.exe格式)：[www.gekorm.com/dart-windows](http://www.gekorm.com/dart-windows/)


### Mac 系统

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

### Linux 系统

ubuntu/debian 使用 apt-get 安装，其他 linux 请[手动安装](#手动安装-sdk)。

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

### 确认 SDK 安装成功

在命令行中输入以下指令

```bash
$ dart --version
```

如果输出类似如下的信息，则表明 SDK 安装成功

```
Dart VM version: 1.24.2 (Thu Jun 22 08:42:17 2017) on "macos_x64"
```

---

## 手动安装 SDK

使用工具自动安装 SDK 失败时，还可以手动安装。

### 下载 SDK

SDK 下载链接模板:

[https://storage.googleapis.com/dart-archive/channels/&lt;stable/dev&gt;/release/&lt;release&gt;/sdk/dartsdk-&lt;platform&gt;-&lt;architecture&gt;-release.zip](https://storage.googleapis.com/dart-archive/channels/<stable/dev>/release/<release>/sdk/dartsdk-<platform>-<architecture>-release.zip)

按照以下规则构造下载地址：

* &lt;stable/dev&gt; - 选择稳定/开发版，可选项：stable，dev

* &lt;release&gt; - 版本号，比如：2.5.2, 2.1.0.9-dev-2

* &lt;platform&gt; - 平台，可选项：windows, macos, linux

* &lt;architecture&gt; - 系统架构，32位或64位，可选项：ia32，x64

地址示例：

> [https://storage.googleapis.com/dart-archive/channels/stable/release/2.9.2/sdk/dartsdk-windows-x64-release.zip](https://storage.googleapis.com/dart-archive/channels/stable/release/2.9.2/sdk/dartsdk-windows-x64-release.zip)
>
> [https://storage.googleapis.com/dart-archive/channels/stable/release/2.9.2/sdk/dartsdk-macos-x64-release.zip](https://storage.googleapis.com/dart-archive/channels/stable/release/2.9.2/sdk/dartsdk-macos-x64-release.zip)


### 安装

下载并解压，将 sdk 中的 bin 文件夹添加到系统环境变量即可。

---

## 编辑器

使用具备 Dart 插件的编辑器，能让开发事半功倍。下面将列举部分 Dart 官网推荐的编辑器或 IDE，如何选择完全看个人喜好，对于初学者，笔者推荐的是 VS Code（免费，插件安装方便，编码体验较好）。

### Jetbrains家族

[Jetbrains](https://www.jetbrains.com/) 公司的 IntelliJ IDEA、WebStorm、PhpStorm 等，都可以安装 Jetbrains 的 [Dart](https://plugins.jetbrains.com/plugin/6351-dart) 插件

### VS Code

来自微软 Visual Studio 团队的 [VS Code](https://code.visualstudio.com/)，配合 [Dart Code](https://marketplace.visualstudio.com/items?itemName=Dart-Code.dart-code) 插件

### Atom

Github 出品的 [Atom](https://atom.io/) 编辑器，配合 [dartlang](https://github.com/dart-atom/dartlang/) 插件

### Vim

Linux 下常用的老牌编辑器 [Vim](http://www.vim.org/)，配合 [dart-vim-plugin](https://github.com/dart-lang/dart-vim-plugin) 插件

---

## Hello World

按照惯例，编写一个 Hello World。

### 编写

在编辑器中新建一个 hello.dart 文件，并输入以下代码

```dart
main() {
  // print是全局打印函数，类似于JavaScript的console.log和Java的System.out.print
  print('Hello World!');
}
```

与C语言等类似，dart 文件的入口是`main`函数。

### 运行

在命令行中执行 hello.dart 并查看输出

```
$ dart hello.dart
Hello World! // 输出 Hello World!
```

成功执行则表明最基本的 Dart 开发环境已配置完成。


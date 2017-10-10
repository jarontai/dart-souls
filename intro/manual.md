# 手动安装SDK

## 下载SDK

SDK下载链接模板:

> [https://storage.googleapis.com/dart-archive/channels/&lt;stable/dev&gt;/release/&lt;release&gt;/sdk/dartsdk-&lt;platform&gt;-&lt;architecture&gt;-release.zip](https://storage.googleapis.com/dart-archive/channels/<stable/dev>/release/<release>/sdk/dartsdk-<platform>-<architecture>-release.zip)

按照说明构造下载地址：

* &lt;stable/dev&gt; - 选择稳定/开发版，可选项：stable，dev

* &lt;release&gt; - 版本号，比如：1.16.1, 1.16.0-dev.1.0

* &lt;platform&gt; - 平台，可选项：windows, macos, linux

* &lt;architecture&gt; - 系统架构，32位或64位，可选项：ia32，x64

示例：

> [https://storage.googleapis.com/dart-archive/channels/stable/release/1.11.1/sdk/dartsdk-windows-ia32-release.zip](https://storage.googleapis.com/dart-archive/channels/stable/release/1.11.1/sdk/dartsdk-windows-ia32-release.zip)
>
> [https://storage.googleapis.com/dart-archive/channels/stable/release/1.12.0/sdk/dartsdk-macos-x64-release.zip](https://storage.googleapis.com/dart-archive/channels/stable/release/1.12.0/sdk/dartsdk-macos-x64-release.zip)
>
> [https://storage.googleapis.com/dart-archive/channels/dev/release/1.13.0-dev.0.0/sdk/dartsdk-linux-ia32-release.zip](https://storage.googleapis.com/dart-archive/channels/dev/release/1.13.0-dev.0.0/sdk/dartsdk-linux-ia32-release.zip)

## 安装

下载解压后，将sdk的bin文件夹添加到系统环境变量即可。


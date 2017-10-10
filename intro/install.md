# 使用工具安装SDK

注意：由于众所周知的原因，在中国大陆使用以下工具安装可能会失败；如果你无法突破网络封锁，请尝试[手动安装](/intro/manual.md)。

## windows

### 方式一

使用 [Chocolatey](https://chocolatey.org/)

```bash
choco install dart-sdk -version <版本号>
```

### 方式二

使用社区维护的安装器：[www.gekorm.com/dart-windows](http://www.gekorm.com/dart-windows/)

## mac

使用 [homebrew](https://brew.sh/) 安装

```bash
# 安装
brew tap dart-lang/dart
brew install dart

# 更新
brew update
brew upgrade dart
brew cleanup dart

# 查看安装信息
brew info dart
```

## linux

ubuntu/debian使用apt-get安装，其他linux请[手动安装](/intro/manual.md)。

```bash
$ sudo apt-get update
$ sudo apt-get install apt-transport-https
$ sudo sh -c 'curl https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'
$ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'
$ sudo apt-get update
$ sudo apt-get install dart
```




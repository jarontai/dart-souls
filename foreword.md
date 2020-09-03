# 前言

Dart 是由 Google 创造的一门通用编程语言，主要创始人是丹麦的编程语言虚拟机专家 Lars Bak，他同时也是 Java 虚拟机 Hotspot JVM 和 JavaScript 虚拟机 v8 项目的主要领导者。Dart 有着类C的语法，支持闭包、类、泛型、mixin、Null Safety、异步编程等等。Dart 吸收了众多语言如：Smalltalk、JavaScript、Java 和 C# 等的优秀特性，自成一体且易于上手。

Dart 初次公布于2011年，定位为web编程语言，以替代 JavaScript 并嵌入 Chrome 为目标。经历数年的曲折发展，于2015年放弃嵌入 Chrome，同时转型为编译输出 JavaScript，且能编写移动端和服务端的通用语言。因初期的定位不明确，在发布后的数年内，Dart 一直不温不火，除 Google 自己外，真正在使用 Dart 的公司屈指可数。除了在发布后的一两年内吸引了较多关注外，时至今日（指2017年），近乎无人问津的状态，对比其他2000年后诞生的语言，如 Google 自己的 Go，Apple 的 Swift，Mozilla 的 Rust等，Dart 的发展真算是惨淡。

幸好，随着发展方向的明确以及语言特性逐渐丰富和稳定，Dart 近两年的发展令人欣喜。首先，Google 内部的 AdWords、AdSense 等大型web项目都在使用 Dart 重构，Google 新推出的跨平台移动端开发工具 [Flutter](https://flutter.io/) 也使用 Dart 构建，而 Google 正在秘密研发的新操作系统 [Fuchsia](https://github.com/fuchsia-mirror)，也在使用 Dart 和 Flutter（基于Dart等跨平台应用开发框架）。此外，使用 Dart 的外部公司也开始慢慢[增多](https://www.dartlang.org/community/who-uses-dart)。虽然发展道路艰辛而曲折，但 Dart 的未来还是让人颇为期待。

笔者，作为一名坚定的 Dart 语言爱好者，为了梳理自身的 Dart 知识，整理了这本小书。水平有限，难免疏漏，欢迎交流指正。

Jaron

2017.11

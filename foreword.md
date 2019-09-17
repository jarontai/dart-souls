# 前言

Dart 是由 Google 创造的一门通用编程语言，它语法类似于C语言，支持类、泛型、mixin、异步编程等。Dart 是纯面向对象的，即所有变量都是对象，数字、字符串甚至 null 也是对象；Dart 的类型是可选的，即类型在语法层面是可选的，并且对代码运行没有实质影响（仅适用于 Dart 1，Dart 2 的类型不再可选，但因为有类型推导，编码体验并无太大改变）。

Dart 初次公布于2011年，定位为web编程语言，以替代 JavaScript 并嵌入 Chrome 为目标。发展几年后，于2015年放弃嵌入 Chrome，同时转型为编译输出 JavaScript，且能编写移动端和服务端的通用语言。因定位不明以及发展初期的不稳定性，发布后数年内，Dart 一直不温不火，除了 Google 自己外，真正在使用 Dart 的公司屈指可数。而 Dart 在中国的发展更是惨淡，除发布后一两年吸引了部分开发者关注外，时至今日，近乎无人问津。对比其他2000年后诞生的语言，如 Google 自己的 Go，Apple 的 Swift 等，Dart 的发展真是缓慢而曲折。

幸好，随着发展方向的明确以及语言特性逐渐稳定，Dart 近一两年的发展还是令人欣喜的。首先，Google 内部的 AdWords、AdSense 等大型web项目都在使用 Dart 重构，Google 新推出的跨平台移动端开发工具 [Flutter](https://flutter.io/) 也使用 Dart 构建，而 Google 正在秘密研发的新操作系统 [Fuchsia](https://github.com/fuchsia-mirror)，也在使用 Dart 和 Flutter。此外，使用 Dart 的外部公司也开始慢慢[增多](https://www.dartlang.org/community/who-uses-dart)。虽然发展道路曲折，但Dart的未来还是让人颇为期待。

笔者，作为一名坚定的 Dart 语言爱好者，为了梳理自身的 Dart 知识，整理了这本小书。水平有限，难免疏漏，欢迎交流指正。

Jaron

2017.11


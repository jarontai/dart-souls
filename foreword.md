# 前言

Dart是由Google创造的一门通用编程语言，它语法类似于C语言，支持类、泛型、mixin、异步编程等。Dart是纯面向对象的，使用可选类型的动态语言（Dart 1.x）。纯面向对象是指所有变量都是对象，数字、字符串甚至`null`也是对象；可选类型是指类型在语法层面是可选的，并且对代码运行没有实质影响；动态语言通常是指在运行时才做数据类型检查的语言。

Dart初次公布于2011年，初期专注于web编程领域，并以替代JavaScript为发展目标，后转型为通用型语言，逐步向移动端与服务端发展。在发布后的几年内，Dart的发展一直不温不火，除了屈指可数的几个中小型公司以及Google自己外，真正使用Dart的公司比较少。在笔者看来，语言发展初期的不稳定性，应该是造成此种状况的主要原因。即从初期以替代JavaScript并嵌入Chrome为目标的web编程语言，变更为一门通用型语言，以及吸收众多动态/静态语言的优点，不断修改迭代语言设计等。

Dart正式发布已经六年，对比其他2000年后诞生的语言，如Google自己的Go，Apple的Swift等，Dart的发展真算是缓慢而曲折。虽然如此，随着语言特性逐渐稳定，Dart近一两年的发展还是令人欣喜的。首先，Google内部的AdWords、AdSense等重要盈利项目都在使用Dart重构web端，Google新推出的跨平台移动app开发工具[Flutter](https://flutter.io/)也是使用Dart构建，而Google正在秘密研发的新操作系统[Fuchsia](https://github.com/fuchsia-mirror)，也在使用Dart和Flutter；此外，使用Dart的外部公司也开始慢慢[增多](https://www.dartlang.org/community/who-uses-dart)。

虽然发展道路曲折，但Dart的未来还是让人颇为期待。而笔者，作为一名Dart爱好者，为了能够更好地学习与梳理Dart的知识，写下了这本小书，也算为Dart在中国的发展添一份微薄之力。


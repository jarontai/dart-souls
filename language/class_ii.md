# 类 - Part II

_类的知识点较多，所以分成两节进行讲解，本节是Part II，上一节是_[_Part I_](/language/class_i.md)_。_

---

本节继续讲解类的知识点，主要包括抽象类/方法，接口，mixin以及枚举。

## 抽象类和抽象方法

没有函数体的方法，即只声明而不实现的方法被称为抽象方法，它只能出现在抽象类中。抽象类是使用`abstract`关键字修饰的类，它可以包含非抽象方法，可以被继承但不能被实例化。

```dart
// 大剑抽象类
abstract class GreatSword {
  // 抽象方法
  upgrade();

  // 非抽象方法
  use() {
    print('attack');
  }
}

// 混种大剑继承大剑
class BastardSword extends GreatSword {
  // 实现父类的抽象方法 
  upgrade() {
    print('upgrade');
  }

  // 重写且使用父类已有的实现
  use() {
    super.use();
  }
}
```

## 接口

Dart 支持接口，但没有定义接口的关键字。Dart 的每个类都隐含定义了一个接口，该接口包含当前类所有的实例变量和方法（包含通过继承和实现其他类而得来的）。通常使用抽象类来定义接口，而接口的实现是通过`implements`关键字，多个接口之间使用逗号分隔。

```dart
// 轻攻击接口
abstract class Light {
  lightAttack();
}

// 重攻击接口
abstract class Heavy {
  heavyAttack();
}

// 武器同时实现了轻重攻击
class Weapon implements Light, Heavy {
  lightAttack() {
    print('Light attack!');
  }
  
  heavyAttack() {
    print('Heavy attack!!!');
  }
}
```

## mixin
TODO:

## 枚举
TODO:

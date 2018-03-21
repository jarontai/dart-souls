# 类 - Part II

_类的知识点较多，所以分成两节进行讲解，本节是Part II，上一节是_[_Part I_](/language/class_i.md)_。_

---

本节继续讲解类的知识点。

## 抽象类和抽象方法

没有函数体的方法，即只声明而不实现的方法被称为抽象方法，抽象方法只能出现在抽象类中。抽象类使用`abstract`关键字修饰，它可以包含非抽象方法，可以被继承但不能被实例化。

```dart
// 大剑
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

## mixin

## 枚举




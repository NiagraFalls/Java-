# 基础
## 方法
Java语言也有类似于Python的this,当局部变量和方法的实例变量重名时，用this指明field。

可变参数相当于数组类型

参数绑定，基本类型数据的值不会改变，引用类型会改变的。

## 构造方法
constructer的名字就是类名，没有返回值，也没有void,为了调用它，需要使用new关键字。

默认构造方法没有语句。当我们定义了构造方法后，编译器将不会自动创建构造方法。

在Java中，创建对象实例的时候，按照如下顺序进行初始化：

1. 先初始化字段，例如，int age = 10;表示字段初始化为10，double salary;表示字段默认初始化为0，String name;表示引用类型字段默认初始化为null；
2. 执行构造方法的代码进行初始化。

因此，构造方法的代码由于后运行，所以，字段值最终由构造方法的代码确定。

一个构造方法可以调用其他构造方法，这样做的目的是便于代码复用。调用其他构造方法的语法是this(…)：

## 方法重载
方法名相同，但各自的参数不同，称为方法重载（Overload）。

举个例子，String类提供了多个重载方法indexOf()，可以查找子串：

int indexOf(int ch)：根据字符的Unicode码查找；

* int indexOf(String str)：根据字符串查找；

* int indexOf(int ch, int fromIndex)：根据字符查找，但指定起始位置；

* * int indexOf(String str, int fromIndex)根据字符串查找，但指定起始位置。
## 继承
在OOP的术语中，我们把Person称为超类（super class），父类（parent class），基类（base class），把Student称为子类（subclass），扩展类（extended class）。

这是因为在Java中，任何class的构造方法，第一行语句必须是调用父类的构造方法。如果没有明确地调用父类的构造方法，编译器会帮我们自动加一句super();

这种把一个子类类型安全地变为父类类型的赋值，被称为向上转型（upcasting）。

继承是is关系，组合是has关系。

## 多态
加上@Override可以让编译器帮助检查是否进行了正确的覆写

多态是指，针对某个类型的方法调用，其真正执行的方法取决于运行时期实际类型的方法。

允许添加更多类型的子类实现功能扩展，却不需要修改基于父类的代码。

在子类的覆写方法中，如果要调用父类的被覆写的方法，可以通过super来调用。例如：

final修饰符有多种作用：

final修饰的方法可以阻止被覆写；

final修饰的class可以阻止被继承；

final修饰的field必须在创建对象时初始化，随后不可修改。

## 抽象类
把一个方法声明为abstract，表示它是一个抽象方法，本身没有实现任何方法语句。因为这个抽象方法本身是无法执行的，所以，Person类也无法被实例化。编译器会告诉我们，无法编译Person类，因为它包含抽象方法。

必须把Person类本身也声明为abstract，才能正确编译它：

因为抽象类本身被设计成只能用于被继承，因此，抽象类可以强迫子类实现其定义的抽象方法，否则编译会报错。因此，抽象方法实际上相当于定义了“规范”。

面向抽象编程的本质就是：

上层代码只定义规范（例如：abstract class Person）；

不需要子类就可以实现业务逻辑（正常编译）；

具体的业务逻辑由不同的子类实现，调用者并不关心。

## 接口
在Java中，使用interface可以声明一个接口：

**interface**** Person {**

    **void** run();

    String getName();

}

所谓interface，就是比抽象类还要抽象的纯抽象接口，因为它连字段都不能有。因为接口定义的所有方法默认都是public abstract的，所以这两个修饰符不需要写出来（写不写效果都一样）。

我们知道，在Java中，一个类只能继承自另一个类，不能从多个类继承。但是，一个类可以实现多个interface。

![图片](https://uploader.shimo.im/f/YjRNtA3Ia7womYkJ.png!thumbnail)

在接口中，可以定义default方法

接口可以继承。

## 静态字段和静态方法
![图片](https://uploader.shimo.im/f/062g12oWcKYMKPYH.png!thumbnail)

## 包
Java编译器最终编译出的.class文件只使用完整类名，因此，在代码中，当编译器遇到一个class名称时：

如果是完整类名，就直接根据完整类名查找这个class；

如果是简单类名，按下面的顺序依次查找：

查找当前package是否存在这个class；

查找import的包是否包含这个class；

查找java.lang包是否包含这个class。

编写class的时候，编译器会自动帮我们做两个import动作：

默认自动import当前package的其他class；

默认自动import java.lang.*。


## 作用域
## classpath和jar
jar包就是用来干这个事的，它可以把package组织的目录层级，以及各个目录下的所有文件（包括.class文件和其他文件）都打成一个jar文件，这样一来，无论是备份，还是发给客户，就简单多了。

jar包实际上就是一个zip格式的压缩文件，而jar包相当于目录。

jar包还可以包含其它jar包，这个时候，就需要在MANIFEST.MF文件里配置classpath了。

在大型项目中，不可能手动编写MANIFEST.MF文件，再手动创建zip包。Java社区提供了大量的开源构建工具，例如[Maven](https://www.liaoxuefeng.com/wiki/1252599548343744/1255945359327200)，可以非常方便地创建jar包。


## 模块
模块和JAR时平行概念

# core class
## 编码
Java的String和char在内存中总是以Unicode编码表示。

## StringJoiner
StringBuilder->StringJoiner->Strring.join

## Java Bean
JavaBean是一种符合命名规范的class，它通过getter和setter来定义属性；

属性是一种通用的叫法，并非Java语法规定；

可以利用IDE快速生成getter和setter；

使用Introspector.getBeanInfo()可以获取属性列表。

## 枚举类
Java使用enum定义枚举类型，它被编译器编译为final class Xxx extends Enum { … }；

通过name()获取常量定义的字符串，注意不要使用toString()；

通过ordinal()返回常量定义的顺序（无实质意义）；

可以为enum编写构造方法、字段和方法

enum的构造方法要声明为private，字段强烈建议声明为final；

enum适合用在switch语句中。

## BigInteger
## BigDecimal
## 常用工具类
Java提供的常用工具类有：

Math：数学计算

Random：生成伪随机数

SecureRandom：生成安全的随机数



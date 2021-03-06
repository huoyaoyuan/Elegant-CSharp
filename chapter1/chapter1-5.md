# 1-5 变量声明与赋值

**变量**是一个*存储空间*，存储某一类型的值。存储空间的值默认可以改变，在不可改变的场合，也被称为**只读量**或**常量**。

> 部分编程语言的存储空间默认为不可改变(如F#)，甚至不允许创建可变的存储空间(如Haskell)。

> 对于不可改变的存储空间，需要在声明的同时提供其值，见后文「初始化赋值」。

## 变量声明语句

C#的变量声明语句采用C语言风格的语法。

```csharp
类型 变量名;
```

例：

```csharp
int a;
char b;
string name;
```

在一条语句内，可以声明多个同类型的变量，其名称间用`,`分隔：

```csharp
int a, b, c;
```

在变量声明语句之前加上`readonly`，可以声明一个只读量。（计划于C# 7.2加入）

## 变量名

C#中的变量名需要为一个合法的**标识符**。标识符为程序中物件的名称，除变量外还有很多地方需要使用标识符。标识符允许包含以下字符：
- 数字`0`~`9`
  - 但不允许出现在开头。这是为了避免与数字值相混淆；无论整数值还是浮点数值，其开头字符一定是一个数字。
- 字母与文字
  - 详细定义：Unicode字符分类Lu,Ll,Lt,Lm,Lo,Nl,Mn,Mc,Pc,Cf
  - 包含拉丁字母、其它系统的字母、汉字等
  - 不包含Emoji
- 下划线符`_`
  - 为了保持C语系的传统，作为常用的分隔符存在。

`_`以外的各种标点（中文和英文标点）、空格、换行等不允许出现在标识符中。这些字符被视为词汇的分隔，而标识符需要作为*一个词汇*存在。

在C#语言中拥有特殊含义的单词（**关键字**）也不能直接作为标识符，如各种基本类型名。但如果在其前面加上一个`@`，可以将其作为标识符使用。

> 注意，`Main`并不是一个关键字。这也是C语言中的一个常见误区。事实上，这是一个受特殊对待的标识符，而通过调整一定的设置之后甚至可以改变受特殊对待的名称。

显而易见，两个变量不能拥有相同的名称，否则将无法区分该名称指的是哪一个变量。

> 准确来说，是同**作用域**内的变量名需要唯一。在学习程序结构之前，所有变量都是同样的作用域。

以下为合法的标识符示例：

```
a0
_local
_1
变量1
@int
```

## 变量赋值

C#的变量赋值采用C语言风格的语法。

```csharp
变量名 = 值;
```

例如：

```csharp
int a, b, c, d;
a = 1;
b = a; //允许将一个变量的值赋值给另一个变量
d = c = 2; //允许连环赋值
```

> 在将一个变量赋值给另一个变量之后，两个变量仍然占据着*不同的存储空间*，被改变的只是空间中的值。在赋值之后，对一个变量的改变并不会影响到另一个变量。

在赋值时，需要提供一个类型正确的值。如以下语句是错误的：

```csharp
int a;
a = 1.0;
```

这是因为`1.0`是一个`double`类型的值，因此不能被赋值给一个`int`类型的变量`a`。

> C#的*每个变量*都有一个类型，*每个值*也有一个类型，只有变量和值的类型匹配（类型相同，或者值的类型可以*转换*为变量的类型）时才允许赋值。

> 这个特性被称作**静态类型**，是开发高效、健壮应用程序的核心优势所在。与其相对被称为**动态类型**。C#中提供了特殊类型来提供动态类型的行为。

### 初始化赋值

变量的声明和赋值可以合并在同一条语句中，称为变量的**初始化**。如：

```csharp
string site = "GitHub";
readonly int l = 10; //不初始化的只读量没有意义。注意：此特性在本文写作时尚未发布
int a, b = 1; //一条语句声明的变量中，可以有的初始化，有的不初始化
```

### 隐式类型声明

在变量的初始化中，可以用关键字`var`来代替类型名。此时，变量的实际类型将与提供的值相同，称为**类型推断**：

在C# 7.2的提案中，`readonly var`可以用`let`代替。（未定案）

```csharp
var a = 1; //a是int
var b = 1u; //b是uint
var f = 1.0; //f是double
var c = 'a'; //c是char
a = 1.0; //这条语句是非法的————a的类型不能改变
```

> 在Visual Studio或者Visual Studio Code中，将鼠标移到`var`或者变量上，可以看到被推断出的实际类型。

> 类型推断在类型名称表达起来很复杂（复合类型），或者无法表达（隐式类型）时很有用。

|与JavaScript和Python的区别|
|-|
|`var`的含义是「不写出类型名」，但声明的变量仍然拥有一个类型。后续赋值仍然必须使用类型正确的值。|
|有一个特殊的类型`dynamic`，使变量不限定类型信息，用于动态类型行为。该类型实际上由编译器进行特殊处理，并不实际存在于.NET中。|

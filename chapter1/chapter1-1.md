# 1.1 背景介绍

## .NET平台

.NET(dotnet)是Microsoft开发的跨语言运行环境。其在设计之初便以不同编程语言之间的交互为目标，并已实现跨操作系统运行。C#是专门为.NET设计的一种编程语言，并被作为主流语言使用。
在.NET中，各种语言被编译到一门字节形式的中间语言（CIL/Common Indetermediate Language，旧称MSIL/Microsoft Indetermediate Language)，然后在目标机器上，由一个运行环境（CLR/Common Language Runtime）执行。

与Java的比较|
-|
历史上，Microsoft曾对Java做出一些私有改动，并导致了和Sun的官司。官司结果是Microsoft放弃对Java的改动，并重新设计一个平台与一门语言，便有了.NET与C#。|
CIL对应Java Bytecode，CLR对应JVM。|
.NET包含了大量Microsoft曾经加入Java的私有特性，或其变种。|
.NET将语言、运行时、标准库明确区分开，并相互独立进行更新。|
作为操作系统拥有者，Microsoft先着眼于.NET在Windows上的功能与应用性（并已成为Windows操作系统的底层服务），直到后期才在其它操作系统上发布了官方实现；Java则从诞生开始一直在各大操作系统上同步发布。|

在仅Windows时期，.NET又被称作.NET Framework。后来官方发布了跨平台可用的.NET Core，从此便以.NET作为整个运行时与环境的称呼，而.NET Framework则被视为.NET的一个发行版，在Windows上可用并具有丰富的、与系统集成较紧密的功能。

## .NET平台上的编程语言

### CIL

CIL的字节形式（二进制格式）是.NET程序的载体。为交流和处理方便，其有一个标准的文本表达形式。
作为载体，CIL的表达能力即为.NET程序的表达能力，因此被用于程序分析和特殊定制处理。由于语法冗长，CIL一般并不被直接用于编写程序。

### C#

C#是专门为.NET设计的编程语言，其特性主要继承自C++和Java。
C#的新式许多特性与.NET标准库紧密集成，为简化许多常见的模式而设计。

### Visual Basic .NET

Visual Basic从版本7开始被Microsoft进行了一次不完全兼容的改造，在保留与以前版本的风格的同时引入了对.NET特性的表达。

### C++/CLI

C++/CLI是对C++语法的一个扩展，提供了与非.NET内容直接交互的能力，以及操纵.NET底层细节的一些能力。C++/CLI可以直接编译出.NET、非.NEI内容混合的程序。

### F#

F#是一门以函数式为基干的编程语言，作为.NET家族的一员，在数据科学等领域受到青睐。
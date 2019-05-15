---
title: 序列化：定义可序列化的类
ms.date: 11/04/2016
helpviewer_keywords:
  - 'serializable class [MFC]'
  - 'DECLARE_SERIAL macro [MFC]'
  - 'default constructor [MFC]'
  - 'VERSIONABLE_SCHEMA macro [MFC]'
  - 'classes [MFC], derived'
  - 'IMPLEMENT_SERIAL macro [MFC]'
  - 'no-arguments constructor [MFC]'
  - 'Serialize method, overriding'
  - 'defaults [MFC], constructor'
  - 'CObject class [MFC], deriving serializable classes'
  - 'constructors [MFC], defining with no arguments'
  - 'serialization [MFC], serializable classes'
  - no default constructor
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
---
# <a name="serialization-making-a-serializable-class"></a>序列化：定义可序列化的类

使类可序列化所需的五个主要步骤。 下面列出了这些步骤，后续章节中对它们进行了说明：

1. [从 CObject 派生您的类](#_core_deriving_your_class_from_cobject)(或从派生自某个类`CObject`)。

1. [重写 Serialize 成员函数](#_core_overriding_the_serialize_member_function)。

1. [使用 DECLARE_SERIAL 宏](#_core_using_the_declare_serial_macro)类声明中。

1. [定义不采用任何参数的构造函数](#_core_defining_a_constructor_with_no_arguments)。

1. [在实现文件中使用 IMPLEMENT_SERIAL 宏](#_core_using_the_implement_serial_macro_in_the_implementation_file)为您的类。

如果您调用`Serialize`直接而不通过 >> 和 << 的运算符[CArchive](../mfc/reference/carchive-class.md)，最后三个步骤并不需要的序列化。

##  <a name="_core_deriving_your_class_from_cobject"></a> 从 CObject 派生您的类

基本序列化协议和功能在 `CObject` 类中定义。 通过从 `CObject` 或派生自 `CObject` 的类派生您的类（如类 `CPerson` 的以下声明中所示），您将能够访问 `CObject` 的序列化协议和功能。

##  <a name="_core_overriding_the_serialize_member_function"></a> 重写 Serialize 成员函数

在 `Serialize` 类中定义的 `CObject` 成员函数负责实际上序列化捕获对象的当前状态所需的数据。 `Serialize` 函数具有一个 `CArchive` 参数，供它读取和写入对象数据。 [CArchive](../mfc/reference/carchive-class.md)对象具有成员函数时， `IsStoring`，指示是否`Serialize`存储 （写入数据） 或加载 （读取数据）。 使用结果`IsStoring`作为指南，您可以插入对象的数据`CArchive`对象使用插入运算符 ( **<\<** ) 或使用提取运算符 (提取数据 **>>** ).

请考虑派生自类`CObject`并且具有的类型的两个新成员变量`CString`并**WORD**。 以下类声明片段显示了新成员变量以及重写的 `Serialize` 成员函数的声明：

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>重写 Serialize 成员函数

1. 调用基类版本的 `Serialize` 以确保对象的继承部分已序列化。

1. 插入或提取特定于您的类的成员变量。

   插入和提取运算符与存档类交互以读取和写入数据。 以下代码示例演示如何为前面声明的 `Serialize` 类实现 `CPerson`：

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

此外可以使用[carchive:: Read](../mfc/reference/carchive-class.md#read)并[carchive:: Write](../mfc/reference/carchive-class.md#write)成员函数来读取和写入大量的非类型化数据。

##  <a name="_core_using_the_declare_serial_macro"></a> 使用 DECLARE_SERIAL 宏

DECLARE_SERIAL 宏要求将支持序列化的类声明中，如下所示：

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

##  <a name="_core_defining_a_constructor_with_no_arguments"></a> 定义不带任何参数的构造函数

当 MFC 因为对象被反序列化（从磁盘加载）而重新创建对象时，MFC 需要一个默认构造函数。 反序列化过程将使用重新创建对象所需的值填写所有成员变量。

此构造函数可声明为公共、受保护或私有。 如果您使它成为受保护或私有构造函数，您就帮助确保了它只会由序列化函数使用。 构造函数必须将对象设为允许它在必要时删除的状态。

> [!NOTE]
>  如果你忘记了使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏的类中定义不带任何参数的构造函数，您将使用 IMPLEMENT_SERIAL 宏的位置的行出现"没有默认构造函数可用"编译器警告。

##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> 在实现文件中使用 IMPLEMENT_SERIAL 宏

IMPLEMENT_SERIAL 宏用于定义各种功能所需类派生可序列化类时从`CObject`。 您为您的类在实现文件 (.cpp) 中使用此宏。 此宏的前两个参数是类的名称和其直接基类的名称。

该宏的第三个参数是一个架构数字。 架构数字本质上是类的对象的版本号。 请对架构数字使用大于或等于 0 的整数值。 （不要将此架构数字与数据库术语混淆。）

MFC 序列化代码在将对象读入内存时检查架构数字。 如果磁盘上的对象的架构数字与内存中的架构数字不匹配，库将引发 `CArchiveException`，这会阻止您的程序读取不正确的版本的对象。

如果你想你`Serialize`成员函数，以便能够读取多个版本 — 即，使用不同版本的应用程序编写的文件 — 您可以使用值*VERSIONABLE_SCHEMA*作为 IMPLEMENT_SERIAL 的参数宏。 有关用法信息和示例，请参阅类 `GetObjectSchema` 的 `CArchive` 成员函数。

下面的示例演示如何为类中使用 IMPLEMENT_SERIAL `CPerson`，即派生自`CObject`:

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

一旦您有一个可序列化类，如本文所述，您可以序列化的类的对象[序列化：将对象序列化为](../mfc/serialization-serializing-an-object.md)。

## <a name="see-also"></a>请参阅

[序列化](../mfc/serialization-in-mfc.md)

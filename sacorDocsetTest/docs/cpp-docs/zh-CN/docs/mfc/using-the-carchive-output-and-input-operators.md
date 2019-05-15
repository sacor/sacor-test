---
title: 使用 CArchive &lt; &lt;并&gt;&gt;运算符
ms.date: 11/04/2016
f1_keywords:
  - CArchive
helpviewer_keywords:
  - 'objects [MFC], loading from previously stored values'
  - 'CArchive class [MFC], storing and loading objects'
  - 'CArchive class [MFC], operators'
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>使用 CArchive &lt; &lt;并&gt;&gt;运算符

`CArchive` 提供了 <\<和 >> 写入和读取简单数据类型的运算符以及`CObject`到和从一个文件。

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>若要将对象存储在通过存档文件

1. 下面的示例演示如何将对象存储在通过存档文件：

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>若要从以前存储在文件中的值加载对象

1. 下面的示例演示如何从以前存储在文件中的值加载对象：

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

通常情况下，存储和加载数据传入和传出文件通过在存档`Serialize`函数的`CObject`的派生类，您必须声明与 DECLARE_SERIALIZE 宏保持一致。 对引用`CArchive`对象传递给你`Serialize`函数。 在调用`IsLoading`的函数`CArchive`对象，以确定是否`Serialize`调用函数以从文件加载数据或存储文件的数据。

`Serialize`函数的可序列化`CObject`-派生的类通常具有以下形式：

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

上面的代码模板正是与其中一个应用程序向导创建的相同`Serialize`函数的文档 (一个类派生自`CDocument`)。 此代码模板可帮助您编写代码，这是更轻松地查看，因为存储代码和加载代码应始终为并行，如以下示例所示：

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

库定义了 **< \<** 并 **>>** 运算符`CArchive`作为第一个操作数的以下数据类型和类类型作为第二个操作数:

||||
|-|-|-|
|`CObject*`|**大小**和 `CSize`|**float**|
|**WORD**|`CString`|**点**和 `CPoint`|
|`DWORD`|**BYTE**|`RECT` 和 `CRect`|
|**Double**|**LONG**|`CTime` 和 `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  存储和加载`CObject`s 通过存档需要额外的注意事项。 有关详细信息，请参阅[存储和加载 Cobject 通过存档](../mfc/storing-and-loading-cobjects-via-an-archive.md)。

**CArchive <\<** 并 **>>** 运算符始终返回对引用`CArchive`对象，它是第一个操作数。 这使您可以链接运算符，如下图所示：

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>请参阅

[序列化：序列化对象](../mfc/serialization-serializing-an-object.md)

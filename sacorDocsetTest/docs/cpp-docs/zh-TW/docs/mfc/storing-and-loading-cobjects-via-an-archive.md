---
title: 透過封存儲存及載入 CObjects
ms.date: 11/04/2016
f1_keywords:
  - CObject
helpviewer_keywords:
  - 'CObjects [MFC], loading through archives'
  - 'CArchive class [MFC], storing and loading objects'
  - 'Serialize method, vs. CArchive operators'
  - 'CObject class [MFC], CArchive objects'
  - 'CObjects [MFC]'
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>透過封存儲存及載入 CObjects

儲存及載入`CObject`s 透過封存需要額外的考量。 在某些情況下，您應該呼叫`Serialize`函式的物件，其中`CArchive`物件是參數`Serialize`呼叫，而不是使用 **< \<** 或 **>>** 操作員`CArchive`。 要牢記在心的重要事實在於`CArchive` **>>** 運算子建構`CObject`為基礎的記憶體中`CRuntimeClass`先前寫入檔案中所儲存的保存的資訊。

因此，您是使用`CArchive` **< \<** 並 **>>** 運算子，與呼叫`Serialize`，取決於是否您*需要*載入封存檔，若要以動態方式重建物件根據先前儲存`CRuntimeClass`資訊。 使用`Serialize`函式在下列情況：

- 當還原序列化物件，會事先知道物件的確切的類別。

- 當還原序列化物件，您已為其配置記憶體。

> [!CAUTION]
>  如果您載入物件使用`Serialize`函式，您也必須儲存物件使用`Serialize`函式。 使用不會儲存`CArchive` **<<** 運算子，然後使用的負載`Serialize`函式，或使用儲存`Serialize`函式，然後將載入使用`CArchive >>`運算子。

下列範例說明的案例：

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

總而言之，如果您可序列化的類別定義內嵌`CObject`做為成員，您應該*不*使用`CArchive` **< \<** 和 **>>** 運算子，針對該物件，但應該呼叫`Serialize`函式。 此外，如果您可序列化的類別定義的指標`CObject`(或衍生自`CObject`) 做為成員，但建構這個其他物件在它自己的建構函式中，您也應該呼叫`Serialize`。

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)

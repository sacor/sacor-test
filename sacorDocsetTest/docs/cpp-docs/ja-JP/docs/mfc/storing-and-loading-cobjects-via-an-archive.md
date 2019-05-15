---
title: アーカイブを通じた CObject の格納と読み込み
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
# <a name="storing-and-loading-cobjects-via-an-archive"></a>アーカイブを通じた CObject の格納と読み込み

格納と読み込み`CObject`アーカイブを通じて追加の考慮事項が必要です。 場合によってを呼び出す必要があります、`Serialize`関数、オブジェクトの場所、`CArchive`オブジェクトがパラメーターの`Serialize`を使用してではなく、呼び出し、 **< \<** または **>>** の演算子、`CArchive`します。 留意する重要な実際のところ、 `CArchive` **>>** 演算子コンストラクト、`CObject`に基づくインメモリ`CRuntimeClass`以前格納アーカイブでファイルに書き込まれた情報。

使用するかどうか、そのため、 `CArchive` **< \<** と **>>** 演算子を呼び出すと`Serialize`、かどうかに依存する*必要*オブジェクトを動的に再構築する読み込みアーカイブに基づいて以前に保存された`CRuntimeClass`情報。 使用して、`Serialize`関数は、次の場合。

- オブジェクトを逆シリアル化するときに事前にわかっているオブジェクトの正確なクラスです。

- オブジェクトを逆シリアル化するときにそれに割り当てられたメモリが既にあります。

> [!CAUTION]
>  使用してオブジェクトを読み込む場合、`Serialize`関数を使用してオブジェクトを格納する必要がありますも、`Serialize`関数。 使用して保存しないで、 `CArchive` **<<** 演算子と、ロードを使用して、`Serialize`関数、または保存を使用して、`Serialize`関数を使用して、ロード`CArchive >>`演算子。

次の例に示します。

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

要約すると、埋め込まれたシリアル化可能なクラスが定義されている場合に`CObject`メンバーは、する必要があります*いない*を使用して、 `CArchive` **< \<** と **>>** 演算子、そのオブジェクトを呼び出す必要があります、`Serialize`関数を使用します。 また、シリアル化可能なクラスがへのポインターを定義する場合、 `CObject` (から派生したオブジェクトまたは`CObject`) が、メンバー、コンストラクトとして独自のコンス トラクターでこの他のオブジェクトを呼び出す必要がありますも`Serialize`します。

## <a name="see-also"></a>関連項目

[シリアル化: オブジェクトのシリアル化](../mfc/serialization-serializing-an-object.md)

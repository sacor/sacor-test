---
title: CArchive を使用して&lt;&lt;と&gt;&gt;演算子
ms.date: 11/04/2016
f1_keywords:
  - CArchive
helpviewer_keywords:
  - 'objects [MFC], loading from previously stored values'
  - 'CArchive class [MFC], storing and loading objects'
  - 'CArchive class [MFC], operators'
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>CArchive を使用して&lt;&lt;と&gt;&gt;演算子

`CArchive` <\<と >> 単純なデータ型を読み取ったりするための演算子だけでなく`CObject`ファイルからの秒。

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>アーカイブを通じたファイルにオブジェクトを格納するには

1. 次の例では、アーカイブを通じたファイルにオブジェクトを格納する方法を示します。

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>ファイルに保存された値からオブジェクトを読み込む

1. 次の例では、ファイルに保存された値からオブジェクトを読み込む方法を示します。

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

通常、格納されとでアーカイブを通じたファイルからデータを読み込む、`Serialize`関数の`CObject`-派生クラスで、読み込んだりマクロで宣言されている必要があります。 参照を`CArchive`にオブジェクトが渡される、`Serialize`関数。 呼び出す、`IsLoading`の関数、`CArchive`を決定するオブジェクトかどうか、`Serialize`ファイルからデータを読み込んだり、ファイルにデータを格納する関数が呼び出されました。

`Serialize`のシリアル化可能な関数`CObject`の派生クラスは、次の形式を通常は。

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

上記のコード テンプレートはまったく AppWizard の作成の 1 つとして同じ、`Serialize`ドキュメントの機能 (から派生したクラス`CDocument`)。 このテンプレート コードでは、ファイルを格納するコードと読み込みコードは常に次の例のように、並列ためを確認する簡単なコードを記述できます。

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

ライブラリ定義 **< \<** と **>>** 演算子の`CArchive`最初のオペランドと、次のデータ型と 2 番目のオペランドとしてクラス型として:

||||
|-|-|-|
|`CObject*`|**サイズ**と `CSize`|**float**|
|**WORD**|`CString`|**ポイント**と `CPoint`|
|`DWORD`|**BYTE**|`RECT` および `CRect`|
|**Double**|**LONG**|`CTime` および `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  格納と読み込み`CObject`アーカイブを通じて追加の考慮事項が必要です。 詳細については、次を参照してください。[の保存とアーカイブを通じた Cobject の読み込み](../mfc/storing-and-loading-cobjects-via-an-archive.md)します。

**CArchive <\<** と **>>** 演算子が常にへの参照を返す、`CArchive`最初のオペランドとなるオブジェクト。 これによりに、演算子のチェーンに次の図に。

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>関連項目

[シリアル化: オブジェクトのシリアル化](../mfc/serialization-serializing-an-object.md)

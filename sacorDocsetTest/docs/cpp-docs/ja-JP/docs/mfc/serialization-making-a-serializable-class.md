---
title: 'シリアル化:シリアル化可能なクラスの作成'
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
# <a name="serialization-making-a-serializable-class"></a>シリアル化:シリアル化可能なクラスの作成

シリアル化可能なクラスを作成するには、5 つの主な手順が必要です。 以下に示すされ次のセクションで説明します。

1. [CObject からクラスを派生](#_core_deriving_your_class_from_cobject)(または一部から派生するクラスから`CObject`)。

1. [メンバー関数をオーバーライドする](#_core_overriding_the_serialize_member_function)します。

1. [DECLARE_SERIAL マクロを使用して](#_core_using_the_declare_serial_macro)クラス宣言でします。

1. [引数を受け取らないコンス トラクターを定義する](#_core_defining_a_constructor_with_no_arguments)します。

1. [IMPLEMENT_SERIAL マクロを使用して、実装ファイル](#_core_using_the_implement_serial_macro_in_the_implementation_file)クラス。

呼び出す場合`Serialize`直接なくを通じて、>> と << の演算子[CArchive](../mfc/reference/carchive-class.md)、最後の 3 つの手順はシリアル化は必要ありません。

##  <a name="_core_deriving_your_class_from_cobject"></a> CObject からクラスの派生

基本的なシリアル化と機能が定義されて、`CObject`クラス。 クラスから派生することによって`CObject`(またはから派生したクラスから`CObject`) クラスの次の宣言に示すように、 `CPerson`、シリアル化プロトコルとの機能にアクセスできる`CObject`します。

##  <a name="_core_overriding_the_serialize_member_function"></a> オーバーライド、メンバー関数をシリアル化

`Serialize`で定義されているメンバー関数、`CObject`クラス、オブジェクトの現在の状態をキャプチャするために必要なデータを実際にシリアル化します。 `Serialize`関数には、`CArchive`オブジェクト データを読み書きするために使用する引数。 [CArchive](../mfc/reference/carchive-class.md)オブジェクトがメンバー関数の場合、`IsStoring`を示すかどうか`Serialize`が (データの書き込み) を格納するか、読み込み (データの読み取り)。 結果を使用して`IsStoring`をガイドでは、いずれかのデータを挿入するオブジェクトので、`CArchive`挿入演算子を持つオブジェクト ( **<\<** ) または抽出演算子 (でデータを抽出 **>>** ).

派生したクラスを検討してください。`CObject`を型の、新しい 2 つのメンバー変数を`CString`と**WORD**します。 変数と宣言には、オーバーライドされた、次のクラス宣言のフラグメントは、新しいメンバーを示しています`Serialize`メンバー関数。

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>メンバー関数をオーバーライドするには

1. 基底クラスのバージョンを呼び出す`Serialize`オブジェクトの継承された部分がシリアル化されることを確認します。

1. 挿入またはクラスに固有のメンバー変数を抽出します。

   挿入と抽出演算子は、データを読み書きするアーカイブ クラスと対話します。 次の例は、実装する方法を示しています。`Serialize`の、`CPerson`上で宣言されたクラス。

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

使用することも、[読み書きするとき](../mfc/reference/carchive-class.md#read)と[CArchive::Write](../mfc/reference/carchive-class.md#write)大量の型指定されていないデータを読み書きするメンバー関数。

##  <a name="_core_using_the_declare_serial_macro"></a> DECLARE_SERIAL マクロを使用します。

次のように、シリアル化をサポートするクラスの宣言で DECLARE_SERIAL マクロが必要です。

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

##  <a name="_core_defining_a_constructor_with_no_arguments"></a> 引数なしのコンス トラクターを定義します。

MFC では、(ディスクから読み込まれて) 逆シリアル化されたオブジェクトを再作成するときに既定のコンス トラクターが必要です。 逆シリアル化プロセスは、オブジェクトを再作成に必要な値を持つすべてのメンバー変数を入力します。

このコンス トラクターは、パブリック、プロテクト、またはプライベートに宣言できます。 保護されたまたはプライベートするように場合、これはのみ関数を使用して、シリアル化かどうかを確認するのに役立ちます。 コンス トラクターは、必要に応じて削除することを許可する状態オブジェクトを配置する必要があります。

> [!NOTE]
>  ストリームのマクロを使用するクラスに引数なしのコンス トラクターを定義することを忘れてしまった場合 IMPLEMENT_SERIAL マクロが使用されている行に「既定コンス トラクターがなく利用可能な」コンパイラの警告が表示されます。

##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> IMPLEMENT_SERIAL マクロを使用して、実装ファイル

IMPLEMENT_SERIAL マクロを使用して必要なときにクラスを派生する、シリアル化可能なから、さまざまな関数を定義する`CObject`します。 このマクロを使用して、実装ファイル (します。CPP) クラス。 マクロの最初の 2 つの引数は、クラスの名前とその直接の基本クラスの名前です。

このマクロの 3 番目の引数は、スキーマの数です。 スキーマの数は、基本的に、クラスのオブジェクトのバージョン番号です。 スキーマの数を 0 以上の整数を使用します。 (と混同しないでくださいデータベース用語でこのスキーマの数。)

MFC のシリアル化コードは、メモリにオブジェクトを読み取るときに、スキーマの番号を確認します。 ディスク上のオブジェクトのスキーマの数がメモリ内のクラスのスキーマの数が一致しない場合、ライブラリがスローされます、`CArchiveException`プログラムのオブジェクトの正しくないバージョンの読み取りを防止します。

場合は、`Serialize`メンバー関数は複数のバージョンを読み取ることができる、アプリケーションのさまざまなバージョンで書き込まれるファイルは、-値を使用することができます*VERSIONABLE_SCHEMA* IMPLEMENT_SERIAL への引数としてマクロ。 使用状況に関する情報と例では、次を参照してください。、`GetObjectSchema`クラスのメンバー関数`CArchive`します。

次の例は、クラスの IMPLEMENT_SERIAL を使用する方法を示します`CPerson`、つまりから派生した`CObject`:

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

シリアル化可能なクラスを作成したら、この記事で説明したように、クラスのオブジェクトがシリアル化できる[シリアル化します。オブジェクトのシリアル化](../mfc/serialization-serializing-an-object.md)します。

## <a name="see-also"></a>関連項目

[シリアル化](../mfc/serialization-in-mfc.md)

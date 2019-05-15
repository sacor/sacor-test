---
title: 規則セットを使用した実行対象の C++ 規則の指定
ms.date: 04/28/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
  - cplusplus
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>規則セットを使用して、実行対象の C++ 規則の指定

Visual Studio で作成し、カスタムの変更*ルール セット*コード分析に関連付けられている特定のプロジェクトのニーズを満たします。 既定の規則セットが格納されている`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`します。

**Visual Studio 2017 バージョン 15.7 以降**任意のテキストを使用してカスタム規則セット エディターを作成し、これらを使用しているシステムを構築するものに関係なくコマンド ライン ビルドで適用することができます。 詳細については、次を参照してください。 [/analyze: ruleset](/cpp/build/reference/analyze-code-analysis)します。

Visual Studio でカスタム C++ 規則を作成するには、は、C と C++ プロジェクトが Visual Studio IDE で開く必要があります。 規則セット エディターで、標準の規則セットを開くと、追加または特定の規則を削除し、必要に応じて変更コード分析ルールに違反したことを決定するときに発生するアクション。

新規のカスタム規則セットを作成する場合は、新しいファイル名を使用して保存します。 作成したカスタム規則セットは、自動的にプロジェクトに割り当てられます。

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>既存の 1 つの規則セットからカスタム規則を作成するには

1. ソリューション エクスプ ローラーで プロジェクトのショートカット メニューを開き、**プロパティ**します。

2. **プロパティ** タブで、選択**コード分析**します。

3. **ルール セットの**ドロップダウン リストで、次のいずれかの操作を行います。

   - 規則セットをカスタマイズするを選択します。

     \- または -

   - 選択 **\<[参照...] >** を既存の規則セットを指定されていないリスト。

4. 選択**オープン**ルール セット エディターで、ルールを表示します。

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>規則セット エディターで規則セットを変更するには

- ルール セットの表示名を変更する、**ビュー**  メニューの 選択**プロパティ ウィンドウ**します。 表示名を入力、**名前**ボックス。 表示名には、ファイル名と異なる名前を指定できます。

- グループ内のすべての規則をカスタム規則セットに追加するには、グループのチェック ボックスをオンにします。 グループ内のすべての規則を削除するには、チェック ボックスをオフにします。

- 特定の規則をカスタム規則セットに追加するには、その規則のチェック ボックスをオンにします。 規則セットから規則を削除するには、チェック ボックスをオフにします。

- コード分析のルールに違反したときの動作を変更するには、選択、**アクション**規則のフィールドし、次の値のいずれかを選択します。

     **警告**-警告が生成されます。

     **エラー** -エラーが生成されます。

     **None** -ルールを無効にします。 このアクションは、規則セットから規則を削除するのと同じです。

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>規則セット エディターのツール バーを使用して、規則セット エディターに表示されるフィールドのグループ化、フィルター処理、または変更を行うには

- すべてのグループの規則を展開するには、選択**すべて展開**します。

- すべてのグループの規則を折りたたむには、次のように選択します。**すべて折りたたみ**します。

- ルールは別にグループ化フィールドを変更するからフィールドを選択、 **Group By**一覧。 グループに属していないルールを表示するには、次のように選択します。  **\<None >** します。

- 追加または列のルールでフィールドを削除、選択**列オプション**します。

- 現在のソリューションに適用されない規則を非表示にするには、 **、現在のソリューションに適用されない規則を非表示に**します。

- 表示とエラーのアクションが割り当てられているルールを非表示の切り替え、次のように選択します。**コード分析エラーを生成するルールを表示する**します。

- 表示と警告の動作が割り当てられているルールを非表示の切り替え、次のように選択します。**コード分析の警告を生成するルールを表示する**します。

- 表示と割り当てられているルールを非表示を切り替える、 **None**アクション、選択**が有効になっていないルールが表示されます**します。

- 追加または Microsoft の現在のルール セットの既定の規則セットを削除、選択**子規則セットの追加または削除する**します。

## <a name="to-create-a-rule-set-in-a-text-editor"></a>テキスト エディターで設定するルールを作成するには

テキスト エディターでカスタム規則セットを作成での任意の場所に格納できます、`.ruleset`拡張機能で適用し、 [/analyze: ruleset](/cpp/build/reference/analyze-code-analysis)コンパイラ オプション。

次の例では、基本的なルール セットの開始点として使用できるファイルを示しています。

::: moniker range="vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

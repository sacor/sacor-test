---
title: Office ソリューションのエラーをトラブルシューティングします。
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
  - VST.Project.DesignerDisabled
  - VST.Designer.CannotActivate
  - VST.Project.ExcelBusy
  - VST.SelectDocWizard.AlreadyCustomized
  - VST.SelectDocWizard.DocPath
  - VST.Project.CannotOpen
  - VST.Designer.ErrorsOccurred
dev_langs:
  - VB
  - CSharp
helpviewer_keywords:
  - 'troubleshooting [Office development in Visual Studio]'
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
  - office
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Office ソリューションのエラーをトラブルシューティングします。
  Visual Studio で Office ソリューションを開発する際、次のタスクを実行するときに問題が発生する場合があります。

- [作成、アップグレード、およびプロジェクトを開く](#creating)

- [デザイナーを使用します。](#designers)

- [コードの記述](#code)

- [プロジェクトをビルドする](#building)

- [プロジェクトをデバッグします。](#debugging)

## <a name="creating"></a> 作成、アップグレード、およびプロジェクトを開く
 Office プロジェクトを作成、または開くときに、次のエラーが発生する場合があります。

### <a name="the-project-cannot-be-created"></a>プロジェクトを作成することはできません。
 Office プロジェクトを作成または開こうとするときにエラーが発生しましたが、Visual Studio では、原因を特定するのに十分な情報がありませんでした。 プロジェクトを閉じ、Visual Studio を終了してから、再起動してみてください。

 ドキュメント レベルのプロジェクトを作成しようとしている場合、新しいプロジェクトのドキュメントと同じ名前を持つ別のドキュメントが Excel または Word で開いている可能性があります。 Excel または Word の他のすべてのインスタンスが閉じられていることを確認してください。

### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>コントロールのプロパティは、既存のプロジェクトのドキュメントに基づく新しいプロジェクトを作成するときに失われます
 既存のプロジェクトのドキュメントに基づいて新しい Office プロジェクトを作成する場合、既存のドキュメントにあるコントロールのプロパティが新しいプロジェクトにコピーされることはありません。 すべての既存のコントロールのプロパティを手動で設定する必要があります。 または、新しいプロジェクトを作成する代わりに既存のプロジェクトのコピーを作成するか、(デザイナーで) 新しいソリューションに既存のプロジェクトを読み込んだうえで、既存のドキュメントから新しいドキュメントにコントロールをコピーして貼り付ければ、コントロールのプロパティを保持できます。

### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>既存のブックに基づいて Excel ブック プロジェクトを作成するときのエラー
 既存のブックに基づいて新しい Excel ブック プロジェクトを作成する場合は、次のエラーの組み合わせを参照してください可能性があります。

 Excel から。"プライバシーに関する注意。このドキュメントには、マクロ、ActiveX コントロール、XML 拡張パック情報、または Web コンポーネントが含まれています。 これらには、ドキュメント検査で削除できない個人情報が含まれている場合があります。"

 Visual Studio から。「デザイナーは、正しく読み込めませんでした」。

 これらのエラーは、ドキュメント検査を使用して削除された個人情報があったブックに基づいてプロジェクトを作成しようとしたときに、発生する可能性があります。 このエラーを回避するには、プロジェクトを作成する前に次の手順を実行します。

1. Excel でブックを開きます。

2. Excel でセキュリティ センターを開きます。

3. **プライバシー オプション**] タブで [、**でファイルのプロパティから個人情報を削除する保存**チェック ボックスをオンします。

4. ブックを保存し、Excel を終了します。

### <a name="cannot-open-a-project-after-migration"></a>移行後に、プロジェクトを開くことができません。
 Office のソリューションを Microsoft Office 2010 に移行後は、2007 Microsoft Office システムのみがインストールされている開発用コンピューターでは、プロジェクトを開くことができません。 次のエラー メッセージが表示される可能性があります。

 "ソリューション内の 1 つ以上のプロジェクトが正しく読み込まれていません。 詳細については、出力ウィンドウを確認してください。"

 "このプロジェクト タイプに関連付けられてるアプリケーションがこのコンピューターにインストールされていないため、プロジェクトを作成できません。 このプロジェクト タイプに関連付けられている Microsoft Office アプリケーションをインストールする必要があります。"

 この問題を解決するには、編集、 *.vbproj*または *.csproj*ファイル。 Word プロジェクトの場合は、HostPackage="{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" を、HostPackage="{6CE98B71-D55A-4305-87A8-0D6E368D9600}" に置き換えます。 Excel プロジェクトの場合は、HostPackage="{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" を、HostPackage="{825100CF-0BA7-47EA-A084-DCF3308DAF74}" に置き換えます。 Outlook プロジェクトの場合は、HostPackage="{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" を HostPackage="{20A848B8-E01F-4801-962E-25DB0FF57389}" に置き換えます。

 または、Microsoft Office 2010 が既にインストールされている開発用コンピューターでのみ、移行後のプロジェクトを開くようにします。

### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Windows フォーム コントロールを含むアップグレード済みの Office 2003 ドキュメント レベル プロジェクトでのエラー
 Microsoft Office 2003 のドキュメント レベルのプロジェクトをアップグレードする、ドキュメントには、Windows フォーム コントロールが含まれている場合は、アップグレードされたプロジェクトがコンパイルまたは実行時エラーにあります。 この問題を回避するには、プロジェクトをアップグレードする前に、Visual Studio 2005 Tools for Office Second Edition Runtime を開発用コンピューターにインストールします。 このバージョンのランタイムは、Microsoft ダウンロード センターの「 [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612)」から再頒布可能パッケージとしてダウンロードできます。

 Visual Studio 2005 Tools for Office Second Edition Runtime は、他の Office ソリューションで使用されていない場合、プロジェクトのアップグレードが完了した後に開発用コンピューターからアンインストールできます。

## <a name="designers"></a> デザイナーを使用します。
 ドキュメント レベルのプロジェクトでドキュメント、ブック、またはワークシート デザイナーを使用する場合に、次のエラーが発生する可能性があります。

### <a name="designer-failed-to-load-correctly"></a>デザイナーが正しく読み込めませんでした。
 Visual Studio は次の場合、デザイナーを開くことができません。

- Excel または Word が既に開いており、モーダル ダイアログ ボックスを表示している。 デザイナーを開くには、Excel または Word でモーダル ダイアログ ボックスが開いていないかを確認し、開いているモーダル ダイアログ ボックスがあればそれを閉じます。 開いているモーダル ダイアログ ボックスがない場合は、Excel または Word が応答する前に、何か別のアクションが必要な可能性があります。

- プロジェクトは現在デバッグ中である。 デザイナーを開くには、デバッグを停止または終了します。

- 開発用コンピューターにインストールされている Excel の VSTO アドインにより、Excel の開始時にダイアログ ボックスが表示される。 ドキュメント レベルの Excel プロジェクトを作成するには、まず、VSTO アドインを無効にする必要があります。

### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>コントロールが文書またはワークシートに黒い長方形として表示されます。
 ドキュメントやワークシートでコントロールをグループ化すると、以降は Visual Studio がそのコントロールを認識しなくなります。 グループ化されたコントロールではアクセスできない、**プロパティ**ウィンドウと、ドキュメントまたはワークシートに黒い長方形として表示されます。 コントロールの機能を復元するには、グループ化を解除する必要があります。

### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Word テンプレート上のコントロールが Visual Studio に表示されません。
 Visual Studio デザイナーで Word テンプレートを開くと、テンプレート上のテキストの範囲内にないコントロールが表示されない場合があります。 これは、Visual Studio で Word テンプレートを開くため**標準**ビュー。 コントロールを表示する をクリックして、**ビュー**メニューで、 **Microsoft Office Word View**  をクリックし、**印刷レイアウト**します。

### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>クリップアートの挿入コマンドは、Visual Studio デザイナーではありません。
 Excel または Word が Visual Studio デザイナーで開いているときにクリックすると、**クリップアート**のボタンでは、**図**、リボン タブが開かない場合は、**クリップアート**作業ウィンドウ。 クリップアートを追加するには、ブックまたはメイン プロジェクト フォルダー内にあるドキュメントのコピーを開く必要があります (内にあるコピーではなく、 *\bin*フォルダー)、Visual Studio の外部で、クリップアートを追加して、ブックまたはドキュメントに保存します。

## <a name="code"></a> コードを記述します。
 Office プロジェクトでコードを作成するときに、次のエラーが発生する場合があります。

### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Office オブジェクトの一部のイベントは、C を使用する場合はアクセスできません。\#
 場合によっては、Visual C# プロジェクトで Office プライマリ相互運用機能アセンブリ (PIA) 型のインスタンスの特定のイベントにアクセスしようとすると、次のようなコンパイラ エラーが表示される場合があります。

 "'Microsoft.Office.Interop.Excel._Application.NewWorkbook' と 'Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook' の間にあいまいさがあります"

 このエラーは、オブジェクトの別のプロパティやメソッドと同じ名前を持つイベントにアクセスしようとしていることを意味します。 イベントにアクセスするにはオブジェクトにキャストする必要があります、*イベント インターフェイス*します。

 イベントを持つ Office PIA の型は、すべてのプロパティとメソッドを持つコア インターフェイスと、オブジェクトによって公開されるイベントを含むイベント インターフェイスの、2 つのインターフェイスを実装します。 これらのイベント インターフェイスを使用して、名前付け規則*objectname*イベント*n*_Event など<xref:Microsoft.Office.Interop.Excel.AppEvents_Event>と<xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event>します。 オブジェクト上で検出できることが予想されるイベントにアクセスできない場合は、オブジェクトをそのイベント インターフェイスにキャストします。

 たとえば、<xref:Microsoft.Office.Interop.Excel.Application> オブジェクトが、<xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> イベントおよび <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> プロパティを持つとします。 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> イベントを処理するには、<xref:Microsoft.Office.Interop.Excel.Application> を <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> インターフェイスにキャストします。 Excel のドキュメント レベルのプロジェクトでこれを実行する方法を、次のコード例に示します。

 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]

 Office Pia のイベント インターフェイスの詳細については、次を参照してください。 [Office プライマリ相互運用機能アセンブリのクラスおよびインターフェイスの概要](/previous-versions/office/office-12//ms247299(v=office.12))します。

### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-includenetv40shortsharepointincludesnet-v40-short-mdmd-or-the-includenetv45vstoincludesnet-v45-mdmd"></a>できません Office PIA のリファレンス内のクラス プロジェクトを対象とする、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とするプロジェクトでは、Office PIA で定義されているクラスを参照するコードは、既定ではコンパイルされません。 Pia のクラスは、名前付け規則を使用して*objectname*クラスなど、<xref:Microsoft.Office.Interop.Word.DocumentClass>と<xref:Microsoft.Office.Interop.Excel.WorkbookClass>します。 たとえば、Word の VSTO アドイン プロジェクトの次のコードはコンパイルされません。

```vb
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;
```

 このコードを実行すると、次のようなコンパイル エラーが発生します。

- Visual Basic: 「クラス 'DocumentClass' への参照は許可されません、アセンブリが NO-PIA モードを使用してリンクされている場合。」

- Visual C#:"相互運用機能型 'microsoft.office.interop.word.documentclass' を埋め込むことができません。 代わりに適用可能なインターフェイスを使用してください。"

  このエラーを解決するには、対応するインターフェイスを代わりに参照するようにコードを変更します。 たとえば、<xref:Microsoft.Office.Interop.Word.DocumentClass> オブジェクトを参照するのではなく、代わりに <xref:Microsoft.Office.Interop.Word.Document> インターフェイスを参照します。

```vb
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;
```

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とするプロジェクトは、既定で自動的に Office PIA のすべての相互運用機能型を埋め込みます。 このコンパイル エラーは、埋め込まれた相互運用機能型の機能は、クラスでなくインターフェイスでのみ機能するために発生します。 Office Pia のインターフェイスとクラスの詳細については、次を参照してください。 [Office プライマリ相互運用機能アセンブリのクラスおよびインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=189592)します。 Office プロジェクトで埋め込まれた相互運用機能型の機能の詳細については、次を参照してください。[デザイン Office ソリューションの作成と](../vsto/designing-and-creating-office-solutions.md)します。

### <a name="references-to-office-classes-are-not-recognized"></a>Office クラスへの参照は認識されません。
 など、複数の名前空間の例では、アプリケーションの一部のクラス名<xref:Microsoft.Office.Interop.Word>と<xref:System.Windows.Forms>します。 このため、 **Imports**/**を使用して**プロジェクト テンプレートの上部にあるステートメントには、修飾定数などの短縮形が含まれています。

 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]

 この方法では、 **Imports**/**を使用して**ステートメントでは、たとえば、Word または Excel の修飾子を持つ Office クラスへの参照を区別することが必要です。

 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]

 非修飾の宣言を使用した場合は、次のようにエラーが発生します。

 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]

 Word または Excel の名前空間をインポートし、その内部のすべてのクラスにアクセスできる場合でも、名前空間のあいまいさを削除するには、Word または Excel のすべての型を完全に修飾する必要があります。

## <a name="building"></a> プロジェクトをビルドする
 Office プロジェクトをビルドするときに、次のエラーが発生する場合があります。

### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>制限されたアクセス許可を持つドキュメントに基づくドキュメント レベルのプロジェクトをビルドすることはできません。
 Visual Studio は、ドキュメントのアクセス許可が制限されている場合、ドキュメント レベルのプロジェクトをビルドできません。 プロジェクトには、アクセス許可が制限されているドキュメントが含まれている場合は、プロジェクトはコンパイルされませんで次のメッセージが表示されます、**エラー一覧**ウィンドウ。

 "カスタマイズを追加できませんでした。"

 アクセス許可が制限されているドキュメントを含める場合は、ソリューションを開発およびビルドする間は、制限のないドキュメントを使用します。 次に、ソリューションを発行した後に、発行場所でアクセス許可の制限をドキュメントに適用します。

### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>NamedRange コントロールを削除した後、コンパイラ エラーが発生します。
 デザイナーで作業中のワークシートではないワークシートから <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを削除した場合、自動生成されたコードがプロジェクトから削除されず、コンパイラ エラーが発生することがあります。 コードが確実に削除されるようにするには、必ず、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを含むワークシートを選択し作業中のワークシートにしてからコントロールを削除します。 コントロールを削除するときに、自動生成されたコードが削除されない場合は、ワークシートをアクティブ化して、ワークシートが変更済みとしてマークされるように変更を加えれば、デザイナーによりコードが削除されます。 プロジェクトをリビルドするときに、コードが削除されます。

## <a name="debugging"></a> プロジェクトをデバッグします。
 Office プロジェクトをデバッグするときに、次のエラーが発生する場合があります。

### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>発行開発用コンピューターでソリューションをインストールするをアンインストールするプロンプトが表示されます。
 Office ソリューションをデバッグするときに、次のエラー メッセージが表示されることがあります。

 "現在他のバージョンがインストールされており、この場所からアップグレードすることはできないため、このカスタマイズをインストールすることはできません。"

 このエラーは、開発用コンピューターで以前に Office ソリューションを発行し、インストールしたことを示しています。 メッセージが表示されないようにには、ソリューションをデバッグする前に、コンピューターにインストールされているプログラムの一覧からソリューションをアンインストールします。 または、開発コンピューターに別のユーザー アカウントを作成し、発行済みソリューションのインストールをテストすることもできます。

### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>UNC ネットワークの場所に作成されたドキュメント レベルのプロジェクトが Visual Studio から実行しないでください。
 UNC ネットワークの場所で Excel または  Word のドキュメント レベルのプロジェクトを作成する場合は、Excel または Word の [信頼できる場所] リストに、そのドキュメントの場所を追加する必要があります。 そうしないと、Visual Studio でプロジェクトの実行またはデバッグを試行するときに、カスタマイズが読み込まれません。 信頼できる場所の詳細については、次を参照してください。[ドキュメントに信頼を付与](../vsto/granting-trust-to-documents.md)します。

### <a name="threads-are-not-stopped-correctly-after-debugging"></a>デバッグ後にスレッドが正しく停止されません。
 Visual Studio の Office プロジェクトは、デバッガーがプログラムを正しく終了できるように、スレッドの名前付け規則に従うようになっています。 ソリューション内にスレッドを作成する場合、デバッグの停止時にこれらのスレッドが確実に正常に処理されるよう、各スレッドに VSTA _  というプレフィックスを付ける必要があります。 たとえば、設定することがあります、`Name`ネットワーク イベントを待機するスレッドのプロパティ**VSTA_NetworkListener**します。

### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>実行または開発用コンピューターで Office ソリューションをデバッグできません。
 開発用コンピューターで Office プロジェクトを実行または開発できない場合に、次のエラー メッセージが表示されることがあります。

 "アプリケーション ドメインが作成されなかったため、カスタマイズは読み込まれませんでした。"

 Visual Studio は、Office ソリューションを読み込む前に、.NET Framework アセンブリ ローダーである Fusion を使用してアセンブリをキャッシュします。 Visual Studio が Fusion キャッシュへ書き込めることを確認し、もう一度やり直してください。 詳細については、次を参照してください。[アセンブリのシャドウ コピー](/dotnet/framework/app-domains/shadow-copy-assemblies)します。

### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>エディット コンティニュを使用した後、ドキュメント レベルのプロジェクトでデバッガーを停止するとエラー
 使用する場合**編集**と**続行**場合、プロジェクトが中断モード中には、Excel または Word のドキュメント レベルのプロジェクトでコードを変更するには、次のエラー メッセージとダイアログ ボックスが表示する場合があります。その後、デバッガーを停止します。

 "このプロセスを現在の状態で終了すると、データを消失したりシステムが不安定になったりするなど、予期しない結果になる場合があります。" 

 クリックするかどうか**はい**または**いいえ** ダイアログ ボックスで、Visual Studio は Excel または Word プロセスを終了し、デバッガーを停止します。 このダイアログ ボックスを表示せずにプロジェクトのデバッグを停止するには、Visual Studio のデバッガを停止するのではなく、直接、Excel または Word を終了します。

## <a name="see-also"></a>関連項目
- [Office ソリューションをトラブルシューティングします。](../vsto/troubleshooting-office-solutions.md)
- [Office ソリューションのセキュリティをトラブルシューティングします。](../vsto/troubleshooting-office-solution-security.md)
- [Office ソリューションのデプロイをトラブルシューティングします。](../vsto/troubleshooting-office-solution-deployment.md)

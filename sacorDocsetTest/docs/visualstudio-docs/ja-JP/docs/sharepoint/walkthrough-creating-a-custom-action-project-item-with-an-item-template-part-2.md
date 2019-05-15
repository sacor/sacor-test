---
title: 'チュートリアル: 項目テンプレートを使用したカスタム動作プロジェクト項目の作成、パート 2 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
  - 'project items [SharePoint development in Visual Studio], creating template wizards'
  - 'SharePoint project items, creating template wizards'
  - 'SharePoint development in Visual Studio, defining new project item types'
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
  - office
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>チュートリアル: 項目テンプレート、第 2 部でのカスタム動作プロジェクト項目を作成します。
  カスタム SharePoint プロジェクト項目の種類を定義し、Visual Studio で項目テンプレートに関連付ける、テンプレートのウィザードを提供する可能性がありますもします。 ウィザードを使用すると、プロジェクトにプロジェクト項目の新しいインスタンスを追加するのにテンプレートを使用するときに、ユーザーから情報を収集します。 収集した情報を使用して、プロジェクト項目を初期化できます。

 このチュートリアルでは、」に示したカスタム動作プロジェクト項目に、ウィザードを追加[チュートリアル。カスタム動作プロジェクト項目を作成、項目テンプレート、第 1 部に](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)します。 ウィザードが (その場所や、エンドユーザーが選択するときの移動先 URL) などのカスタム アクションに関する情報を収集するときに、ユーザーがカスタム動作プロジェクト項目を SharePoint プロジェクトに追加すると、この情報を追加します、 *Elements.xml*で新しいプロジェクト項目ファイル。

 このチュートリアルでは、次のタスクについて説明します。

- カスタム SharePoint プロジェクト項目の種類の項目テンプレートに関連付けられているウィザードを作成します。

- カスタム ウィザードの Visual Studio での SharePoint プロジェクト項目用の組み込みウィザードのような UI を定義します。

- 置き換え可能パラメーターを使用して、ウィザードで収集したデータで SharePoint プロジェクト ファイルを初期化します。

- ウィザードをデバッグおよびテストします。

> [!NOTE]
> サンプルをダウンロードする[Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities)ワークフローのカスタム アクティビティを作成する方法を示すです。

## <a name="prerequisites"></a>必須コンポーネント
 このチュートリアルを実行する必要があります最初、CustomActionProjectItem ソリューション実行して作成した[チュートリアル。カスタム動作プロジェクト項目を作成、項目テンプレート、第 1 部に](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)します。

 また、このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。

- サポート対象エディションの Windows、SharePoint、Visual Studio。

- Visual Studio SDK。 このチュートリアルでは、 **VSIX プロジェクト**sdk プロジェクト アイテムを配置するための VSIX パッケージを作成するテンプレート。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)します。

  次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。

- Visual Studio のプロジェクトおよび項目テンプレート用のウィザード。 詳細については、「[方法 :プロジェクト テンプレートにウィザードを使用して](../extensibility/how-to-use-wizards-with-project-templates.md)と<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>インターフェイス。

- SharePoint のカスタム動作。 詳細については、次を参照してください。[カスタム アクション](http://go.microsoft.com/fwlink/?LinkId=177800)します。

## <a name="create-the-wizard-project"></a>ウィザード プロジェクトを作成します。
 このチュートリアルを完了する、CustomActionProjectItem ソリューションで作成したプロジェクトを追加する必要があります[チュートリアル。カスタム動作プロジェクト項目を作成、項目テンプレート、第 1 部に](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)します。 このプロジェクトで、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装し、ウィザードの UI を定義します。

#### <a name="to-create-the-wizard-project"></a>ウィザード プロジェクトを作成するには

1. Visual Studio で、CustomActionProjectItem ソリューションを開く

2. **ソリューション エクスプ ローラー**、ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。

3. **新しいプロジェクト** ダイアログ ボックスで、 **Visual C#** または **Visual Basic**ノードを展開し、**Windows**ノードを選択します。

4. 上部にある、**新しいプロジェクト** ダイアログ ボックスで、ことを確認します **.NET Framework 4.5** .NET Framework のバージョンの一覧でを選択します。

5. 選択、 **WPF ユーザー コントロール ライブラリ**プロジェクト テンプレート、プロジェクトの名前**ItemTemplateWizard**、選択し、 **OK**ボタン。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **ItemTemplateWizard**プロジェクトがソリューションにします。

6. プロジェクトから UserControl1 の項目を削除します。

## <a name="configure-the-wizard-project"></a>ウィザード プロジェクトを構成します。
 ウィザードを作成する前に、Windows Presentation Foundation (WPF) ウィンドウ、コード ファイル、およびアセンブリ参照をプロジェクトを追加する必要があります。

#### <a name="to-configure-the-wizard-project"></a>ウィザード プロジェクトを構成するには

1. **ソリューション エクスプ ローラー**からショートカット メニューを開き、 **ItemTemplateWizard**プロジェクト ノードを選び、**プロパティ**します。

2. **プロジェクト デザイナー**、ターゲット フレームワークが .NET Framework 4.5 に設定されていることを確認します。

     Visual C# プロジェクトの場合は、**アプリケーション**タブでこの値を設定することができます。Visual Basic プロジェクトの場合は、**コンパイル**タブでこの値を設定できます。詳細については、「[.NET Framework のターゲット バージョンを指定する方法](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。

3. **ItemTemplateWizard**プロジェクトに、追加、**ウィンドウ (WPF)** 項目をプロジェクトにし、その項目を名前**WizardWindow**します。

4. CustomActionWizard と文字列という名前の 2 つのコード ファイルを追加します。

5. ショートカット メニューを開き、 **ItemTemplateWizard**プロジェクトを選び、**参照の追加**します。

6. **参照マネージャー - ItemTemplateWizard**ダイアログ ボックスで、**アセンブリ**ノードを選択、**拡張機能**ノード。

7. 次のアセンブリの横にあるチェック ボックスをオンにして、 **OK**ボタン。

    - EnvDTE

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. **ソリューション エクスプ ローラー**の**参照**ItemTemplateWizard プロジェクトのフォルダーを選択して、 **EnvDTE**参照。

9. **プロパティ** ウィンドウの値を変更、 **Embed Interop Types**プロパティを**False**します。

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>カスタム アクションの ID 文字列と既定の場所を定義します。
 すべてのカスタム アクションには、場所と ID で指定されている、`GroupID`と`Location`の属性、`CustomAction`内の要素、 *Elements.xml*ファイル。 この手順で ItemTemplateWizard プロジェクトでこれらの属性の有効な文字列の一部を定義します。 このチュートリアルを完了すると、これらの文字列が書き込む、 *Elements.xml*ファイルでカスタム動作プロジェクト項目と、ユーザーは、ウィザードで、場所と ID を指定します。

 わかりやすくするため、このサンプルでは、使用可能な既定の場所と Id のサブセットのみをサポートしています。 完全な一覧についてを参照してください。[カスタム アクションの既定の場所と Id](http://go.microsoft.com/fwlink/?LinkId=181964)します。

#### <a name="to-define-the-default-location-and-id-strings"></a>既定の場所と ID の文字列を定義するには

1. 開きます。

2. **ItemTemplateWizard**プロジェクトで、文字列のコード ファイル内のコードを次のコードに置き換えます。

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>ウィザードの UI を作成します。
 ウィザードの UI を定義する XAML を追加し、ウィザード内の一部のコントロール ID の文字列にバインドするコードを追加します。 作成するウィザードは、Visual Studio の SharePoint プロジェクト用の組み込みウィザードに似ています。

#### <a name="to-create-the-wizard-ui"></a>ウィザードの UI を作成するには

1. **ItemTemplateWizard**プロジェクトで、ショートカット メニューを開き、 **WizardWindow.xaml**ファイルを選び、**開く**デザイナーでウィンドウを開きます。

2. XAML ビューで、現在の XAML を次の XAML に置き換えます。 XAML では、見出しが含まれています、制御、カスタムの動作と、ウィンドウの下部にあるナビゲーション ボタンの動作を指定するための UI を定義します。

    > [!NOTE]
    > このコードを追加した後は、プロジェクトをいくつかのコンパイル エラーになります。 これらのエラーは、この後の手順でコードを追加すると解消されます。

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > この XAML で作成したウィンドウがから派生、<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>基本クラス。 Visual Studio にカスタムの WPF ダイアログ ボックスを追加すると、Visual Studio での他のダイアログ ボックスで一貫性のあるスタイルを設定して、モーダル ダイアログ ボックスで発生する可能性のある問題を回避するためには、このクラスから、ダイアログ ボックスを派生させることをお勧めします。 詳細については、次を参照してください。[モーダル ダイアログ ボックスの管理の作成と](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes)します。

3. Visual Basic プロジェクトを開発する場合は、削除、`ItemTemplateWizard`から名前空間、`WizardWindow`内のクラス名、`x:Class`の属性、`Window`要素。 この要素は XAML の 1 行目にあります。 完了したら、最初の行は、次のコードをようになります。

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. WizardWindow.xaml ファイルの分離コード ファイルでは、現在のコードを次のコードで置き換えます。

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>ウィザードを実装します。
 実装することで、ウィザードの機能を定義、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>インターフェイス。

#### <a name="to-implement-the-wizard"></a>ウィザードを実装するには

1. **ItemTemplateWizard**プロジェクトを開き、 **CustomActionWizard**コード ファイル、および、このファイルの現在のコードを次のコードに置き換えます。

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>チェックポイント
 この段階で、ウィザードに必要なすべてのコードがプロジェクトに揃ったことになります。 エラーが発生することなくプロジェクトをコンパイルできるかどうか、プロジェクトをビルドして確認してください。

#### <a name="to-build-your-project"></a>プロジェクトをビルドするには

1. メニュー バーで、 **[ビルド]**  >  **[ソリューションのビルド]** の順にクリックします。

## <a name="associate-the-wizard-with-the-item-template"></a>項目テンプレートを使用して、ウィザードを関連付ける
 ウィザードの実装をそれを関連付ける必要があります、**カスタム アクション**3 つの主な手順を完了して項目テンプレート。

1. ウィザード アセンブリに厳密な名前で署名します。

2. ウィザード アセンブリの公開キー トークンを取得します。

3. ウィザード アセンブリへの参照を追加の .vstemplate ファイルで、**カスタム アクション**項目テンプレート。

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>ウィザード アセンブリに厳密な名前で署名するには

1. **ソリューション エクスプ ローラー**からショートカット メニューを開き、 **ItemTemplateWizard**プロジェクト ノードを選び、**プロパティ**します。

2. **署名**] タブで、[、**アセンブリに署名**チェック ボックスをオンします。

3. **厳密な名前キー ファイルを選択して**一覧で、選択 **\<新規作成 >** します。

4. **厳密な名前キーの作成** ダイアログ ボックスに、オフ、名前を入力、**キーファイルをパスワードで保護する**チェック ボックスをオンにして、 **ok**ボタンをクリックします。

5. メニュー バーで、 **[ビルド]**  >  **[ソリューションのビルド]** の順にクリックします。

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>ウィザード アセンブリの公開キー トークンを取得するには

1. Visual Studio コマンド プロンプト ウィンドウで、次のコマンド実行コマンドを置き換える*PathToWizardAssembly*開発で ItemTemplateWizard、プロジェクトのビルド ItemTemplateWizard.dll アセンブリへの完全パスをコンピューター。

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     公開キー トークン、 *ItemTemplateWizard.dll*アセンブリは、Visual Studio コマンド プロンプト ウィンドウに書き込まれます。

2. Visual Studio コマンド プロンプト ウィンドウは開いたままにします。 次の手順を実行する公開キー トークンを必要があります。

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.vstemplate ファイルにウィザード アセンブリへの参照を追加するには

1. **ソリューション エクスプ ローラー**、展開、 **ItemTemplate**プロジェクト ノードを開き、 *ItemTemplate.vstemplate*ファイル。

2. ファイルの末尾の近くで、次の `WizardExtension` 要素を `</TemplateContent>` タグと `</VSTemplate>` タグの間に追加します。 置換、 *YourToken*の値、`PublicKeyToken`前の手順で取得した公開キー トークンの属性。

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     詳細については、`WizardExtension`要素を参照してください[WizardExtension 要素&#40;Visual Studio テンプレート&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates)します。

3. ファイルを保存して閉じます。

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>置き換え可能パラメーターを追加、 *Elements.xml*項目テンプレートのファイル
 いくつかの置き換え可能パラメーターを追加、 *Elements.xml* ItemTemplate プロジェクト ファイル。 これらのパラメーターは、前に定義した `PopulateReplacementDictionary` クラスの `CustomActionWizard` メソッドで初期化されます。 ユーザーは、カスタム動作プロジェクト項目をプロジェクトに追加で Visual Studio でこれらのパラメーターが自動的に置き換えられます、 *Elements.xml*ウィザードでユーザーが指定した値を持つ新しいプロジェクト項目内のファイル。

 置き換え可能パラメーターはトークンであり、先頭と末尾にはドル記号 ($) が付いています。 独自の置き換え可能パラメーターを定義するだけでなく、SharePoint プロジェクト システムを定義し、初期化するための組み込みパラメーターを使用できます。 詳細については、次を参照してください。[置き換え可能パラメーター](../sharepoint/replaceable-parameters.md)します。

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>置き換え可能パラメーターを追加する、 *Elements.xml*ファイル

1. ItemTemplate プロジェクトでの内容を置き換える、 *Elements.xml*を次の XML ファイル。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="$IdValue$"
                    GroupId="$GroupIdValue$"
                    Location="$LocationValue$"
                    Sequence="1000"
                    Title="$TitleValue$"
                    Description="$DescriptionValue$" >
        <UrlAction Url="$UrlValue$"/>
      </CustomAction>
    </Elements>
    ```

     新しい XML の値を変更する、 `Id`、 `GroupId`、 `Location`、 `Description`、および`Url`置き換え可能パラメーターの属性します。

2. ファイルを保存して閉じます。

## <a name="add-the-wizard-to-the-vsix-package"></a>VSIX パッケージをウィザードに追加します。
 VSIX プロジェクトの source.extension.vsixmanifest ファイルでは、プロジェクト項目を含む VSIX パッケージと共にデプロイされるようにウィザード プロジェクトへの参照を追加します。

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>VSIX パッケージにウィザードを追加するには

1. **ソリューション エクスプ ローラー**からショートカット メニューを開き、 **source.extension.vsixmanifest**ファイル、CustomActionProjectItem プロジェクトを選び、**開く**を開くマニフェスト エディターのファイルです。

2. マニフェスト エディターで選択、**資産**タブを選択し、**新規**ボタンをクリックします。

     **新しい資産の追加** ダイアログ ボックスが表示されます。

3. **型**一覧で、選択 **[microsoft.visualstudio.assembly]** します。

4. **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。

5. **プロジェクト**一覧で、選択**ItemTemplateWizard**、選択し、 **OK**ボタン。

6. メニュー バーで、**ビルド** > **ソリューションのビルド**、ソリューションがエラーなしでコンパイルされるかどうかを確認します。

## <a name="test-the-wizard"></a>ウィザードをテストします。
 これで、ウィザードをテストする準備ができました。 最初に、Visual Studio の実験用インスタンスで CustomActionProjectItem ソリューションのデバッグを開始します。 Visual Studio の実験用インスタンスで、SharePoint プロジェクトでカスタム動作プロジェクト項目のウィザードが、テストします。 最後に、SharePoint プロジェクトをビルドして実行し、カスタム動作が正常に機能することを確認します。

#### <a name="to-start-to-debug-the-solution"></a>ソリューションのデバッグを開始するには

1. 管理者の資格情報で Visual Studio を再起動し、CustomActionProjectItem ソリューションを開きます。

2. ItemTemplateWizard プロジェクトで CustomActionWizard コード ファイルを開くし、コードの最初の行にブレークポイントを追加し、`RunStarted`メソッド。

3. メニュー バーで、**デバッグ** > **例外**します。

4. **例外** ダイアログ ボックスに、必ず、**スローされるとき**と**user-unhandled**のチェック ボックスを**Common Language Runtime Exceptions**クリアされますが、クリックして、 **OK**ボタンをクリックします。

5. 選択してデバッグを開始、 **F5**キー、または、メニュー バーで**デバッグ** > **デバッグの開始**します。

     Visual Studio では、アクション プロジェクト Item\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom に拡張機能をインストールし、Visual Studio の実験用インスタンスを開始します。 このインスタンスの Visual Studio でプロジェクト項目をテストします。

#### <a name="to-test-the-wizard-in-visual-studio"></a>Visual Studio でウィザードをテストするには

1. メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ファイル** > **新規** > **プロジェクト**します。

2. （アイテムテンプレートがサポートする言語に応じて）**Visual C#** または **Visual Basic** ノードを展開し、**SharePoint** ノードを展開し、**2010** ノードを選択します。

3. プロジェクト テンプレートの一覧で選択**SharePoint 2010 プロジェクト**、プロジェクトに名前を**CustomActionWizardTest**、選択し、 **OK**ボタン。

4. **SharePoint カスタマイズ ウィザード**、デバッグに使用するサイトの URL を入力し、、**完了**ボタンをクリックします。

5. **ソリューション エクスプ ローラー**、プロジェクト ノードのショートカット メニューを開き、**追加**を選び、**新しい項目の**します。

6. **新しい項目の追加 - CustomItemWizardTest**  ダイアログ ボックスで、展開、 **SharePoint**ノードの順に展開し、 **2010**ノード。

7. プロジェクト項目の一覧で選択、**カスタム アクション**項目をクリックして、**追加**ボタンをクリックします。

8. Visual Studio のもう一方のインスタンスで、先ほど `RunStarted` メソッドに設定したブレークポイントで、コードが停止していることを確認します。

9. 選択して、プロジェクトのデバッグを続行、 **F5**キーか、メニュー バーで**デバッグ** > **続行**します。

     SharePoint カスタマイズ ウィザードが表示されます。

10. **場所**、選択、**一覧の編集**オプション ボタンをクリックします。

11. **グループ ID**一覧で、選択**通信**します。

12. **タイトル**ボックスに、入力**SharePoint デベロッパー センター**します。

13. **説明**ボックスに、入力**SharePoint デベロッパー センター web サイトが開きます**します。

14. **URL**ボックスに、入力 **https://docs.microsoft.com/sharepoint/dev/** 、選択し、**完了**ボタンをクリックします。

     Visual Studio がという名前の項目を追加します**CustomAction1**開きますをプロジェクトに、 *Elements.xml*ファイルがエディターでします。 いることを確認*Elements.xml*ウィザードで指定した値が含まれています。

#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint のカスタム動作をテストするには

1. Visual Studio の実験用インスタンスの選択、 **f5 キーを押して**キーまたは、メニュー バーで、**デバッグ** > **デバッグの開始**します。

     カスタム アクションをパッケージ化されで指定された SharePoint サイトに配置された、**サイトの URL**プロジェクトでは、web ブラウザーのプロパティがこのサイトの既定のページが表示されます。

    > [!NOTE]
    > 場合、**スクリプト デバッグが無効** ダイアログ ボックスが表示されたら、選択、**はい**ボタンをクリックします。

2. SharePoint サイトの一覧の領域で、選択、**タスク**リンク。

     **タスク - すべてのタスク**ページが表示されます。

3. **リスト ツール**] タブ、リボンの選択、**一覧**] タブで、[、**設定**グループで、[**一覧の設定**します。

     **一覧の設定**ページが表示されます。

4. 、**通信**見出し、ページの上部で、選択、 **SharePoint デベロッパー センター**リンクで、ブラウザーが web サイトを開くことを確認します。 https://docs.microsoft.com/sharepoint/dev/、し、ブラウザーを閉じます。

## <a name="cleaning-up-the-development-computer"></a>開発用コンピューターのクリーンアップ
 プロジェクト項目のテストが終わったら、プロジェクト項目テンプレートを Visual Studio の実験用インスタンスから削除します。

#### <a name="to-clean-up-the-development-computer"></a>開発コンピューターをクリーンアップするには

1. メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ツール** > **拡張機能と更新**します。

     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。

2. 拡張機能の一覧で選択、 **Custom Action Project Item**拡張機能を選択し、**アンインストール**ボタンをクリックします。

3. ダイアログ ボックスが表示されますが、選択、**はい**ボタンをクリックして、拡張機能をアンインストールすることを確認します、**今すぐ再起動**アンインストールを完了するボタン。

4. Visual Studio (実験用インスタンスと、CustomActionProjectItem ソリューションが開いている Visual Studio のインスタンス) の両方のインスタンスを閉じます。

## <a name="see-also"></a>関連項目
- [チュートリアル: 項目テンプレート、第 1 部でのカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio テンプレート スキーマ参照](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [方法: プロジェクト テンプレートでウィザードを使用する](../extensibility/how-to-use-wizards-with-project-templates.md)
- [カスタム アクションの既定の場所と Id](http://go.microsoft.com/fwlink/?LinkId=181964)

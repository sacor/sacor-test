---
title: 'チュートリアル: SharePoint プロジェクトに対するカスタムの配置手順の作成 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
  - VB
  - CSharp
helpviewer_keywords:
  - SharePoint commands
  - 'SharePoint development in Visual Studio, extending deployment'
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
  - office
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>チュートリアル: SharePoint プロジェクトのカスタム配置手順を作成します。
  SharePoint プロジェクトを展開するときに、Visual Studio は、特定の順序で一連の展開の手順を実行します。 Visual Studio には、多くの組み込みの配置手順が含まれていますが、独自に作成することもできます。

 このチュートリアルでは、SharePoint を実行しているサーバー上でソリューションをアップグレードするカスタムの配置手順を作成します。 Visual Studio には、多くのタスク、そのような取り消しまたは、ソリューションの追加の組み込みの配置手順が含まれていますが、ソリューションのアップグレードの配置手順は含まれません。 既定では、SharePoint ソリューションを展開するときに Visual Studio 最初、ソリューションを取り消します (既にデプロイされて) の場合と、ソリューション全体を再デプロイします。 組み込みの配置手順の詳細については、次を参照してください。[デプロイ、発行、および SharePoint ソリューション パッケージをアップグレード](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)します。

 このチュートリアルでは、次のタスクについて説明します。

- 次の 2 つの主要タスクを実行する Visual Studio の拡張機能を作成する。

    - 拡張機能は、SharePoint ソリューションをアップグレードするカスタムの配置手順を定義します。

    - 拡張機能は、特定のプロジェクトに対して実行される配置手順のセットである新しい配置構成を定義するプロジェクトの拡張機能を作成します。 新しい展開の構成には、カスタムの配置手順といくつかの組み込みの配置手順が含まれています。

- 拡張機能のアセンブリを呼び出す 2 つのカスタム SharePoint コマンドを作成します。 SharePoint コマンドは、SharePoint のサーバー オブジェクト モデルでの Api を使用する拡張機能アセンブリを呼び出すことができる方法です。 詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)します。

- アセンブリの両方を配置するための Visual Studio Extension (VSIX) パッケージを構築します。

- 新しい配置手順をテストします。

## <a name="prerequisites"></a>必須コンポーネント
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。

- サポート対象エディションの Windows、SharePoint、Visual Studio。

- Visual Studio SDK。 このチュートリアルでは、 **VSIX プロジェクト**sdk、拡張機能を配置するための VSIX パッケージを作成するテンプレート。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)します。

  次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。

- For SharePoint サーバー オブジェクト モデルを使用します。 詳細については、次を参照してください。 [SharePoint Foundation サーバー側オブジェクト モデルを使用して](http://go.microsoft.com/fwlink/?LinkId=177796)します。

- SharePoint ソリューション。 詳細については、次を参照してください。[ソリューションの概要](http://go.microsoft.com/fwlink/?LinkId=169422)します。

- SharePoint ソリューションをアップグレードします。 詳細については、次を参照してください。[ソリューションをアップグレード](http://go.microsoft.com/fwlink/?LinkId=177802)します。

## <a name="create-the-projects"></a>プロジェクトを作成します。
 このチュートリアルを完了するには、3 つのプロジェクトを作成する必要があります。

- 拡張機能をデプロイする VSIX パッケージを作成する VSIX プロジェクト。

- 拡張機能を実装するクラス ライブラリ プロジェクト。 このプロジェクトは、.NET Framework 4.5 をターゲットする必要があります。

- カスタムの SharePoint コマンドを定義するクラス ライブラリ プロジェクト。 このプロジェクトは、.NET Framework 3.5 をターゲットする必要があります。

  この 2 つのプロジェクトを作成することから始めます。

#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。

2. メニュー バーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

3. **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** または**Visual Basic**ノードを選択し、**機能拡張**ノード。

    > [!NOTE]
    > **Extensibility**ノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。

4. ダイアログ ボックスの上部にある次のように選択します。 **.NET Framework 4.5**で .NET Framework のバージョンの一覧。

5. 選択、 **VSIX プロジェクト**名では、プロジェクト テンプレートは、 **UpgradeDeploymentStep**、選択し、 **OK**ボタン。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **UpgradeDeploymentStep**プロジェクトを**ソリューション エクスプ ローラー**します。

#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには

1. **ソリューション エクスプ ローラー**、UpgradeDeploymentStep ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。

2. **新しいプロジェクト** ダイアログ ボックスで、 **Visual C#** または **Visual Basic**ノードを展開し、**Windows**ノードを選択します。

3. ダイアログ ボックスの上部にある次のように選択します。 **.NET Framework 4.5**で .NET Framework のバージョンの一覧。

4. 選択、**クラス ライブラリ**プロジェクト テンプレート、プロジェクトの名前**DeploymentStepExtension**、選択し、 **OK**ボタン。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **DeploymentStepExtension**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。

5. Class1 コード ファイルをプロジェクトから削除します。

#### <a name="to-create-the-sharepoint-command-project"></a>SharePoint コマンド プロジェクトを作成するには

1. **ソリューション エクスプ ローラー**、UpgradeDeploymentStep ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。

2. **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#** または**Visual Basic**を選択し、 **Windows**ノード。

3. ダイアログ ボックスの上部にある次のように選択します。 **.NET Framework 3.5**で .NET Framework のバージョンの一覧。

4. 選択、**クラス ライブラリ**プロジェクト テンプレート、プロジェクトの名前**SharePointCommands**、選択し、 **OK**ボタン。

     Visual Studio の追加、 **SharePointCommands**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。

5. Class1 コード ファイルをプロジェクトから削除します。

## <a name="configure-the-projects"></a>プロジェクトを構成します。
 カスタム配置手順を作成するコードを記述する前に、コード ファイルとアセンブリの参照を追加する必要があり、プロジェクトを構成する必要があります。

#### <a name="to-configure-the-deploymentstepextension-project"></a>DeploymentStepExtension プロジェクトを構成するには

1. **DeploymentStepExtension**プロジェクトに、次の名前を持つ 2 つのコード ファイルを追加します。

    - UpgradeStep

    - DeploymentConfigurationExtension

2. DeploymentStepExtension プロジェクトのショートカット メニューを開き、選択し、**参照の追加**します。

3. **Framework**  タブで、System.ComponentModel.Composition アセンブリのチェック ボックスをオンにします。

4. **拡張**タブ、Microsoft.VisualStudio.SharePoint アセンブリのチェック ボックスを選択し、、 **ok**ボタンをクリックします。

#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointCommands プロジェクトを構成するには

1. **SharePointCommands**プロジェクトに、コマンドは、というコード ファイルを追加します。

2. **ソリューション エクスプ ローラー**のショートカット メニューを開き、 **SharePointCommands**プロジェクト ノードを選び、**参照の追加**します。

3. **拡張**タブ、次のアセンブリのチェック ボックスをオンおよび選択 をクリックし、 **ok**ボタン

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

## <a name="define-the-custom-deployment-step"></a>カスタム配置手順を定義します。
 デプロイのアップグレード手順を定義するクラスを作成します。 配置の手順で、クラスが実装を定義する、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>インターフェイス。 カスタムの配置手順を定義するときに、このインターフェイスを実装します。

#### <a name="to-define-the-custom-deployment-step"></a>カスタム配置手順を定義するには

1. **DeploymentStepExtension**プロジェクト、UpgradeStep コード ファイルを開き、そこに次のコードを貼り付けます。

    > [!NOTE]
    > 後はこのコードを追加する、プロジェクトは、一部のコンパイル エラーになりますが、表示されなくなるときにコードを追加する後の手順でします。

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>カスタム配置手順を含む展開構成を作成します。
 いくつかの組み込みの配置手順と、新しいデプロイのアップグレード手順を含む新しい展開構成、プロジェクトの拡張機能を作成します。 この拡張機能を作成すると、SharePoint プロジェクトで、デプロイのアップグレードの手順を使用する SharePoint 開発者を支援します。

 デプロイ構成は、クラスが実装を作成する、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>インターフェイス。 SharePoint プロジェクト拡張機能を作成するときに、このインターフェイスを実装します。

#### <a name="to-create-the-deployment-configuration"></a>展開構成を作成するには

1. **DeploymentStepExtension**プロジェクト、DeploymentConfigurationExtension コード ファイルを開き、そこに次のコードを貼り付けます。

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>カスタムの SharePoint コマンドを作成します。
 For SharePoint サーバー オブジェクト モデルを呼び出す 2 つのカスタム コマンドを作成します。 1 つのコマンドは、ソリューションが既に展開されているかどうかを決定します。その他のコマンドは、ソリューションをアップグレードします。

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint コマンドを定義するには

1. **SharePointCommands**プロジェクト、コマンド コード ファイルを開き、そこに次のコードを貼り付けます。

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>チェックポイント
 この時点でチュートリアルでは、カスタムの配置手順と、SharePoint コマンドのすべてのコードは、プロジェクトのようになりましたことにします。 エラーなしでコンパイルすることを確認するようにビルドします。

#### <a name="to-build-the-projects"></a>プロジェクトをビルドします

1. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **DeploymentStepExtension**プロジェクトを選び、**ビルド**します。

2. ショートカット メニューを開き、 **SharePointCommands**プロジェクトを選び、**ビルド**します。

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>拡張機能をデプロイするため、VSIX パッケージを作成します。
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。 最初に、VSIX プロジェクトの source.extension.vsixmanifest ファイルを変更することで、VSIX パッケージを構成します。 ソリューションをビルドして VSIX パッケージを作成します。

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX パッケージを構成および作成するには

1. **ソリューション エクスプ ローラー**下で、 **UpgradeDeploymentStep**プロジェクトで、ショートカット メニューを開き、 **source.extension.vsixmanifest**ファイルを選び、 **開いている**します。

     Visual Studio によってマニフェスト エディターでファイルが開きます。 source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)します。

2. **製品名**ボックスに、入力**SharePoint プロジェクトの配置のアップグレード手順**します。

3. **作成者**ボックスに、入力**Contoso**します。

4. **説明**ボックスに、入力**SharePoint プロジェクトで使用できるカスタム デプロイのアップグレード手順を提供します。** します。

5. **資産** タブ、エディターの選択、**新規**ボタンをクリックします。

     **新しい資産の追加** ダイアログ ボックスが表示されます。

6. **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**します。

    > [!NOTE]
    > この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))します。

7. **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。

8. **プロジェクト**一覧で、選択**DeploymentStepExtension**、選択し、 **OK**ボタン。

9. マニフェストのエディターで選択、**新規**もう一度ボタンをクリックします。

     **新しい資産の追加** ダイアログ ボックスが表示されます。

10. **型**一覧で、入力**SharePoint.Commands.v4**します。

    > [!NOTE]
    > この要素は、Visual Studio 拡張機能に含めるカスタム拡張機能を指定します。 詳細については、次を参照してください。[資産要素 (VSX Schema)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737)します。

11. **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。

12. **プロジェクト**一覧で、選択**SharePointCommands**、選択し、 **OK**ボタン。

13. メニュー バーで、**ビルド** > **ソリューションのビルド**、ソリューションがエラーなしでコンパイルされるかどうかを確認します。

14. UpgradeDeploymentStep プロジェクトのビルド出力フォルダーに今すぐ UpgradeDeploymentStep.vsix ファイルが含まれていることを確認します。

     既定では、ビルド出力フォルダーは ..\bin\Debug で、プロジェクト ファイルが格納されているフォルダーの下にあります。

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>デプロイのアップグレード手順をテストするための準備します。
 デプロイのアップグレード手順をテストするには、SharePoint サイトにまずサンプル ソリューションを配置する必要があります。 Visual Studio の実験用インスタンスで拡張機能のデバッグを開始します。 リスト定義と配置の手順でのテストに使用するリスト インスタンスを作成し、SharePoint サイトに配置します。 次に、リスト定義、およびリスト インスタンスを変更し、既定の展開プロセスが、SharePoint サイト上のソリューションを上書きする方法を示すために、再展開します。

 このチュートリアルの後半のリスト定義とリスト インスタンスを変更し、それらの SharePoint サイトにアップグレードします。

#### <a name="to-start-debugging-the-extension"></a>拡張機能のデバッグを開始するには

1. 管理者の資格情報で Visual Studio を再起動して UpgradeDeploymentStep ソリューションを開きます。

2. DeploymentStepExtension プロジェクトで UpgradeStep コード ファイルを開くし、コードの最初の行にブレークポイントを追加し、`CanExecute`と`Execute`メソッド。

3. 選択してデバッグを開始、 **F5**キーか、メニュー バーで**デバッグ** > **デバッグの開始**します。

4. Visual Studio では、SharePoint Projects\1.0 用 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade 配置手順を拡張機能をインストールし、Visual Studio の実験用インスタンスを開始します。 Visual Studio のこのインスタンスでは、デプロイのアップグレード手順をテストします。

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>リスト定義およびリスト インスタンスを SharePoint プロジェクトを作成するには

1. メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ファイル** > **新規** > **プロジェクト**します。

2. **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** ノードまたは**Visual Basic**ノード、展開、 **SharePoint**ノードを選び、**2010**ノード。

3. ダイアログ ボックスの上部にあることを確認します **.NET Framework 3.5** .NET Framework のバージョンの一覧に表示されます。

    プロジェクトには[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]と[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]このバージョンの .NET Framework が必要です。

4. プロジェクト テンプレートの一覧で選択**SharePoint 2010 プロジェクト**、プロジェクトに名前を**EmployeesListDefinition**、選択し、 **OK**ボタン。

5. **SharePoint カスタマイズ ウィザード**、デバッグに使用するサイトの URL を入力します。

6. **この SharePoint ソリューションの信頼レベルはどの**、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックします。

   > [!NOTE]
   > デプロイのアップグレード手順では、サンド ボックス ソリューションをサポートしていません。

7. 選択、**完了**ボタンをクリックします。

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] EmployeesListDefinition プロジェクトを作成します。

8. EmployeesListDefinition プロジェクトのショートカット メニューを開き、選択**追加**を選び、**新しい項目の**します。

9. **新しい項目の追加 - EmployeesListDefinition**  ダイアログ ボックスで、展開、 **SharePoint**ノードを選択し、 **2010**ノード。

10. 選択、**一覧**項目テンプレート、項目の名前を付けて**従業員リスト**、選択し、**追加**ボタン。

     SharePoint カスタマイズ ウィザードが表示されます。

11. **選択リストの設定**ページで、次の設定を確認し、選択、**完了**ボタン。

    1. **従業員リスト**に表示されます、**の一覧を表示する名前ですか?** ボックス。

    2. **に基づくカスタマイズ可能なリストを作成する:** オプション ボタンを選択します。

    3. **既定 (空白)** で選択された、**に基づくカスタマイズ可能なリストを作成する:** リスト。

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] タイトル列と 1 つの空のインスタンスで、従業員リスト項目を作成し、リスト デザイナーを開きます。

12. リストのデザイナーでの**列** タブで、選択、**新規または既存の列名を入力**行、および次の列を追加し、**列の表示名**一覧。

    1. 名

    2. 会社名

    3. 勤務先電話番号

    4. 電子メール

13. すべてのファイルを保存し、リスト デザイナーを閉じます。

14. **ソリューション エクスプ ローラー**、展開、**従業員リスト**ノードの順に展開し、**従業員リスト インスタンス**子ノード。

15. *Elements.xml*ファイルでこのファイルの既定の XML を次の XML に置き換えます。 この XML をリストの名前を変更する**従業員**佐藤直樹という名前を持つ従業員の情報を追加します。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
        <Data>
          <Rows>
            <Row>
              <Field Name="Title">Hance</Field>
              <Field Name="FirstName">Jim</Field>
              <Field Name="Company">Contoso</Field>
              <Field Name="Business Phone">555-555-5555</Field>
              <Field Name="E-Mail">jim@contoso.com</Field>
            </Row>
          </Rows>
        </Data>
      </ListInstance>
    </Elements>
    ```

16. 保存して閉じます、 *Elements.xml*ファイル。

17. EmployeesListDefinition プロジェクトのショートカット メニューを開き、選択し、**オープン**または**プロパティ**します。

     プロパティのデザイナーが開きます。

18. **SharePoint**タブで、、**デバッグ後に自動取り消し**チェック ボックスをオンし、プロパティを保存します。

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>リスト定義とリスト インスタンスをデプロイするには

1. **ソリューション エクスプ ローラー**、選択、 **EmployeesListDefinition**プロジェクト ノード。

2. **プロパティ**ウィンドウで、ことを確認、**アクティブな配置構成**プロパティに設定されて**既定**します。

3. 選択、 **F5**キーまたは、メニュー バーで、**デバッグ** > **デバッグの開始**します。

4. プロジェクトが正常にビルド、SharePoint サイトに web ブラウザーを開くことを確認する、**一覧**クイック起動バー内の項目が含まれていますが、新しい**従業員**、一覧に表示され、 **従業員**佐藤直樹のエントリが一覧に含まれています。

5. Web ブラウザーを閉じます。

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>リスト定義およびリスト インスタンスを変更して、それらを再デプロイするには

1. EmployeesListDefinition プロジェクトで開き、 *Elements.xml*の子であるファイル、**従業員リスト インスタンス**プロジェクト アイテム。

2. 削除、`Data`要素とその子佐藤直樹の一覧からエントリを削除します。

     完了したら、ファイルは、次の XML を含める必要があります。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
      </ListInstance>
    </Elements>
    ```

3. 保存して閉じます、 *Elements.xml*ファイル。

4. ショートカット メニューを開き、**従業員リスト**プロジェクト項目を選び、**オープン**または**プロパティ**します。

5. 選択リストのデザイナーで、**ビュー**タブ。

6. **選択した列**一覧で、選択**添付ファイル**、選択し、< キーには、その列を移動する、**使用可能な列**一覧。

7. 移動する前の手順を繰り返して、**勤務先電話番号**から列、**選択した列**の一覧を表示、**使用可能な列**一覧。

     この操作の既定のビューからのこれらのフィールドの削除、**従業員**SharePoint サイト上のリスト。

8. 選択してデバッグを開始、 **F5**キーか、メニュー バーで**デバッグ** > **デバッグの開始**します。

9. いることを確認、**配置競合** ダイアログ ボックスが表示されます。

     このダイアログ ボックスをそのソリューションは既に展開されている SharePoint サイトに (リスト インスタンス) ソリューションを展開する際に Visual Studio が表示されます。 このチュートリアルで後で、デプロイのアップグレード手順を実行するときに、このダイアログ ボックスは表示されません。

10. **配置競合** ダイアログ ボックスで、選択、**を自動的に解決**オプション ボタンをクリックします。

     Visual Studio は、SharePoint サイト上のリスト インスタンスを削除します。、プロジェクト内のリスト項目を展開およびから SharePoint サイトを開きます。

11. **を一覧表示**セクション、クイック起動バーの選択、**従業員**ボックスの一覧を次の詳細を確認してください。

    - **添付ファイル**と**自宅電話番号**列は、一覧のこのビューに表示されません。

    - リストが空です。 使用したときに、**既定**、ソリューションを再配置する配置の構成、**従業員**一覧は、プロジェクトで新しい空のリストと置き換えられました。

## <a name="test-the-deployment-step"></a>配置手順をテストします。
 デプロイのアップグレード手順をテストする準備が整いました。 まず、SharePoint でリスト インスタンスに項目を追加します。 リスト定義とリスト インスタンスを変更し、SharePoint サイトのアップグレードおよびデプロイのアップグレード手順が、新しい項目を上書きしないことを確認します。

#### <a name="to-manually-add-an-item-to-the-list"></a>リストに項目を手動で追加するには

1. リボン、SharePoint サイトの下で、**リスト ツール** タブで、選択、**項目**タブ。

2. **新規**グループで、**新しい項目の**します。

     代わりに、選択することができます、**新しい項目の追加**項目リスト自体にリンクします。

3. **従業員 - 新しい項目の**ウィンドウで、**タイトル**ボックスに、入力**設備マネージャー**します。

4. **名**ボックスに、入力**Andy**します。

5. **会社**ボックスに「 **Contoso**します。

6. 選択、**保存**ボタンをクリックし、一覧で、新しい項目が表示されることを確認し、web ブラウザーを閉じます。

     このチュートリアルの後半では、デプロイのアップグレード手順がこの一覧の内容を上書きしないことを確認するのにこの項目を使用します。

#### <a name="to-test-the-upgrade-deployment-step"></a>デプロイのアップグレード手順をテストするには

1. Visual Studio の実験用インスタンスで**ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **EmployeesListDefinition**プロジェクト ノードを選び、**プロパティ**.

    プロパティ エディターとデザイナーが開きます。

2. **SharePoint**タブで、設定、**アクティブな配置構成**プロパティを**アップグレード**します。

    このカスタムの配置構成には、新しいデプロイのアップグレード手順が含まれています。

3. ショートカット メニューを開き、**従業員リスト**プロジェクト項目を選び、**プロパティ**または**オープン**します。

    プロパティ エディターとデザイナーが開きます。

4. **ビュー**  タブで、選択、**電子メール**列で、選択し、 **<** キーから列を移動する、**選択した列**の一覧を表示、**使用可能な列**一覧。

    この操作の既定のビューからのこれらのフィールドの削除、**従業員**SharePoint サイト上のリスト。

5. 選択してデバッグを開始、 **F5**キーか、メニュー バーで**デバッグ** > **デバッグの開始**します。

6. Visual Studio のもう一方のインスタンスで、先ほど `CanExecute` メソッドに設定したブレークポイントで、コードが停止していることを確認します。

7. 選択、 **F5**または、キーをもう一度メニュー バーで、**デバッグ** > **続行**します。

8. コードの前に設定したブレークポイントで停止することを確認、`Execute`メソッド。

9. 選択、 **F5**キーまたは、メニュー バーで、**デバッグ** > **続行**最終時刻。

     Web ブラウザーでは、SharePoint サイトが開きます。

10. **を一覧表示**セクション、クイック起動領域の選択、**従業員**ボックスの一覧を次の詳細を確認してください。

    - 以前 (Andy、設備マネージャー) を手動で追加した項目では、リストに残ります。

    - **勤務先電話番号**と**電子メール アドレス**列は、一覧のこのビューに表示されません。

      **アップグレード**既存の展開の構成を変更します**従業員**SharePoint サイト上のリスト インスタンス。 使用した場合、**既定**配置構成の代わりに、**アップグレード**構成では、配置の競合は発生します。 Visual Studio は、置き換えることで、競合を解決すると、**従業員**リスト、および Andy、設備マネージャーの項目は削除されます。

## <a name="clean-up-the-development-computer"></a>開発用コンピューターをクリーンアップします。
 デプロイのアップグレード手順のテストが完了したら、リスト インスタンスとリスト定義を SharePoint サイトから削除し、Visual Studio から展開手順の拡張機能を削除します。

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>リスト インスタンスを SharePoint サイトから削除するには

1. 開く、**従業員**リストが開いていない場合に、SharePoint サイトに一覧表示します。

2. SharePoint サイトのリボンで、選択、**リスト ツール**、タブをクリックして、**一覧**タブ。

3. **設定**グループで、選択、**一覧の設定**項目。

4. **権限と管理**、選択、**このリストの削除**コマンドを選択**OK**リストをごみ箱に送信し、web を ことを確認しますブラウザー。

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>SharePoint サイトから、リスト定義を削除するには

1. メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ビルド** > **Retract**します。

     Visual Studio には、SharePoint サイトからリスト定義が取り消されます。

#### <a name="to-uninstall-the-extension"></a>拡張機能をアンインストールするには

1. メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ツール** > **拡張機能と更新**します。

     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。

2. 拡張機能の一覧で選択**SharePoint プロジェクトの配置のアップグレード手順**を選択し、**アンインストール**コマンド。

3. 表示されるダイアログ ボックスで、次のように選択します。**はい**、拡張機能をアンインストールしてから選択することを確認する**今すぐ再起動**アンインストールを完了します。

4. Visual Studio (実験用インスタンスと UpgradeDeploymentStep ソリューションが開いている Visual Studio のインスタンス) の両方のインスタンスを閉じます。

## <a name="see-also"></a>関連項目
- [SharePoint のパッケージ化と配置を拡張します。](../sharepoint/extending-sharepoint-packaging-and-deployment.md)

---
title: カスタム プロジェクトと項目テンプレートの Visual Studio 2017 のアップグレード |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
  - vssdk
monikerRange: vs-2017
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>カスタム プロジェクトと項目テンプレートの Visual Studio 2017 をアップグレードします。

Visual Studio 2017 以降、Visual Studio は Visual Studio の以前のバージョンを別の方法で、.vsix、.msi インストールされているプロジェクトと項目テンプレートを検出します。 カスタムのプロジェクトまたは項目テンプレートを使用する拡張機能を所有している場合は、拡張機能を更新する必要があります。 この記事では、必要な作業について説明します。

この変更では、Visual Studio 2017 のみに影響します。 Visual Studio の以前のバージョンには影響しません。

VSIX 拡張機能の一部としてプロジェクトや項目テンプレートを作成する場合は、「[を作成するカスタム プロジェクトと項目テンプレート](../extensibility/creating-custom-project-and-item-templates.md)します。

## <a name="template-scanning"></a>テンプレートのスキャン

Visual Studio の以前のバージョンで**devenv/setup**または**devenv/installvstemplates**プロジェクトと項目テンプレートを検索するローカル ディスクをスキャンします。 Visual Studio 2017 以降はスキャン ユーザー レベルの場所に対してのみ実行されます。 ユーザー レベルの既定の場所は **%USERPROFILE%\Documents\\< Visual Studio バージョン\>\Templates\\** します。 この場所はによって生成されたテンプレートの使用、**プロジェクト** > **テンプレートをエクスポートしています.** コマンドの場合、**自動的に Visual Studio にテンプレートをインポート**ウィザードでオプションを選択します。

その他 (非ユーザー) の場所、場所と、テンプレートの他の特性を指定する manifest(.vstman) ファイルを含める必要があります。 テンプレートを使用している .vstemplate ファイルと共に .vstman ファイルが生成されます。 .Vsix を使用して、拡張機能をインストールする場合は、Visual Studio 2017 で拡張機能を再コンパイルしてこれを実行できます。 .Msi を使用する場合、変更を手動で行う必要があります。 これらの変更を行う必要があるものの一覧は、次を参照してください。**と共に拡張機能のインストールのアップグレードをします。MSI**後でこのページ。

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>プロジェクトまたは項目テンプレートで VSIX 拡張機能を更新する方法

1. Visual Studio 2017 では、ソリューションを開きます。 コードのアップグレードになります。 **[OK]** をクリックします。

2. アップグレードの完了したら、インストール先のバージョンを変更する必要があります。 VSIX プロジェクトの source.extension.vsixmanifest ファイルを開き、選択、**インストールの対象**タブ。場合、**バージョン範囲**フィールドは **[14.0]** 、 をクリックして**編集**し、Visual Studio 2017 を含むように変更します。 たとえば設定することができます **[14.0,15.0]** または Visual Studio 2015 または Visual Studio 2017 では、いずれかに、拡張機能をインストールする **[15.0]** だけの Visual Studio 2017 をインストールします。

3. コードを再コンパイルします。

4. Visual Studio を閉じます。

5. VSIX をインストールします。

6. 次の手順に従って、更新プログラムをテストできます。

    1. 次のレジストリ キーがファイル変更のスキャンをアクティブにします。

         **reg は、hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg:32 を追加します。**

    2. キーを追加した後、実行**devenv/installvstemplates**します。

    3. Visual Studio を再度開きます。 予期された場所にテンプレートを探す必要があります。

    > [!NOTE]
    > レジストリ キーが存在する場合は、Visual Studio 機能拡張プロジェクト テンプレートは使用できません。 レジストリ キーを削除する必要があります (再実行して**devenv/installvstemplates**) それらを使用します。

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>プロジェクトと項目テンプレートをデプロイするための推奨事項

- Zip 形式のテンプレート ファイルを使用しないでください。 ファイルは、リソースやコンテンツを取得するために圧縮する必要があるテンプレートを zip 圧縮され、そのためされますなるほどを使用します。 代わりに、高速化するテンプレートの初期化に独自のディレクトリの下の個別のファイルとしてプロジェクトと項目テンプレートをデプロイする必要があります。 VSIX 拡張機能 SDK のビルド タスクは、zip 形式のテンプレートを VSIX ファイルを作成するときに自動的に解凍されます。

- テンプレート名、説明、アイコン、パッケージ/リソース ID のエントリを使用しないようにするか、テンプレートの検出中に不要なリソース アセンブリの読み込みを回避するためにプレビューします。 代わりに、ローカライズされたマニフェストを使用して、ロケールごとに、ローカライズされた名前またはプロパティを使用するテンプレート エントリを作成することができます。

- ファイルのアイテムとしてテンプレートをインクルードする場合は、マニフェスト生成得ることができない、期待される結果。 その場合は、VSIX プロジェクトに手動で生成されたマニフェストを追加する必要があります。

## <a name="file-changes-in-project-and-item-templates"></a>プロジェクトと項目テンプレート ファイルの変更
Visual Studio 2015 と Visual Studio 2017 のバージョンのテンプレート ファイルの相違点のポイントを表示する、新しいファイルを正しく作成できるようにします。

 Visual Studio 2015 によって作成された既定プロジェクトの .vstemplate ファイルを次に示します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 次に、VSIX プロジェクトの再構築の原因となった .vstman ファイル (方で、VSIX プロジェクトのマニフェストのディレクトリ) を示します。

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 によって提供される情報、 [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)要素は変わりません。 **\<VSTemplateContainer >** 要素は、関連付けられたテンプレートの .vstemplate ファイルを指します。

 Visual Studio 2015 によって作成された既定の項目 .vstemplate ファイルを次に示します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 次に、VSIX プロジェクトの再構築の原因となった .vstman ファイル (方で、VSIX プロジェクトのマニフェストのディレクトリ) を示します。

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>
```

 によって提供される情報、  **\<TemplateData >** 要素は変わりません。 **\<VSTemplateContainer >** 要素は、関連付けられたテンプレートの .vstemplate ファイルを指します

 .Vstman ファイルのさまざまな要素の詳細については、次を参照してください。 [Visual Studio テンプレート マニフェスト スキーマ参照](../extensibility/visual-studio-template-manifest-schema-reference.md)します。

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>拡張機能のアップグレードがと共にインストールします。MSI

一部 MSI ベースの拡張機能は、次のディレクトリなど一般的なテンプレートの場所にテンプレートを展開します。

- **\<Visual Studio のインストール ディレクトリ > \Common7\IDE\\< ProjectTemplates/項目テンプレート >**

- **\<Visual Studio のインストール ディレクトリ > \Common7\IDE\Extensions\\< ExtensionName\>\\< プロジェクト/項目テンプレート >**

拡張機能は、MSI ベースの展開を実行する場合は、テンプレート マニフェストを手動で生成し、拡張機能のセットアップに含まれていることを確認する必要があります。 上に挙げた .vstman 例を比較し、 [Visual Studio テンプレート マニフェスト スキーマ参照](../extensibility/visual-studio-template-manifest-schema-reference.md)します。

プロジェクトと項目テンプレートでは、個別のマニフェストを作成し、ルート テンプレートのディレクトリとして指定された上記を指す必要があります。 拡張機能とロケールごとの 1 つのマニフェストを作成します。

## <a name="see-also"></a>関連項目

- [テンプレートの検出のトラブルシューティング](troubleshooting-template-discovery.md)
- [カスタム プロジェクトと項目テンプレートの作成](creating-custom-project-and-item-templates.md)
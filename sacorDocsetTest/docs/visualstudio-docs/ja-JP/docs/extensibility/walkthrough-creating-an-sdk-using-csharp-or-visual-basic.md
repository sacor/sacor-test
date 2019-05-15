---
title: 'チュートリアル: C# または Visual Basic を使用して SDK の作成 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
  - vssdk
dev_langs:
  - CSharp
  - VB
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>チュートリアル: C# または Visual Basic を使用して、SDK を作成します。
このチュートリアルでは、Visual c# を使用して単純な数値演算ライブラリの SDK を作成し、SDK と Visual Studio Extension (VSIX) パッケージ化する方法を学習します。 次の手順を完了します。

- [SimpleMath Windows ランタイム コンポーネントを作成するには](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [SimpleMathVSIX 拡張機能プロジェクトを作成するには](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [クラス ライブラリを使用するサンプル アプリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>必須コンポーネント
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。

## <a name="createClassLibrary"></a> SimpleMath Windows ランタイム コンポーネントを作成するには

1. メニュー バーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

2. テンプレートの一覧で  **Visual c#** または**Visual Basic**、選択、 **Windows ストア**ノードを選択し、 **Windows ランタイム コンポーネント**テンプレート。

3. **名前**ボックスで、指定**SimpleMath**、選択し、 **OK**ボタン。

4. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMath**プロジェクト ノードを選び、**プロパティ**します。

5. 名前を変更**Class1.cs**に**Arithmetic.cs**し、次のコードと一致するように更新します。

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**ソリューション 'SimpleMath'** ノードを選び、 **Configuration Manager**します。

    **Configuration Manager**  ダイアログ ボックスが表示されます。

7. **アクティブ ソリューション構成**一覧で、選択**リリース**します。

8. **構成**列、ことを確認します**SimpleMath**に設定されている行**リリース**を選択し、**閉じる**ボタンをクリック、変更します。

   > [!IMPORTANT]
   > SimpleMath コンポーネントの SDK には、1 つのみの構成が含まれています。 この構成は、リリース ビルドである必要がありますまたはコンポーネントを使用するアプリの証明を渡さない、します。

9. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMath**プロジェクト ノードを選び、**ビルド**します。

## <a name="createVSIX"></a> SimpleMathVSIX 拡張機能プロジェクトを作成するには

1. ショートカット メニューで、**ソリューション 'SimpleMath'** ノード選択**追加** > **新しいプロジェクト**します。

2. テンプレートの一覧で展開**Visual c#** または**Visual Basic**、選択、**機能拡張**ノードを選択し、 **VSIX プロジェクト**テンプレート。

3. **名前**ボックスで、指定**SimpleMathVSIX**、選択し、 **OK**ボタン。

4. **ソリューション エクスプ ローラー**、選択、 **source.extension.vsixmanifest**項目。

5. メニュー バーで **[表示]**  >  **[コード]** の順に選択します。

6. 既存の XML を次の XML に置き換えます。

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. **ソリューション エクスプ ローラー**、選択、 **SimpleMathVSIX**プロジェクト。

8. メニュー バーで **[プロジェクト]**  >  **[新しい項目の追加]** の順に選択します。

9. 一覧で**一般的な項目**、展開**データ**を選び、 **XML ファイル**します。

10. **名前**ボックスで、指定`SDKManifest.xml`、選択し、**追加**ボタンをクリックします。

11. **ソリューション エクスプ ローラー**、ショートカット メニューを開き`SDKManifest.xml`、選択**プロパティ**、しの値を変更し、 **VSIX に含める**プロパティを**True**します。

12. ファイルの内容を次の XML に置き換えます。

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMathVSIX**プロジェクトで、選択**追加**を選び、**新しいフォルダー**します。

14. フォルダーの名前を変更`references`します。

15. ショートカット メニューを開き、**参照**フォルダー選択**追加**を選び、**新しいフォルダー**。

16. サブフォルダーの名前を変更`commonconfiguration`、サブフォルダーを作成し、名前をサブフォルダー、`neutral`します。

17. この時間には、最初のフォルダーの名前を変更する前の 4 つの手順を繰り返して`redist`します。

     プロジェクトには、次のフォルダー構造が含まれています。

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMath**プロジェクトを選び、**ファイル エクスプ ローラーでフォルダーを開く**します。

19. **ファイル エクスプ ローラー**に移動し、 *bin \release*フォルダー、ショートカット メニューを開き、 **SimpleMath.winmd**ファイルを選び、 **をコピー**.

20. **ソリューション エクスプ ローラー**、ファイルに貼り付け、 *references\commonconfiguration\neutral*フォルダー、 **SimpleMathVSIX**プロジェクト。

21. 前の手順を繰り返します貼り付け、 **SimpleMath.pri**ファイルを*redist\commonconfiguration\neutral*フォルダーで、 **SimpleMathVSIX**プロジェクト。

22. **ソリューション エクスプ ローラー**、選択**SimpleMath.winmd**します。

23. メニュー バーで、**ビュー** > **プロパティ**(キーボード。選択、 **F4**キー)。

24. **プロパティ**ウィンドウで、変更、**ビルド アクション**プロパティを**コンテンツ**、し、変更、 **VSIX に含める**プロパティ**True**します。

25. **ソリューション エクスプ ローラー**、この手順を繰り返します**SimpleMath.pri**します。

26. **ソリューション エクスプ ローラー**、選択、 **SimpleMathVSIX**プロジェクト。

27. メニュー バーで、**ビルド** > **ビルド SimpleMathVSIX**します。

28. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMathVSIX**プロジェクトを選び、**ファイル エクスプ ローラーでフォルダーを開く**します。

29. **ファイル エクスプ ローラー**に移動します *\bin\Release*フォルダー、および実行し*SimpleMathVSIX.vsix*をインストールします。

30. 選択、**インストール**ボタンをクリックし、インストールを完了するまで待機し、Visual Studio を再起動します。

## <a name="createSample"></a> クラス ライブラリを使用するサンプル アプリを作成するには

1. メニュー バーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

2. テンプレートの一覧で  **Visual c#** または**Visual Basic**を選択し、 **Windows ストア**ノード。

3. 選択、**空のアプリ**名では、プロジェクト テンプレートは、 **ArithmeticUI**、選択し、 **OK**ボタン。

4. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ArithmeticUI**プロジェクトを選び、**追加** > **参照**.

5. 参照型の一覧で、展開**Windows**を選び、**拡張機能**します。

6. 詳細ペインで選択、 **WinRT 数値演算ライブラリ**拡張機能。

    SDK に関する追加情報が表示されます。 選択することができます、**詳細**を開くリンク https://msdn.microsoft.com/ 、このチュートリアルで先ほど SDKManifest.xml ファイルで指定しました。

7. **参照マネージャー**ダイアログ ボックスで、 **WinRT 数値演算ライブラリ**チェック ボックスをオンにして、 **OK**ボタン。

8. メニュー バーで、**ビュー** > **オブジェクト ブラウザー**します。

9. **参照**一覧で、選択**単純な算術**します。

     SDK の新機能を参照できます。

10. **ソリューション エクスプ ローラー**オープン**MainPage.xaml**、し、その内容を次の XAML に置き換えます。

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Update **MainPage.xaml.cs**次のコードに一致するようにします。

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. 選択、 **F5**キーをアプリを実行します。

13. アプリでは、任意の 2 つの数値を入力します。、、の操作を選択し、、 **=** ボタンをクリックします。

     正しい結果が表示されます。

    作成し、拡張機能 SDK を使用できました。

## <a name="see-also"></a>関連項目
- [チュートリアル: C++ を使用して、SDK を作成します。](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [チュートリアル: JavaScript を使用して、SDK を作成します。](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [ソフトウェア開発キットを作成します。](../extensibility/creating-a-software-development-kit.md)

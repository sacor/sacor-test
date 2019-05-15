---
title: 'チュートリアル: JavaScript を使用して SDK の作成 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
  - vssdk
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>チュートリアル: JavaScript を使用して、SDK を作成します。
このチュートリアルでは、JavaScript を使用して単純な算術 SDK と Visual Studio Extension (VSIX) を作成する方法について説明します。  このチュートリアルは、これらの部分に分かれています。

- [SimpleMathVSIX 拡張機能 SDK のプロジェクトを作成するには](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [SDK を使用するサンプル アプリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  の JavaScript 用クラス ライブラリ プロジェクトの種類はありません。 このチュートリアルでは、このサンプルで*arithmetic.js* VSIX プロジェクトに直接ファイルを作成します。 実際を最初にビルドしてテストする JavaScript と CSS ファイルを Windows ストア アプリとしてお勧め — などを使用して、**空のアプリ**テンプレート、VSIX プロジェクトに配置する前にします。

## <a name="prerequisites"></a>必須コンポーネント
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。

## <a name="createSimpleMathVSIX"></a> SimpleMathVSIX 拡張機能 SDK のプロジェクトを作成するには

1. メニュー バーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

2. テンプレートのカテゴリの一覧で  **Visual c#** を選択します**拡張**を選び、 **VSIX プロジェクト**テンプレート。

3. **名前**テキスト ボックスで、指定`SimpleMathVSIX`を選択し、 **OK**ボタン。

4. 場合、 **Visual Studio パッケージ ウィザード**が表示されたら、選択、**次**ボタンを**へようこそ**  ページで、し**7 のページ 1**、選択、**完了**ボタンをクリックします。

     ただし、**マニフェスト デザイナー**が開き、スクリプトを紹介するこのチュートリアル単純なマニフェスト ファイルを直接変更することで。

5. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **source.extension.vsixmanifest**ファイルを選び、**コードの表示**します。 このコードを使用して、ファイルの既存のコンテンツを置き換えます。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SimpleMathVSIX**プロジェクトを選び、**追加** > **新しい項目の**.

7. **データ**カテゴリで、 **XML ファイル**、ファイルに名前を`SDKManifest.xml`を選択し、**追加**ボタンをクリックします。

8. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SDKManifest.xml**ファイルを選び、**開く**でファイルを表示する、 **のXMLエディター**.

9. 次のコードを追加、 **SDKManifest.xml**ファイル。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. **ソリューション エクスプ ローラー**のショートカット メニューで、 **SDKManifest.xml**ファイルで、**プロパティ**します。

11. **プロパティ**ウィンドウで、設定、 **VSIX に含める**プロパティを**True**します。

12. **ソリューション エクスプ ローラー**のショートカット メニューで、 **SimpleMathVSIX**プロジェクトで、選択**追加** > **新しいフォルダー**とフォルダーの名前を付けます`Redist`します。

13. このフォルダー構造を作成する再頒布可能パッケージ内のサブフォルダーを追加します。

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. ショートカット メニューで、 **\js\\** フォルダー選択**追加** > **新しい項目の**します。

15. **Visual c# アイテム**を選択、 **Web**カテゴリ、および選択し、 **JavaScript ファイル**項目。 ファイルに名前を`arithmetic.js`を選択し、**追加**ボタンをクリックします。

16. 次のコードに挿入*arithmetic.js*:

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. **ソリューション エクスプ ローラー**のショートカット メニューで、 **arithmetic.js**ファイルで、**プロパティ**します。 これらのプロパティの変更を加えます。

    - 設定、 **VSIX に含める**プロパティを**True**します。

    - 設定、**出力ディレクトリにコピー**プロパティを**常にコピー**します。

18. **ソリューション エクスプ ローラー**のショートカット メニューで、 **SimpleMathVSIX**プロジェクトで、選択**ビルド**します。

19. プロジェクトのショートカット メニューで、ビルドが正常に完了した後は、選択**ファイル エクスプ ローラーでフォルダーを開く**します。 移動します **\bin\debug\\** 、および実行`SimpleMathVSIX.vsix`をインストールします。

20. 選択、**インストール**ボタンをクリックし、インストールが完了しました。

21. Visual Studio を再起動します。

## <a name="createSampleApp"></a> SDK を使用するサンプル アプリを作成するには

1. メニュー バーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

2. テンプレートのカテゴリの一覧で  **JavaScript**を選択します**Windows ストア**を選び、**空のアプリ**テンプレート。

3. **名前**ボックスで、指定`ArithmeticUI`します。 **[OK]** を選択します。

4. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ArithmeticUI**プロジェクトを選び、**追加** > **参照**.

5. **Windows**、選択**拡張**、ことに注意して**単純な算術**が表示されます。

6. 選択、**単純な算術**チェック ボックスをオンにして、 **OK**ボタン。

7. **ソリューション エクスプ ローラー****参照**、注意、**単純な算術**参照が表示されます。 あることに注意してください。 を展開し、 **\js\\** を含むフォルダー **arithmetic.js**します。 開くことができます**arithmetic.js**をソース コードがインストールされていることを確認します。

8. 次のコードを使用して、内容を置き換える*default.htm*します。

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. 次のコードを使用して、内容を置き換える *\js\default.js*します。

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. 内容を置き換える *\css\default.css*次のコードで。

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. 選択、 **F5**キー、アプリをビルドして実行します。

12. アプリケーションの UI で、2 つの数値を入力します。、、の操作を選択し、選択、 **=** ボタンをクリックします。 正しい結果が表示されます。

## <a name="see-also"></a>関連項目
- [ソフトウェア開発キットを作成します。](../extensibility/creating-a-software-development-kit.md)

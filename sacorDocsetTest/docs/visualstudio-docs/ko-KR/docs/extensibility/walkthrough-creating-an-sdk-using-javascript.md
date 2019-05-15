---
title: '연습: JavaScript를 사용 하 여 SDK 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
  - vssdk
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>연습: JavaScript를 사용 하 여 SDK 만들기
이 연습에서는 JavaScript는 간단한 수학 SDK는 Visual Studio 확장 (VSIX)로 만들기를 사용 하는 방법을 설명 합니다.  이 연습에서는 이러한 부분으로 구분 됩니다.

- [SimpleMathVSIX 확장 SDK 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [SDK를 사용 하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  JavaScript에 대 한 형식이 없습니다 클래스 라이브러리 프로젝트입니다. 이 연습에서는 샘플 *arithmetic.js* VSIX 프로젝트에서 직접 파일이 만들어집니다. 실제로 것이 좋습니다는 먼저 빌드 및 테스트 JavaScript 및 CSS 파일을 Windows 스토어 앱-를 사용 하 여 예를 들어 합니다 **비어 있는 앱** 템플릿-VSIX 프로젝트에 삽입 하기 전에 합니다.

## <a name="prerequisites"></a>전제 조건
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.

## <a name="createSimpleMathVSIX"></a> SimpleMathVSIX 확장 SDK 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 범주 목록에서 아래 **Visual C#** 를 선택 **확장성**를 선택한 후는 **VSIX 프로젝트** 템플릿.

3. 에 **이름** 텍스트 상자에서 지정 `SimpleMathVSIX` 선택 합니다 **확인** 단추.

4. 경우는 **Visual Studio 패키지 마법사** 나타납니다 선택 합니다 **다음** 단추를 **시작** 페이지에서 한 후 **7의 1 페이지**, 선택는 **완료** 단추입니다.

     하지만 합니다 **매니페스트 디자이너** 열리면 보존이 연습에서는 간단한 매니페스트 파일을 직접 수정 하 여 합니다.

5. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **source.extension.vsixmanifest** 파일을 선택한 후 **코드 보기**합니다. 이 코드를 사용 하 여 파일의 기존 내용을 바꿉니다.

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

6. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMathVSIX** 프로젝트를 선택한 후 **추가** > **새 항목**.

7. 에 **데이터** 범주를 선택한 **XML 파일**, 파일 이름을 `SDKManifest.xml`, 선택는 **추가** 단추입니다.

8. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SDKManifest.xml** 파일을 선택한 후 **엽니다** 에서 파일을 표시 하려면를 **XML 편집기**.

9. 다음 코드를 추가 합니다 **SDKManifest.xml** 파일입니다.

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

10. **솔루션 탐색기**에 대 한 바로 가기 메뉴의 **SDKManifest.xml** 파일을 선택 **속성**합니다.

11. 에 **속성** 창에서 설정 합니다 **VSIX에 포함** 속성을 **True**합니다.

12. **솔루션 탐색기**에 대 한 바로 가기 메뉴의 **SimpleMathVSIX** 프로젝트 **추가** > **새 폴더**, 및 다음 폴더 이름을 `Redist`입니다.

13. 이 폴더 구조를 만들려면 Redist 하위 폴더를 추가 합니다.

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. 에 대 한 바로 가기 메뉴를 **\js\\**  폴더를 선택 **추가** > **새 항목**합니다.

15. 아래 **Visual C# 항목**를 선택 합니다 **웹** 범주를 선택한 후는 **JavaScript 파일** 항목입니다. 파일 이름을 `arithmetic.js`를 선택한 후 합니다 **추가** 단추입니다.

16. 다음 코드를 삽입할 *arithmetic.js*:

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

17. **솔루션 탐색기**에 대 한 바로 가기 메뉴의 **arithmetic.js** 파일을 선택 **속성**합니다. 이러한 속성 변경 내용을 확인 합니다.

    - 설정 된 **VSIX에 포함** 속성을 **True**합니다.

    - 설정 된 **출력 디렉터리로 복사** 속성을 **항상 복사**합니다.

18. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 **SimpleMathVSIX** 프로젝트 **빌드**합니다.

19. 빌드 프로젝트의 바로 가기 메뉴에서 성공적으로 완료 한 후 선택할 **파일 탐색기에서 폴더 열기**합니다. 이동할 **\bin\debug\\** , 실행 및 `SimpleMathVSIX.vsix` 설치 합니다.

20. 선택 된 **설치** 단추를 통해 설치를 완료 합니다.

21. Visual Studio를 다시 시작합니다.

## <a name="createSampleApp"></a> SDK를 사용 하는 샘플 앱을 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 범주 목록에서 아래 **JavaScript**를 선택 **Windows 스토어**를 선택한 후는 **비어 있는 앱** 템플릿.

3. 에 **이름을** 상자에서 지정 `ArithmeticUI`합니다. **확인** 단추를 선택합니다.

4. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ArithmeticUI** 프로젝트를 선택한 후 **추가** > **참조**.

5. 아래 **Windows**, 선택 **Extensions**, 알 수 있습니다 **간단한 수학** 표시 됩니다.

6. 선택 된 **간단한 수학** 확인란을 선택한 후 합니다 **확인** 단추입니다.

7. **솔루션 탐색기**아래에 있는 **참조**, 있음을 합니다 **간단한 수학** 참조 표시 됩니다. 확장 하는 한 **\js\\**  포함 하는 폴더 **arithmetic.js**합니다. 열 수 있습니다 **arithmetic.js** 소스 코드에 설치 되어 있는지 확인 합니다.

8. 다음 코드를 사용 하 여의 내용을 바꿉니다 *default.htm*합니다.

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

9. 다음 코드를 사용 하 여의 내용을 바꿉니다 *\js\default.js*합니다.

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

10. 내용을 바꿉니다 *\css\default.css* 이 코드를 사용 하 여:

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

11. 선택 된 **F5** 키를 빌드하고 앱을 실행 합니다.

12. 앱 UI에서에서 임의의 두 숫자로 입력 작업을 선택한 다음 선택 합니다 **=** 단추입니다. 올바른 결과 표시 합니다.

## <a name="see-also"></a>참고자료
- [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)

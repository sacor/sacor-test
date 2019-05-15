---
title: 'チュートリアル: カスタム XML 部分へのコンテンツ コントロールをバインドします。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
  - VB
  - CSharp
helpviewer_keywords:
  - 'PlainTextContentControl, binding to a custom XML part'
  - 'custom XML parts, binding to content controls'
  - 'content controls [Office development in Visual Studio], data binding'
  - 'data binding [Office development in Visual Studio], content controls'
  - 'DropDownListContentControl, binding items to a custom XML part'
  - 'DatePickerContentControl, binding to a custom XML part'
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
  - office
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>チュートリアル: カスタム XML 部分へのコンテンツ コントロールをバインドします。
  このチュートリアルでは、Word のドキュメント レベルのカスタマイズで、コンテンツ コントロールを同じ文書内の XML データにバインドする方法を説明します。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word では、という名前の XML データを格納することができます*カスタム XML 部分*ドキュメントにします。 このデータの表示は、カスタム XML 部分の要素にコンテンツ コントロールをバインドすることによって制御できます。 このチュートリアルで例として示す文書のカスタム XML 部分には、従業員情報が格納されています。 この文書を開くと、XML 要素の値がコンテンツ コントロールに表示されます。 コンテンツ コントロール内のテキストに加えた変更は、カスタム XML 部分に保存されます。

 このチュートリアルでは、次の作業について説明します。

- デザイン時におけるドキュメント レベルのプロジェクトの Word 文書へのコンテンツ コントロールの追加

- XML データ ファイルと、コンテンツ コントロールにバインドする要素を定義する XML スキーマを作成する。

- デザイン時に XML スキーマを文書に添付する。

- 実行時にドキュメント内のカスタム XML 部分を XML ファイルの内容を追加します。

- コンテンツ コントロールをカスタム XML 部分の要素にバインドする。

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> を XML スキーマに定義された値にバインドする。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必須コンポーネント
 このチュートリアルを実行するには、次のコンポーネントが必要です。

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word。

## <a name="create-a-new-word-document-project"></a>新しい Word 文書プロジェクトを作成します。
 このチュートリアルで使用する Word 文書を作成します。

### <a name="to-create-a-new-word-document-project"></a>Word 文書プロジェクトを作成するには

1. 名前の Word 文書プロジェクトを作成**EmployeeControls**します。 ソリューションの新しい文書を作成します。 詳細については、「[方法 :Visual Studio で Office プロジェクトを作成する方法](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーで新しい Word 文書を開いてを追加します、 **EmployeeControls**プロジェクトを**ソリューション エクスプ ローラー**します。

## <a name="add-content-controls-to-the-document"></a>コンテンツ コントロールをドキュメントに追加します。
 ユーザーが従業員に関する情報を表示または編集できる 3 種類のコンテンツ コントロールが含まれるテーブルを作成します。

### <a name="to-add-content-controls-to-the-document"></a>文書にコンテンツ コントロールを追加するには

1. ホストされている Word 文書で、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デザイナーのリボンで、選択、**挿入**タブ。

2. **テーブル**グループで、**テーブル**、2 つの列と 3 つの行を含むテーブルを挿入します。

3. 最初の列に次のようにテキストを入力します。

   ||
   |-|
   |**従業員の名前**|
   |**採用日**|
   |**タイトル**|

4. テーブルの 2 番目の列の最初の行を選択します (横に**Employee Name**)。

5. リボンで、選択、**開発者**タブ。

   > [!NOTE]
   > **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。

6. **コントロール**グループで、選択、**テキスト**ボタン![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") を追加する<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>最初のセルにします。

7. テーブルの 2 番目の列で 2 番目の行を選択します (横に**Hire Date**)。

8. **コントロール**グループで、選択、**日付選択カレンダー**ボタン![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") を追加するには<xref:Microsoft.Office.Tools.Word.DatePickerContentControl> 2 番目のセルにします。

9. テーブルの 2 番目の列、3 番目の行を選択します (横に**タイトル**)。

10. **コントロール**グループで、選択、**ドロップ ダウン リスト**ボタン![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl")を追加するには<xref:Microsoft.Office.Tools.Word.DropDownListContentControl>最後のセルにします。

    これで、このプロジェクトのユーザー インターフェイスが完成しました。 ここでこのプロジェクトを実行すると、最初の行にテキストを入力し、2 つ目の行で日付を選択できます。 次の手順では、表示するデータを XML ファイル内の文書に添付します。

## <a name="create-the-xml-data-file"></a>XML データ ファイルを作成します。
 通常は、ファイルやデータベースなどの外部ソースからカスタム XML 部分に格納する XML 文字列を取得する必要があります。 このチュートリアルでは、文書内のコンテンツ コントロールにバインドする要素でマークされた従業員データを含む、XML ファイルを作成します。 実行時に使用可能にするため、カスタマイズ アセンブリのリソースとして XML ファイルを埋め込みます。

#### <a name="to-create-the-data-file"></a>データ ファイルを作成するには

1. **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。

     **[新しい項目の追加]** ダイアログ ボックスが表示されます。

2. **テンプレート**ペインで、 **XML ファイル**します。

3. ファイルに名前を**employees.xml**を選択し、**追加**ボタンをクリックします。

     **Employees.xml**コード エディターでファイルが開きます。

4. 内容を置き換える、 **employees.xml**を次のテキスト ファイル。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">
      <employee>
        <name>Karina Leal</name>
        <hireDate>1999-04-01</hireDate>
        <title>Manager</title>
      </employee>
    </employees>
    ```

5. **ソリューション エクスプ ローラー**、選択、 **employees.xml**ファイル。

6. **プロパティ**ウィンドウで、**ビルド アクション**プロパティに値を変更し、**埋め込まれたリソース**します。

     この操作によって、プロジェクトをビルドしたときに、XML ファイルがリソースとしてアセンブリに埋め込まれます。 これにより、実行時に XML ファイルの内容にアクセスできます。

## <a name="create-an-xml-schema"></a>XML スキーマを作成します。
 コンテンツ コントロールをカスタム XML 部分の 1 つの要素にバインドする場合は、XML スキーマを使用する必要はありません。 ただし、<xref:Microsoft.Office.Tools.Word.DropDownListContentControl> を複数の値にバインドする場合は、前の手順で作成した XML データ ファイルを検証する XML スキーマを作成する必要があります。 XML スキーマには、`title` 要素に割り当てることができる値を定義します。 このチュートリアルの後半で、この要素に <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> をバインドします。

#### <a name="to-create-an-xml-schema"></a>XML スキーマを作成するには

1. **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。

     **[新しい項目の追加]** ダイアログ ボックスが表示されます。

2. **テンプレート**ペインで、 **XML スキーマ**します。

3. スキーマの名前を付けます**employees.xsd**を選択し、**追加**ボタンをクリックします。

     スキーマ デザイナーが開きます。

4. **ソリューション エクスプ ローラー**、ショートカット メニューを開き**employees.xsd**を選び、**コードの表示**します。

5. 内容を置き換える、 **employees.xsd**次のスキーマ ファイル。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"
        targetNamespace="http://schemas.microsoft.com/vsto/samples"
        xmlns:xs="http://www.w3.org/2001/XMLSchema"
        elementFormDefault="qualified">
      <xs:element name="employees" type="EmployeesType"></xs:element>
      <xs:complexType name="EmployeesType">
        <xs:all>
          <xs:element name="employee" type="EmployeeType"/>
        </xs:all>
      </xs:complexType>
      <xs:complexType name="EmployeeType">
        <xs:sequence>
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>
        </xs:sequence>
      </xs:complexType>
      <xs:simpleType name="TitleType">
        <xs:restriction base="xs:string">
          <xs:enumeration value ="Engineer"/>
          <xs:enumeration value ="Designer"/>
          <xs:enumeration value ="Manager"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:schema>
    ```

6. **ファイル** メニューのをクリックして**すべて保存**に変更を保存する、 **employees.xml**と**employees.xsd**ファイル。

## <a name="attach-the-xml-schema-to-the-document"></a>XML スキーマを文書に添付します。
 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> を `title` 要素の有効な値にバインドするためには、XML スキーマを文書に添付する必要があります。

### <a name="to-attach-the-xml-schema-to-the-document--includeword15shortvstoincludesword-15-short-mdmd"></a>XML スキーマをドキュメントにアタッチする ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])

1. アクティブ化**EmployeeControls.docx**デザイナー。

2. リボンで、次のように選択します。、**開発者**、タブをクリック、**アドイン**ボタンをクリックします。

3. **テンプレートとアドイン** ダイアログ ボックスで、選択、 **XML スキーマ**、タブをクリックして、**スキーマの追加**ボタンをクリックします。

4. 参照、 **employees.xsd**スキーマ、先ほど作成した、プロジェクト ディレクトリにあるし、選択し、**オープン**ボタンをクリックします。

5. 選択、 **OK**ボタン、**スキーマ設定** ダイアログ ボックス。

6. 選択、 **OK**を閉じる ボタン、**テンプレートとアドイン** ダイアログ ボックス。

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>XML スキーマをドキュメントに添付するには (Word 2010)

1. アクティブ化**EmployeeControls.docx**デザイナー。

2. リボンで、選択、**開発者**タブ。

3. **XML**グループで、選択、**スキーマ**ボタンをクリックします。

4. **テンプレートとアドイン** ダイアログ ボックスで、選択、 **XML スキーマ**、タブをクリックして、**スキーマの追加**ボタンをクリックします。

5. 参照、 **employees.xsd** 、プロジェクト ディレクトリにあるし、選択する前に作成したスキーマ、**オープン**ボタンをクリックします。

6. 選択、 **OK**ボタン、**スキーマ設定** ダイアログ ボックス。

7. 選択、 **OK**を閉じる ボタン、**テンプレートとアドイン** ダイアログ ボックス。

     **XML 構造**作業ウィンドウが開きます。

8. 閉じる、 **XML 構造**作業ウィンドウ。

## <a name="add-a-custom-xml-part-to-the-document"></a>カスタム XML 部分をドキュメントに追加します。
 コンテンツ コントロールを XML ファイル内の要素にバインドするためには、XML ファイルの内容を文書内の新しいカスタム XML 部分に追加する必要があります。

### <a name="to-add-a-custom-xml-part-to-the-document"></a>カスタム XML 部分を文書に追加するには

1. **ソリューション エクスプ ローラー**、ショートカット メニューを開き**ThisDocument.cs**または**ThisDocument.vb**を選び、**コードの表示**します。

2. `ThisDocument` クラスに次の宣言を追加します。 このコードでは、カスタム XML 部分を文書に追加するために使用する複数のオブジェクトを宣言しています。

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]

3. `ThisDocument` クラスに次のメソッドを追加します。 このメソッドは、アセンブリにリソースとして埋め込まれている XML データ ファイルの内容を取得し、それを XML 文字列として返します。

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]

4. `ThisDocument` クラスに次のメソッドを追加します。 `AddCustomXmlPart` メソッドは、受け取った XML 文字列を含むカスタム XML 部分を作成します。

     カスタム XML 部分が一度だけ作成されるように、このメソッドは、一致する GUID を持つカスタム XML 部分が文書内に存在しない場合のみカスタム XML 部分を作成します。 このメソッドは、初めて呼び出されたときに、<xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> プロパティの値を `employeeXMLPartID` 文字列に格納します。 `employeeXMLPartID` 文字列の値は、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 属性によって宣言されているため、文書内に保持されます。

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>カスタム XML 部分の要素にコンテンツ コントロールをバインドします。
 使用して、各コンテンツ コントロールをカスタム XML 部分の要素にバインド、 **XMLMapping**各コンテンツ コントロールのプロパティ。

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>コンテンツ コントロールをカスタム XML 部分の要素にバインドするには

1. `ThisDocument` クラスに次のメソッドを追加します。 このメソッドは、各コンテンツ コントロールをカスタム XML 部分の要素にバインドし、<xref:Microsoft.Office.Tools.Word.DatePickerContentControl> の日付表示形式を設定します。

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]

## <a name="run-your-code-when-the-document-is-opened"></a>ドキュメントを開いたときに、コードを実行します。
 カスタム XML 部分を作成し、文書が開かれたときにカスタム コントロールをデータにバインドします。

### <a name="to-run-your-code-when-the-document-is-opened"></a>文書が開かれたときにコードを実行するには

1. `ThisDocument_Startup` クラスの `ThisDocument` メソッドに次のコード行を追加します。 このコードから XML 文字列を取得する、 **employees.xml**ファイルが、ドキュメント内の新しいカスタム XML 部分に XML 文字列を追加し、カスタム XML 部分の要素にコンテンツ コントロールをバインドします。

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]

## <a name="test-the-project"></a>プロジェクトをテストします。
 文書を開くと、コンテンツ コントロールにカスタム XML 部分の要素のデータが表示されます。 クリックすることができます、<xref:Microsoft.Office.Tools.Word.DropDownListContentControl>の 3 つの有効な値のいずれかを選択、`title`要素で定義されている、 **employees.xsd**ファイル。 コンテンツ コントロールに表示されたデータを編集すると、新しい値が文書内のカスタム XML 部分に保存されます。

### <a name="to-test-the-content-controls"></a>コンテンツ コントロールをテストするには

1. **F5** キーを押してプロジェクトを実行します。

2. 文書内に次のようなテーブルが表示されることを確認します。 2 つ目の列の文字列は、文書内のカスタム XML 部分の要素から取得されます。

    |||
    |-|-|
    |**従業員の名前**|**Karina Leal**|
    |**採用日**|**1999 年 4 月 1 日**|
    |**タイトル**|**Manager**|

3. 右側にあるセルを選択、 **Employee Name**セルし、異なる名前を入力します。

4. 右側にあるセルを選択、 **Hire Date**セルし、日付の選択に別の日付を選択します。

5. 右側にあるセルを選択、**タイトル**セルし、ドロップダウン リストから項目を選択します。

6. 文書を保存して閉じます。

7. ファイル エクスプ ローラーで開き、 *\bin\Debug*プロジェクトの場所の下のフォルダー。

8. ショートカット メニューを開き**EmployeeControls.docx**選び、**の名前を変更**します。

9. ファイルに名前を**EmployeeControls.docx.zip**します。

     **EmployeeControls.docx**オープン XML 形式で文書を保存します。 このドキュメントでの名前を変更して、 *.zip*ファイル名拡張子をドキュメントの内容を調べることができます。 Open XML の詳細については、技術記事を参照してください。[概要 Office (2007) Open XML ファイル形式](/previous-versions/office/developer/office-2007/aa338205(v=office.12))します。

10. 開く、 **EmployeeControls.docx.zip**ファイル。

11. 開く、 **customXml**フォルダー。

12. ショートカット メニューを開き**item2.xml**選び、**オープン**します。

     このファイルには、文書に追加したカスタム XML 部分が含まれています。

13. `name`、`hireDate`、`title` の各要素に文書内のコンテンツ コントロールに入力した値が設定されていることを確認します。

14. 閉じる、 **item2.xml**ファイル。

## <a name="next-steps"></a>次の手順
 コンテンツ コントロールの使用方法の詳細については、次の各トピックを参照してください。

- 用意されているすべてのコンテンツ コントロールを使用してテンプレートを作成できます。 詳細については、「[チュートリアル:コンテンツ コントロールを使用してテンプレートを作成](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)です。

- 文書を閉じた状態でカスタム XML 部分のデータを変更できます。 その文書を次にユーザーが開いたときには、XML 要素にバインドされたコンテンツ コントロールに新しいデータが表示されます。

- コンテンツ コントロールを使用して文書の一部を保護できます。 詳細については、「[方法 :コンテンツ コントロールを使用してドキュメントの一部を保護](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)します。

## <a name="see-also"></a>関連項目
- [拡張オブジェクトを使用した Word の自動化](../vsto/automating-word-by-using-extended-objects.md)
- [コンテンツ コントロール](../vsto/content-controls.md)
- [方法: コンテンツ コントロールを Word 文書に追加します。](../vsto/how-to-add-content-controls-to-word-documents.md)
- [方法: コンテンツ コントロールを使用してドキュメントを保護する. します。](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)
- [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)

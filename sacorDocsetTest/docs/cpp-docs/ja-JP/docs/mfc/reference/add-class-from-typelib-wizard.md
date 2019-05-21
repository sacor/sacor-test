---
title: Typelib クラス追加ウィザード
ms.date: 05/09/2019
helpviewer_keywords:
  - 'COM interfaces, adding classes'
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
---
# <a name="add-class-from-typelib-wizard"></a>Typelib クラス追加ウィザード

::: moniker range="vs-2019"

このウィザードでは以降では、Visual Studio 2019 利用できます。

::: moniker-end

::: moniker range="vs-2017"

このウィザードを使用すると、使用可能なタイプ ライブラリからの MFC クラスを追加します。 ウィザードでは、各インターフェイス、選択したタイプ ライブラリからを追加するためのクラスを作成します。

- **クラスを追加します。**

   クラスの作成元となる、タイプ ライブラリの場所を指定します。

   |オプション|説明|
   |------------|-----------------|
   |**Registry**|タイプ ライブラリはシステムで登録されます。 登録されているタイプ ライブラリは、 **[Available type libraries]\(使用可能なタイプ ライブラリ\)** にリストされます。|
   |**ファイル**|タイプ ライブラリは必ずしもシステムで登録されるわけではありませんが、ファイルには含まれます。 ファイルの場所は **[場所]** で指定する必要があります。|

- **[Available type libraries]\(使用可能なタイプ ライブラリ\)**

   システムに現在登録されているタイプ ライブラリを一覧表示します。 そのインターフェイスを表示するには、このリストからタイプ ライブラリを選択して、**インターフェイス**一覧。

   参照してください"内で分散 COM:タイプ ライブラリと言語統合"タイプ ライブラリの登録の詳細については、MSDN ライブラリ。

- **場所**

   タイプ ライブラリの場所を指定します。 **[Add Class From]\(クラスの追加元\)** の **[ファイル]** をクリックすると、タイプ ライブラリを含むファイルの場所を指定できます。 ファイルの場所を参照するには、省略記号ボタンをクリックします。

- **インターフェイス**

   インターフェイスで現在選択されているタイプ ライブラリを一覧表示、**使用可能なタイプ ライブラリ**一覧。

   |転送ボタン|説明|
   |---------------------|-----------------|
   |**>**|現在、 **[インターフェイス]** リストで選択されているインターフェイスを追加します。 インターフェイスが選択されていない場合は淡色表示になります。|
   |**>>**|現在選択されているタイプ ライブラリのすべてのインターフェイスを追加、**使用可能なタイプ ライブラリ**一覧。|
   |**\<**|現在、 **[生成されたクラス]** リストで選択されているクラスを削除します。 現在選択されているクラスがない場合はグレー表示、**生成済みクラス**一覧。|
   |**\<\<**|**[生成されたクラス]** リストのクラスをすべて削除します。 淡色表示の場合、**生成済みクラス**リストが空です。|

- **生成されたクラス**

   [ **>** ] または [ **>>** ] ボタンを使用して、追加したインターフェイスから生成されるクラス名を指定します。 内の各クラス名を表示する、クラスを選択し上矢印または下矢キーの一覧をスクロールするには、このボックスをクリックできます、**クラス**ボックスとファイル名を**ファイル**ウィザードに、タイミングが生成されるボックスをクリックして**完了**します。 このボックスでは、一度に 1 つのクラスのみを選択できます。

   このリストでクラスを選択して [ **<** ] をクリックすると、クラスを削除できます。 すべてのクラスを削除する生成されたクラス ボックスで、クラスを選択する必要はありません。クリックして **<<** 、すべてのクラスを削除する、**生成済みクラス**ボックス。

- **Class**

   **[完了]** をクリックしたときにウィザードで追加される、 **[生成されたクラス]** ボックスで選択されるクラスの名前を指定します。 **Class** ボックスで名前を編集できます。

- **ファイル**

   新しいクラスのヘッダー ファイルの名前を設定します。 既定では、この名前は、 **[生成されたクラス]** で指定した名前に基づきます。 選択した場所にファイル名を保存するには、あるいはクラス宣言を既存のファイルに追加するには、省略記号ボタンをクリックします。 既存のファイルを選択した場合、ウィザードで **[完了]** をクリックするまで、ファイルは選択した場所に保存されません。

   ウィザードではファイルは上書きされません。 既存のファイルの名前を選択する場合、 **[完了]** をクリックすると、ウィザードからクラス宣言をファイルのコンテンツに追加するかどうかを指定するように求められます。 ファイルを追加するには、 **[はい]** をクリックします。ウィザードに戻り、別のファイル名を指定するには、 **[いいえ]** をクリックします。

::: moniker-end

## <a name="see-also"></a>関連項目

[タイプ ライブラリからの MFC クラス](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)<br/>
[オートメーション クライアント: タイプ ライブラリの使用](../../mfc/automation-clients-using-type-libraries.md)
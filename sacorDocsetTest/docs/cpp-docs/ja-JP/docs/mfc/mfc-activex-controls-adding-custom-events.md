---
title: 'MFC ActiveX コントロール:カスタム イベントの追加'
ms.date: 11/04/2016
helpviewer_keywords:
  - 'MFC ActiveX controls [MFC], events [MFC]'
  - 'EVENT_CUSTOM prefix [MFC]'
  - 'custom events [MFC], adding to ActiveX controls'
  - 'EVENT_CUSTOM macro [MFC]'
  - 'InCircle method [MFC]'
  - ClickIn event
  - FireClickIn event
  - 'COleControl class [MFC], custom events [MFC]'
  - 'Click event, custom events [MFC]'
  - 'events [MFC], ActiveX controls'
  - 'custom events [MFC]'
  - 'FireEvent method, adding custom events'
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX コントロール:カスタム イベントの追加

カスタム イベントは、クラスによって自動的に発生しない点で、ストック イベントとは異なります。`COleControl`します。 カスタム イベントは、特定のアクションをイベントとして、コントロール開発者によって決定を認識します。 EVENT_CUSTOM マクロでは、カスタム イベントのイベントのマップ エントリが表されます。 次のセクションでは、ActiveX コントロール ウィザードを使用して作成された ActiveX コントロール プロジェクトのカスタム イベントを実装します。

##  <a name="_core_adding_a_custom_event_with_classwizard"></a> 追加のカスタム イベント、イベント追加ウィザード

次の手順では、特定のカスタム イベント、クリックして追加します。 この手順を使用すると、その他のカスタム イベントを追加します。 カスタム イベントの名前と ClickIn イベント名およびパラメーターについては、そのパラメーターに置き換えてください。

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>イベントの追加ウィザードを使用して、クリックしてカスタム イベントを追加するには

1. コントロールのプロジェクトを読み込みます。

1. クラス ビューでは、ショートカット メニューを開き、ActiveX コントロール クラスを右クリックします。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**イベントの追加**します。

   イベントの追加ウィザードが開きます。

1. **イベント名**ボックス、まず、任意の既存のイベントを選択し、をクリックして、**カスタム**ラジオ ボタンをクリックし、入力*ClickIn*します。

1. **内部名**ボックスに、イベントの発生させる関数の名前を入力します。 この例では、イベントの追加ウィザードによって提供される既定値を使用して (`FireClickIn`)。

1. という名前のパラメーターを追加*xCoord* (型*OLE_XPOS_PIXELS*) を使用して、**パラメーター名**と**パラメーターの型**コントロール。

1. 呼ばれる 2 番目のパラメーターを追加*yCoord* (型*OLE_YPOS_PIXELS*)。

1. クリックして**完了**イベントを作成します。

##  <a name="_core_classwizard_changes_for_custom_events"></a> カスタム イベントのイベント ウィザードによる変更を追加します。

カスタム イベントを追加する場合は、イベントの追加ウィザードが、コントロール クラスに変更を加えます。H、します。CPP と。IDL ファイル。 次のコード サンプルでは、ClickIn イベントに固有です。

次の行は、ヘッダーに追加されます (します。H)、コントロール クラスのファイル:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

このコードが呼び出されるインライン関数を宣言して`FireClickIn`を呼び出す[COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent)イベントの追加ウィザードを使用する定義を ClickIn イベントとパラメーターを使用します。

イベント マップ コントロールの実装である場合に、次の行を追加するさらに、(します。コントロール クラスの CPP) ファイル:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

このコードでは、インライン関数に ClickIn イベントをマップ`FireClickIn`イベントの追加ウィザードを使用して定義したパラメーターを渡します。

最後に、次の行は、コントロールに追加されます。IDL ファイル:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

この行では、ClickIn イベントにイベントの追加ウィザードのイベントの一覧で、イベントの位置から取得する、特定の ID 番号が割り当てられます。 イベント一覧のエントリには、イベントに対応するためのコンテナーができます。 たとえば、イベントが発生したときに実行するハンドラーのコードが提供されます。

##  <a name="_core_calling_fireclickin"></a> FireClickIn を呼び出す

イベントの追加ウィザードを使用して、ClickIn カスタム イベントを追加したら、これで、このイベントが起動されるときを決める必要があります。 呼び出すことによって、これを行う`FireClickIn`適切なアクションが発生します。 この説明については、コントロールを使用して、 `InCircle` ClickIn イベントを円または楕円のリージョン内でユーザーがクリックしたときに発生させる WM_LBUTTONDOWN メッセージ ハンドラー内の関数。 次の手順では、WM_LBUTTONDOWN ハンドラーを追加します。

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>イベントの追加ウィザードを使用してメッセージ ハンドラーを追加するには

1. コントロールのプロジェクトを読み込みます。

1. クラス ビューでは、ActiveX コントロール クラスを選択します。

1. [プロパティ] ウィンドウ、**メッセージ**ボタンをクリックします。

   [プロパティ] ウィンドウには、ActiveX コントロールで処理できるメッセージの一覧が表示されます。 既に、太字で表示されているメッセージでは、それに割り当てられているハンドラー関数があります。

1. [プロパティ] ウィンドウから処理するメッセージを選択します。 この例では、WM_LBUTTONDOWN を選択します。

1. 右側のドロップダウン リスト ボックスから選択 **\<追加 > OnLButtonDown**します。

1. クラス ビューの実装では、メッセージ ハンドラーのコードにジャンプする新しいハンドラー関数をダブルクリックします (します。ActiveX コントロールの CPP) ファイルです。

次のコード サンプルは、`InCircle`コントロール ウィンドウ内でマウスの左ボタンがクリックされるたびに機能します。 このサンプルは、WM_LBUTTONDOWN ハンドラー関数にあります`OnLButtonDown`で、[円サンプル](../overview/visual-cpp-samples.md)抽象です。

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  イベントの追加ウィザードでは、マウス ボタンのアクションのメッセージ ハンドラーを作成するとき、基本クラスの同じメッセージ ハンドラーの呼び出しが自動的に追加します。 この呼び出しを削除しないでください。 コントロールは、株価のマウス メッセージのいずれかを使用している場合は、マウスのキャプチャが適切に処理されることを確認する基本クラスのメッセージ ハンドラーを呼び出す必要があります。

次の例では、イベントは、クリックがコントロール内の円または楕円のリージョン内で発生時のみ発生させます。 この動作を実現するために配置することができます、`InCircle`コントロールの実装での関数 (します。CPP) ファイル:

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

次の宣言を追加する必要がありますも、`InCircle`関数をコントロールのヘッダー (します。H) ファイル:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a> ストックの名前のカスタム イベント

両方で同じコントロールを実装することができますされませんが、ストック イベントと同じ名前のカスタム イベントを作成できます。 たとえば、ストック イベント クリックの発生が通常時は起動しませんクリックと呼ばれるカスタム イベントを作成する可能性があります。 起動処理関数を呼び出すことによって、いつでも Click イベントが発生する可能性がありますし。

次の手順は、カスタムのクリックを追加イベント。

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>ストック イベント名を使用するカスタム イベントを追加するのには

1. コントロールのプロジェクトを読み込みます。

1. クラス ビューでは、ショートカット メニューを開き、ActiveX コントロール クラスを右クリックします。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**イベントの追加**します。

   イベントの追加ウィザードが開きます。

1. **イベント名**ドロップダウン リストで、ストック イベント名を選択します。 この例では、次のように選択します。**クリック**します。

1. **イベントの種類**、**カスタム**します。

1. クリックして**完了**イベントを作成します。

1. 呼び出す`FireClick`コードの適切な場所にします。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX コントロール: メソッド](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl クラス](../mfc/reference/colecontrol-class.md)

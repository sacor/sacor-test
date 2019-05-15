---
title: 'ActiveX コントロール コンテナー:ActiveX コントロールからのイベントの処理'
ms.date: 09/12/2018
helpviewer_keywords:
  - 'event handlers [MFC], ActiveX controls'
  - 'ActiveX control containers [MFC], event sinks'
  - 'event handling [MFC], ActiveX controls'
  - 'ON_EVENT macro [MFC]'
  - 'ActiveX controls [MFC], events [MFC]'
  - 'END_EVENTSINK_MAP macro, using'
  - 'events [MFC], ActiveX controls'
  - BEGIN_EVENTSINK_MAP macro
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX コントロール コンテナー:ActiveX コントロールからのイベントの処理

この記事では、[プロパティ] ウィンドウを使用して ActiveX コントロール コンテナーで ActiveX コントロールのイベント ハンドラーをインストールするについて説明します。 イベント ハンドラーは、特定のイベントの (制御) から通知を受け取り、応答で何らかのアクションを実行に使用されます。 この通知は、イベントを「起動」と呼ばれます。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

> [!NOTE]
>  この記事では、ダイアログ ベース ActiveX コントロール コンテナーという名前のプロジェクト コンテナーと円をという名前のプロシージャとコードの例として、埋め込みのコントロールを使用します。

イベント ボタンを使用して、[プロパティ] ウィンドウで、ActiveX コントロール コンテナー アプリケーションで発生するイベントのマップを作成することができます。 「イベント シンク マップ」と呼ばれる、このマップは作成され、コントロールのコンテナー クラスにイベント ハンドラーを追加すると、Visual C で保持されます。 イベント マップ エントリの場合は、実装、各イベント ハンドラーは、特定のイベントをコンテナーのイベント ハンドラーのメンバー関数にマップします。 ActiveX コントロールのオブジェクトによって指定されたイベントが発生したときに、このイベント ハンドラー関数が呼び出されます。

イベント シンク マップの詳細については、次を参照してください。[イベント シンク マップ](../mfc/reference/event-sink-maps.md)で、*クラス ライブラリ リファレンス*します。

##  <a name="_core_event_handler_modifications_to_the_project"></a> プロジェクトにイベント ハンドラーの変更

[プロパティ] ウィンドウを使用してイベント ハンドラーを追加するときにイベント シンク マップが宣言され、プロジェクトで定義されています。 次のステートメントは、コントロールに追加されます。CPP ファイル初めてイベント ハンドラーを追加します。 このコードは、ダイアログ ボックス クラスのイベント シンク マップを宣言します (この場合、 `CContainerDlg`)。

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

イベント マップ エントリで、[プロパティ] ウィンドウを使用してイベントを追加すると (`ON_EVENT`) が追加イベント シンク マップし、イベント ハンドラー関数は、コンテナーの実装に追加されます (します。CPP) ファイルです。

次の例と呼ばれる、イベント ハンドラーを宣言する`OnClickInCircCtrl`、円のコントロールの`ClickIn`イベント。

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

次のテンプレートをさらに、追加、`CContainerDlg`クラスの実装 (します。メンバー関数のイベント ハンドラーのファイルを CPP):

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

イベント シンク マクロの詳細については、次を参照してください。[イベント シンク マップ](../mfc/reference/event-sink-maps.md)で、*クラス ライブラリ リファレンス*します。

#### <a name="to-create-an-event-handler-function"></a>イベント ハンドラー関数を作成するには

1. クラス ビューからには、ActiveX コントロールを含むダイアログ クラスを選択します。 この例では、使用`CContainerDlg`します。

1. [プロパティ] ウィンドウ、**イベント**ボタンをクリックします。

1. [プロパティ] ウィンドウでは、埋め込みの ActiveX コントロールのコントロール ID を選択します。 この例では、使用`IDC_CIRCCTRL1`します。

   [プロパティ] ウィンドウには、埋め込みの ActiveX コントロールによって起動できるイベントの一覧が表示されます。 既に太字で表示されたメンバー関数では、それに割り当てられているハンドラー関数があります。

1. ダイアログ クラスに処理するイベントを選択します。 この例では、次のように選択します。**クリック**します。

1. 右側のドロップダウン リスト ボックスから選択 **\<追加 > ClickCircctrl1**します。

1. クラス ビューでの実装でイベント ハンドラーのコードに移動する新しいハンドラー関数をダブルクリックします (します。Cpp) の`CContainerDlg`します。

## <a name="see-also"></a>関連項目

[ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)

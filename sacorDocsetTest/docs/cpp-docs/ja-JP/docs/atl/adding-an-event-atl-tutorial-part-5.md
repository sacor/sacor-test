---
title: イベントの追加 (ATL チュートリアル、パート 5)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>イベントの追加 (ATL チュートリアル、パート 5)

この手順では、追加、`ClickIn`と`ClickOut`ATL コントロールにイベント。 起動は、`ClickIn`多角形および火災内で、ユーザーがクリックした場合、イベント`ClickOut`の外側をクリックした場合。 イベントを追加するタスクは次のとおりです。

- 追加、`ClickIn`と`ClickOut`メソッド

- タイプ ライブラリを生成します。

- 接続ポイントのインターフェイスを実装します。

## <a name="adding-the-clickin-and-clickout-methods"></a>ClickIn と ClickOut メソッドの追加

選択した ATL のコントロールを手順 2. で作成したときに、**コネクション ポイント**チェック ボックスをオンします。 作成した、 `_IPolyCtlEvents` Polygon.idl ファイルのインターフェイス。 インターフェイス名がアンダー スコアで始まるに注意してください。 これは、インターフェイスが内部のインターフェイスであることを示す規則です。 したがって、COM オブジェクトを参照するためのプログラムは、ユーザー インターフェイスを表示しないように選択できます。 また**コネクション ポイント**ことを示すために Polygon.idl ファイルで、次の行を追加`_IPolyCtlEvents`は既定のソース インターフェイス。

`[default, source] dispinterface _IPolyCtlEvents;`

基になる属性では、コントロールは、コンテナーでこのインターフェイスを呼び出すことが、ため、通知のソースをことを示します。

ここで追加、`ClickIn`と`ClickOut`メソッドを`_IPolyCtlEvents`インターフェイス。

### <a name="to-add-the-clickin-and-clickout-methods"></a>ClickIn と ClickOut メソッドを追加するには

1. **ソリューション エクスプ ローラー**Polygon.idl を開き、次のコードを追加`methods:`で、 `dispInterface_IPolyCtlEvents` PolygonLib ライブラリの宣言。

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

`ClickIn`と`ClickOut`メソッドを x とパラメーターとして、クリックした点の y 座標。

## <a name="generating-the-type-library"></a>タイプ ライブラリを生成します。

プロジェクトを使用すると接続ポイントのインターフェイスとコントロールの接続ポイント コンテナー インターフェイスを構築する必要がある情報の取得に使用するため、この時点では、タイプ ライブラリを生成します。

### <a name="to-generate-the-type-library"></a>タイプ ライブラリを生成するには

1. プロジェクトをリビルドします。

     - または -

1. Polygon.idl ファイルを右クリックして**ソリューション エクスプ ローラー** ] をクリック**コンパイル**ショートカット メニューの [します。

これにより、これは、タイプ ライブラリ Polygon.tlb ファイルが作成されます。 Polygon.tlb ファイルはから認識できない**ソリューション エクスプ ローラー**バイナリ ファイルしできません表示または編集直接ためです。

## <a name="implementing-the-connection-point-interfaces"></a>接続ポイントのインターフェイスを実装します。

接続ポイントのインターフェイスとコントロールの接続ポイント コンテナー インターフェイスを実装します。 COM では、イベントは、コネクション ポイントのメカニズムを通じて実装されます。 COM オブジェクトからイベントを受信するには、コンテナーは、COM オブジェクトを実装する接続ポイントにアドバイザリ コネクションを確立します。 COM オブジェクトが複数の接続ポイントを持てないため、COM オブジェクトは、接続ポイント コンテナー インターフェイスも実装します。 このインターフェイスを使用する接続ポイントがサポートされているコンテナーを確認できます。

接続ポイントを実装するインターフェイスと呼びます`IConnectionPoint`、接続ポイント コンテナーを実装するインターフェイスを呼び出すと`IConnectionPointContainer`します。

実装に役立つ`IConnectionPoint`、接続ポイントの実装ウィザードを使用します。 このウィザードで生成、`IConnectionPoint`タイプ ライブラリを読み取って、起動できるイベントごとに関数を実装するインターフェイス。

### <a name="to-implement-the-connection-points"></a>接続ポイントを実装するには

1. **ソリューション エクスプ ローラー**_IPolyCtlEvents_CP.h を開き、次のコードを追加、`public:`内のステートメント、`CProxy_IPolyCtlEvents`クラス。

    ```cpp
    VOID Fire_ClickIn(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x1, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    VOID Fire_ClickOut(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x2, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    ```

このファイルにはというクラスが表示されます`CProxy_IPolyCtlEvents`から派生した`IConnectionPointImpl`します。 _IPolyCtlEvents_CP.h 2 つのメソッドを定義します`Fire_ClickIn`と`Fire_ClickOut`、座標の 2 つのパラメーターを取ることができます。 コントロールからイベントを発生する場合に、これらのメソッドを呼び出します。

コントロールを作成して**コネクション ポイント**オプションを選択すると、_IPolyCtlEvents_CP.h ファイルが自動的に生成します。 It も追加`CProxy_PolyEvents`と`IConnectionPointContainerImpl`コントロールの複数の継承リストに、公開される`IConnectionPointContainer`COM マップに適切なエントリを追加できます。

イベントをサポートするコードの実装が完了したら。 適切な時点で、イベントを発生させるコードを追加します。 起動することに注意してください、`ClickIn`または`ClickOut`イベント、ユーザーがコントロールでマウスの左ボタンをクリックするとします。 ユーザーがボタンをクリックしたときに確認をするのハンドラーを追加、`WM_LBUTTONDOWN`メッセージ。

### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>WM_LBUTTONDOWN メッセージ ハンドラーを追加するには

1. **クラス ビュー**を右クリックし、`CPolyCtl`クラスし、クリックして**プロパティ**ショートカット メニューの します。

1. **プロパティ**ウィンドウで、をクリックして、**メッセージ**アイコンをクリック`WM_LBUTTONDOWN`、左側の一覧から。

1. 表示されるドロップダウン リストから、クリックして **\<追加 > OnLButtonDown** します。 `OnLButtonDown` PolyCtl.h、するハンドラーの宣言が追加され、ハンドラーの実装は PolyCtl.cpp に追加されます。

次に、ハンドラーを変更します。

### <a name="to-modify-the-onlbuttondown-method"></a>OnLButtonDown メソッドを変更するには

1. 構成するコードを変更、`OnLButtonDown`メソッド PolyCtl.cpp (ウィザードで配置された任意のコードを削除する) で次のように見えるように。

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

ポイントの使用が計算されたこのコードにより、`OnDraw`関数の呼び出しで、ユーザーのマウスのクリックを検出する領域を作成する`PtInRegion`します。

*UMsg*パラメーターは、処理されている Windows メッセージの ID。 これにより、さまざまなメッセージを処理する 1 つの関数が存在することができます。 *WParam*と*lParam*パラメーターは、処理されるメッセージの標準の値。 パラメーター *bHandled*かどうか、関数が、メッセージを処理するかどうかを指定することができます。 既定では、値を FALSE に設定することができますが、関数は、メッセージを処理を示すために TRUE に設定します。 ATL にメッセージを送信するメッセージ ハンドラー関数が別の検索を続行するのには、なります。

## <a name="building-and-testing-the-control"></a>コントロールのビルドとテスト

イベントを試すようになりました。 コントロールをビルドし、ActiveX コントロール テスト コンテナーをもう一度開始します。 今回では、イベント ログ ウィンドウを表示します。 出力ウィンドウにイベントをルーティングする をクリックして**ログ**から、**オプション**メニュー選択し、**出力ウィンドウにログ**します。 インポート コントロールの挿入 ウィンドウでクリックして操作をやり直してください。 注意`ClickIn`、多角形内をクリックした場合に発生し、`ClickOut`外部をクリックしたときに発生します。

次に、プロパティ ページを追加します。

[手順 4 に戻る](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [手順 6 に進む](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>関連項目

[チュートリアル](../atl/active-template-library-atl-tutorial.md)

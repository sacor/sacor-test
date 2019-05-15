---
title: 功能表和資源：合併的功能表
ms.date: 11/04/2016
helpviewer_keywords:
  - 'status bars [MFC], OLE document applications'
  - 'visual editing [MFC], application menus and resources'
  - 'coordinating menu layouts [MFC]'
  - 'OLE containers [MFC], menus and resources'
  - 'toolbars [MFC], OLE document applications'
  - 'merging toolbar and status bar [MFC]'
  - 'menus [MFC], OLE document applications'
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
---
# <a name="menus-and-resources-menu-merging"></a>功能表和資源：合併的功能表

本文詳細說明 OLE 文件的應用程式來處理視覺化編輯，並就地啟用正確的必要步驟。 在就地啟用造成容器和伺服器的挑戰 （元件） 的應用程式。 使用者會保留在同一個框架視窗 （在容器文件的內容），但實際上正在執行另一個應用程式 （伺服器）。 這需要協調的容器和伺服器應用程式的資源。

本文章涵蓋的主題包括：

- [功能表配置](#_core_menu_layouts)

- [工具列和狀態列](#_core_toolbars_and_status_bars)

##  <a name="_core_menu_layouts"></a> 功能表配置

第一個步驟是協調功能表配置。 如需詳細資訊，請參閱 < ** 功能表建立**一節[功能表程式設計考量](https://msdn.microsoft.com/library/ms647557.aspx)Windows SDK 中。

容器應用程式應該建立要內嵌的項目就地啟動時，才使用新的功能表。 在 最小值，這個功能表應該包含下列命令，列出的順序：

1. 與檔案開啟時所使用的密碼完全相同的檔案 功能表。 （通常是任何其他的功能表項目會不放在下一步 的項目之前）。

1. 兩個連續的分隔符號。

1. 視窗功能表與檔案開啟時所使用的密碼完全相同 (只有當 MDI 應用程式中的容器應用程式)。 有些應用程式可能會有其他功能表，例如 [選項] 功能表中，屬於此群組中，當內嵌項目就地啟動功能表上會維持。

    > [!NOTE]
    >  可能會影響容器文件，例如縮放檢視其他功能表。 這些容器的功能表會出現在此功能表資源中的兩個分隔符號之間。

伺服器 （元件） 應用程式也應該建立新的功能表，專為就地啟用。 它應該是檔案開啟時所使用的功能表類似，但沒有功能表項目，例如檔案和管理伺服器文件，而不是資料的視窗。 一般而言，這個功能表包含下列任一動作：

1. 編輯功能表與檔案開啟時所使用的密碼完全相同。

1. 分隔符號。

1. 編輯功能表，例如 Scribble 範例應用程式中的 [畫筆] 功能表的物件。

1. 分隔符號。

1. [說明] 功能表。

如需範例，看看的容器和伺服器的部分範例在就地功能表配置。 若要讓範例更清楚已移除的每個功能表項目詳細資料。 容器的就地功能表有下列項目：

```
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&File C1"
    MENUITEM SEPARATOR
    POPUP "&Zoom C2"
    MENUITEM SEPARATOR
    POPUP "&Options C3"
    POPUP "&Window C3"
END
```

連續的分隔符號指示的伺服器 功能表的第一個部分應該在哪裡。 現在，請查看伺服器的就地功能表：

```
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&Edit S1"
    MENUITEM SEPARATOR
    POPUP "&Format S2"
    MENUITEM SEPARATOR
    POPUP "&Help S3"
END
```

此處的分隔符號指示應容器功能表項目的第二個群組。 此容器內就地啟動此伺服器中的物件時所產生功能表結構看起來像這樣：

```
BEGIN
    POPUP "&File C1"
    POPUP "&Edit S1"
    POPUP "&Zoom C2"
    POPUP "&Format S2"
    POPUP "&Options C3
    POPUP "&Window C3"
    POPUP "&Help S3"
END
```

如您所見，分隔符號已取代為不同的群組的每個應用程式的功能表。

伺服器應用程式也應該提供就地功能表與相關聯的快速鍵對應表。 容器會將其合併至自己的快速鍵對應表。

就地啟動內嵌項目時，framework 就會載入在就地功能表。 它然後要求在就地啟用的伺服器應用程式，其功能表，並將它所在的分隔符號。 這是功能表如何結合。 從容器取得功能表上，檔案和視窗的位置，運作，並從伺服器取得功能表項目上運作。

##  <a name="_core_toolbars_and_status_bars"></a> 工具列和狀態列

伺服器應用程式應該建立新的工具列，並將其點陣圖儲存在個別的檔案。 應用程式精靈產生應用程式會將此點陣圖儲存在稱為 ITOOLBAR 的檔案。BMP。 當您的伺服器項目啟動的位置，並應該包含相同的項目，和一般工具列，但請移除圖示，它代表在 檔案 和 視窗功能表上的項目時，新的工具列取代容器應用程式的工具列。

這個工具列載入您`COleIPFrameWnd`-衍生的類別，為您建立應用程式精靈。 [狀態] 列是由容器應用程式處理。 如需有關實作的就地框架視窗的詳細資訊，請參閱[伺服器：實作伺服器](../mfc/servers-implementing-a-server.md)。

## <a name="see-also"></a>另請參閱

[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[啟動](../mfc/activation-cpp.md)<br/>
[伺服器](../mfc/servers.md)<br/>
[容器](../mfc/containers.md)

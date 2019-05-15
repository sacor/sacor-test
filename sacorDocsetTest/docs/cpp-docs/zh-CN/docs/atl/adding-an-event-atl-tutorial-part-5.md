---
title: 添加事件（ATL 教程，第 5 部分）
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>添加事件（ATL 教程，第 5 部分）

在此步骤中，您将添加`ClickIn`和一个`ClickOut`ATL 控件的事件。 将激发`ClickIn`事件，如果用户单击内多边形和火灾`ClickOut`如果用户单击外部。 若要添加一个事件的任务如下所示：

- 添加`ClickIn`和`ClickOut`方法

- 生成类型库

- 实现连接点接口

## <a name="adding-the-clickin-and-clickout-methods"></a>添加 ClickIn 和 ClickOut 方法

在步骤 2 中创建 ATL 控件，所选**连接点**复选框。 这创建`_IPolyCtlEvents`polygon.idl 使其文件中的接口。 请注意，接口名称开头为下划线。 这是一个约定，表示该接口是一个内部接口。 因此，使您可以浏览 COM 对象的程序可以选择不向用户显示的界面。 此外请注意，选择**连接点**polygon.idl 使其文件，以指示中添加以下行`_IPolyCtlEvents`是默认源接口：

`[default, source] dispinterface _IPolyCtlEvents;`

源属性指示的控件是源的通知，以便它将在容器上调用此接口。

现在，添加`ClickIn`并`ClickOut`方法添加到`_IPolyCtlEvents`接口。

### <a name="to-add-the-clickin-and-clickout-methods"></a>若要添加的 ClickIn 和 ClickOut 方法

1. 在中**解决方案资源管理器**，打开 polygon.idl 使其并添加以下代码`methods:`中`dispInterface_IPolyCtlEvents`PolygonLib 库的声明：

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

`ClickIn`和`ClickOut`方法 take x 和 y 坐标的被单击点作为参数。

## <a name="generating-the-type-library"></a>生成类型库

此时，生成类型库，因为该项目将使用它来获取构造的连接点接口和您的控件的连接点容器接口所需的信息。

### <a name="to-generate-the-type-library"></a>若要生成类型库

1. 重新生成项目。

     或

1. 右键单击 polygon.idl 使其文件中的**解决方案资源管理器**然后单击**编译**快捷菜单上。

这将创建 Polygon.tlb 文件，该类型库文件。 Polygon.tlb 文件不是从可见**解决方案资源管理器**，因为它是一个二进制文件和无法查看或直接编辑。

## <a name="implementing-the-connection-point-interfaces"></a>实现连接点接口

实现连接点接口和您的控件的连接点容器接口。 在 COM 中，通过连接点的机制实现事件。 若要从 COM 对象接收事件，容器会建立到 COM 对象实现的连接点的通知连接。 COM 对象可以具有多个连接点，因为 COM 对象还实现连接点容器接口。 通过此接口，该容器可以确定支持的连接点。

实现连接点的接口称为`IConnectionPoint`，并实现连接点容器的接口称为`IConnectionPointContainer`。

若要帮助实施`IConnectionPoint`，您将使用实现连接点向导。 此向导将生成`IConnectionPoint`通过读取类型库并实现每个事件都可以触发的函数的接口。

### <a name="to-implement-the-connection-points"></a>若要实现连接点

1. 在中**解决方案资源管理器**，打开 _IPolyCtlEvents_CP.h 并添加以下代码`public:`中的语句`CProxy_IPolyCtlEvents`类：

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

你将看到此文件有一个名为类`CProxy_IPolyCtlEvents`派生`IConnectionPointImpl`。 现在定义了两种方法 _IPolyCtlEvents_CP.h`Fire_ClickIn`和`Fire_ClickOut`，这需要两个坐标的参数。 当你想要触发从您的控件事件时调用这些方法。

通过创建与控件**连接点**选项处于选中状态，_IPolyCtlEvents_CP.h 文件生成的。 It 还添加了`CProxy_PolyEvents`并`IConnectionPointContainerImpl`到控件的多个继承列表和公开`IConnectionPointContainer`为您通过将合适的条目添加到 COM 映射。

已完成实现以支持事件的代码。 现在，添加一些代码，以便在适当的时候引发事件。 请记住，要激发`ClickIn`或`ClickOut`当用户单击鼠标按钮在控件中的事件。 若要了解何时用户单击按钮时，将添加的处理程序`WM_LBUTTONDOWN`消息。

### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>若要添加 WM_LBUTTONDOWN 消息的处理程序

1. 在中**类视图**，右键单击`CPolyCtl`类，并单击**属性**快捷菜单上。

1. 在中**属性**窗口中，单击**消息**图标，然后单击`WM_LBUTTONDOWN`从左侧列表。

1. 从下拉列表中显示，单击 **\<添加 > OnLButtonDown**。 `OnLButtonDown`处理程序声明将添加到 PolyCtl.h，和的处理程序实现将添加到 PolyCtl.cpp。

接下来，修改该处理程序。

### <a name="to-modify-the-onlbuttondown-method"></a>若要修改 OnLButtonDown 方法

1. 更改代码，其中包括`OnLButtonDown`PolyCtl.cpp （删除由向导的任何代码） 中的方法，以便它如下所示：

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

点的使用中计算此代码使`OnDraw`函数来创建区域，用于检测用户的鼠标单击调用`PtInRegion`。

*UMsg*参数是要处理的 Windows 消息的 ID。 这使您能够处理大量消息的一个函数。 *WParam*并*lParam*参数是要处理的消息的标准值。 将参数*bHandled*允许您指定或不该函数是否处理消息。 默认情况下，值设置为 TRUE 以指示该函数处理该消息，但可以将其设置为 FALSE。 这将导致 ATL 继续查找其他消息处理程序函数将消息发送到。

## <a name="building-and-testing-the-control"></a>生成和测试控件

现在尝试您的活动。 生成控件，并再次启动 ActiveX 控件测试容器。 这一次，查看事件日志窗口。 若要将事件路由到输出窗口中，单击**日志记录**从**选项**菜单，然后选择**记录到输出窗口**。 插入控件并尝试在窗口中单击。 请注意，`ClickIn`如果已填充多边形内单击触发和`ClickOut`外部单击时触发。

接下来，您将添加属性页。

[返回到步骤 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [到步骤 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>请参阅

[教程](../atl/active-template-library-atl-tutorial.md)

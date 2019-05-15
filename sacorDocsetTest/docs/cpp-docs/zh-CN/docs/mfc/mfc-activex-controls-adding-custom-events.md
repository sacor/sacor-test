---
title: MFC ActiveX 控件：添加自定义事件
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
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX 控件：添加自定义事件

自定义事件不同于常用事件，它们不会自动触发类`COleControl`。 自定义事件可识别的某些操作，由控件开发人员，为事件。 由 EVENT_CUSTOM 宏表示自定义事件的事件映射条目。 以下部分实现使用 ActiveX 控件向导创建的 ActiveX 控件项目的自定义事件。

##  <a name="_core_adding_a_custom_event_with_classwizard"></a> 添加的自定义事件添加事件向导

下面的过程中添加特定的自定义事件，ClickIn。 此过程可用于添加其他自定义事件。 替换为你的自定义事件名称和其参数 ClickIn 事件名称和参数。

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>若要添加使用添加事件向导 ClickIn 自定义事件

1. 加载控件的项目。

1. 在类视图中，右键单击你的 ActiveX 控件类以打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加事件**。

   这将打开添加事件向导。

1. 在中**事件名称**框中，首先选择现有的任何事件，然后单击**自定义**单选按钮，然后键入*ClickIn*。

1. 在中**内部名称**框中，键入事件的触发函数的名称。 对于此示例中，使用添加事件向导提供的默认值 (`FireClickIn`)。

1. 添加名为的参数*xCoord* (类型*OLE_XPOS_PIXELS*)，并使用**参数名称**并**参数类型**控件。

1. 添加名为的第二个参数*yCoord* (类型*OLE_YPOS_PIXELS*)。

1. 单击**完成**创建事件。

##  <a name="_core_classwizard_changes_for_custom_events"></a> 为自定义事件添加事件向导更改

当添加自定义事件时，添加事件向导对控件类进行更改。H。CPP、 和。IDL 文件。 下面的代码示例是特定于 ClickIn 事件。

将以下行添加到标头 (。H） 控件类的文件：

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

此代码声明了内联函数调用`FireClickIn`的调用[COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent)使用 ClickIn 事件和参数定义使用添加事件向导。

此外，以下行添加到控件中，在实现中定位事件映射 (。控件类的 CPP) 文件：

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

此代码会将事件 ClickIn 映射到的内联函数`FireClickIn`，传递使用添加事件向导定义的参数。

最后，将以下行添加到控件的。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

此行将 ClickIn 事件分配一个特定的 ID 号，从在添加事件向导事件列表中的事件的位置。 事件列表中的条目允许容器以应对预期的事件。 例如，它可以提供激发事件时要执行的处理程序代码。

##  <a name="_core_calling_fireclickin"></a> 调用 FireClickIn

现在，已添加使用添加事件向导 ClickIn 自定义事件，必须确定激发此事件时。 执行此操作通过调用`FireClickIn`相应操作发生的时间。 本次讨论中，该控件使用`InCircle`WM_LBUTTONDOWN 消息处理程序，以触发 ClickIn 事件在用户在圆形或椭圆形区域内单击时内部函数。 以下过程添加 WM_LBUTTONDOWN 处理程序。

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>若要使用添加事件向导添加消息处理程序

1. 加载控件的项目。

1. 在类视图中，选择 ActiveX 控件类。

1. 在属性窗口中，单击**消息**按钮。

   属性窗口显示 ActiveX 控件可以处理的消息的列表。 已以粗体显示的任何消息有为其分配一个处理程序函数。

1. 从属性窗口中，选择你想要处理的消息。 对于此示例中，选择 WM_LBUTTONDOWN。

1. 从右侧的下拉列表框中，选择 **\<添加 > OnLButtonDown**。

1. 双击要跳转到实现中的消息处理程序代码的类视图中的新处理程序函数 (。ActiveX 控件的 CPP) 文件。

下面的代码示例调用`InCircle`函数每次在控制窗口内单击鼠标左键。 此示例可以在 WM_LBUTTONDOWN 处理程序函数中，找到`OnLButtonDown`，请在[Circ 示例](../overview/visual-cpp-samples.md)抽象。

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  当添加事件向导创建的鼠标按钮操作的消息处理程序时，会自动添加到相同的消息处理程序的类的基类的调用。 不要删除此调用。 如果您的控件使用任何常用鼠标消息，则必须调用基类中的消息处理程序以确保正确处理鼠标捕获。

在以下示例中，将仅当单击发生时在控件内的圆形或椭圆形区域内引发事件。 若要实现此行为，可以将放置`InCircle`控件的实现中的函数 (。CPP) 文件：

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

您还需要添加以下声明的`InCircle`函数到控件的标头 (。H） 文件：

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a> 使用常用名称自定义事件

可以使用常用事件相同的名称创建自定义事件，但可以实现相同的控件中。 例如，你可能想要创建自定义称为常用事件单击正常激发时不会激发的 Click 事件。 然后，您可以通过调用其触发函数在任何时间触发 Click 事件。

以下过程添加自定义单击事件。

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>添加自定义事件使用的常用事件名称

1. 加载控件的项目。

1. 在类视图中，右键单击你的 ActiveX 控件类以打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加事件**。

   这将打开添加事件向导。

1. 在中**事件名称**下拉列表中，选择常用事件名称。 对于此示例中，选择**单击**。

1. 有关**事件类型**，选择**自定义**。

1. 单击**完成**创建事件。

1. 调用`FireClick`在你的代码中的相应位置。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)

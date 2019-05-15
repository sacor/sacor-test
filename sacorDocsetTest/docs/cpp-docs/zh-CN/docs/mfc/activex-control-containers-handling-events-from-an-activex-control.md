---
title: ActiveX 控件容器：处理 ActiveX 控件中的事件
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
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX 控件容器：处理 ActiveX 控件中的事件

本文讨论如何使用属性窗口在 ActiveX 控件容器中安装 ActiveX 控件的事件处理程序。 事件处理程序用于接收通知 （从控件） 的某些事件和响应执行某些操作。 此通知是名为"触发"此事件。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

> [!NOTE]
>  本文使用一个名为 Container、基于对话框的 ActiveX 控件容器项目和一个名为 Circ 的嵌入控件分别作为过程和代码中的示例。

在属性窗口中使用事件按钮，可以在 ActiveX 控件容器应用程序中创建的映射可以发生的事件。 此映射，称为"事件接收器映射 '，创建和维护视觉对象C++时将事件处理程序添加到控件容器类。 每个事件处理程序，实现与事件映射条目时，将特定事件映射到容器事件处理程序成员函数。 指定的事件触发的 ActiveX 控件对象时调用此事件处理程序函数。

事件接收器映射的详细信息，请参阅[事件接收器映射](../mfc/reference/event-sink-maps.md)中*类库参考*。

##  <a name="_core_event_handler_modifications_to_the_project"></a> 修改项目的事件处理程序

当使用属性窗口来添加事件处理程序时，事件接收器映射声明和定义项目中。 以下语句添加到控件。CPP 文件第一次添加一个事件处理程序。 此代码声明了事件接收器映射对话框类 (在这种情况下， `CContainerDlg`):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

当您使用属性窗口中添加事件，事件映射条目 (`ON_EVENT`) 添加到事件接收器映射和事件处理程序函数添加到容器的实现 (。CPP) 文件。

下面的示例声明一个事件处理程序调用`OnClickInCircCtrl`，为 Circ 控件的`ClickIn`事件：

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

此外，以下模板添加到`CContainerDlg`类实现 (。对于事件处理程序成员函数 CPP) 文件：

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

事件接收器宏的详细信息，请参阅[事件接收器映射](../mfc/reference/event-sink-maps.md)中*类库参考*。

#### <a name="to-create-an-event-handler-function"></a>若要创建一个事件处理程序函数

1. 从类视图中，选择包含 ActiveX 控件的对话框类。 对于此示例中，使用`CContainerDlg`。

1. 在属性窗口中，单击**事件**按钮。

1. 在属性窗口中，选择嵌入 ActiveX 控件的控件 ID。 对于此示例中，使用`IDC_CIRCCTRL1`。

   属性窗口显示可以由嵌入 ActiveX 控件激发的事件的列表。 已以粗体显示的任何成员函数具有分配给它的处理程序函数。

1. 选择想要处理的对话框类的事件。 对于此示例中，选择**单击**。

1. 从右侧的下拉列表框中，选择 **\<添加 > ClickCircctrl1**。

1. 双击要跳转到实现中的事件处理程序代码的类视图中的新处理程序函数 (。CPP) 文件的`CContainerDlg`。

## <a name="see-also"></a>请参阅

[ActiveX 控件容器](../mfc/activex-control-containers.md)

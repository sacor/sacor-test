---
title: 添加属性页（ATL 教程，第 6 部分）
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>添加属性页（ATL 教程，第 6 部分）

> [!NOTE] 
> ATL OLE DB 提供程序向导不是可在 Visual Studio 2019 及更高版本。

属性页将作为单独的 COM 对象，以便能够在需要时共享。 在此步骤中，将执行以下任务来添加到控件的属性页：

- 创建属性页资源

- 添加代码以创建和管理的属性页

- 向控件添加的属性页

## <a name="creating-the-property-page-resource"></a>创建属性页资源

若要添加到控件属性页，请使用 ATL 属性页模板。

### <a name="to-add-a-property-page"></a>若要添加的属性页

1. 在中**解决方案资源管理器**，右键单击`Polygon`。

1. 在快捷菜单上，单击**外** > **新项**。

1. 从模板列表中，选择**ATL** > **ATL 属性页**然后单击**添加**。

1. 当**ATL 属性页向导**出现，请输入*PolyProp*作为**短**名称。

1. 单击**字符串**以打开**字符串**页，并输入 **& 多边形**作为**标题**。

   **标题**的属性页是在该页面的选项卡中显示的字符串。 **文档字符串**是属性框架使用将放置在状态行或工具提示中的说明。 请注意，标准属性框架当前不使用此字符串中，因此，您可以保留使用默认内容。 你将不会生成**帮助文件**目前，因此请删除该文本框中的条目。

1. 单击**完成**，并且将创建属性页对象。

创建以下三个文件：

|文件|描述|
|----------|-----------------|
|PolyProp.h|包含C++类`CPolyProp`，它可实现的属性页。|
|PolyProp.cpp|包括 PolyProp.h 文件。|
|PolyProp.rgs|注册属性页对象以注册表脚本。|

此外进行了以下代码更改：

- 新的属性页添加到 Polygon.cpp 中的对象项映射。

- `PolyProp`类添加到 polygon.idl 使其文件。

- 新的注册表脚本文件 PolyProp.rgs 添加到项目资源。

- 对话框模板添加到属性页的项目资源。

- 指定的属性字符串添加到资源字符串表。

现在，添加你想要在属性页上显示的字段。

### <a name="to-add-fields-to-the-property-page"></a>若要将字段添加到属性页

1. 在中**解决方案资源管理器**，双击 Polygon.rc 资源文件。 这将打开**资源视图**。

1. 在中**资源视图**，展开`Dialog`节点，然后双击`IDD_POLYPROP`。 请注意，将出现的对话框中只有一个标签，告诉你在此处插入控件为空。

1. 选择该标签，然后将其更改为读取`Sides:`通过更改**标题**中的文本**属性**窗口。

1. 调整标签框的大小，使其适应文本的大小。

1. 拖动**编辑控件**从**工具箱**标签的右侧。

1. 最后，更改**ID**到编辑控件的`IDC_SIDES`使用**属性**窗口。

这将完成创建属性页资源的过程。

## <a name="adding-code-to-create-and-manage-the-property-page"></a>添加代码以创建和管理的属性页

现在，创建属性页资源后，需要编写的实现代码。

首先，启用`CPolyProp`类来设置您的对象中的边数时**应用**按下按钮。

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>若要修改应用函数以设置边数

1. 替换为`Apply`PolyProp.h 中使用以下代码的函数：

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

属性页中可以有多个客户端连接到它一次，因此`Apply`函数循环，并调用`put_Sides`从编辑框中检索值的每个客户端上。 正在使用[CComQIPtr](../atl/reference/ccomqiptr-class.md)类，该类执行`QueryInterface`若要获取的每个对象`IPolyCtl`从接口`IUnknown`接口 (存储在`m_ppUnk`数组)。

该代码立即检查该设置`Sides`属性却真的灵验了。 如果失败，代码将显示一个消息框，显示错误详细信息从`IErrorInfo`接口。 通常情况下，容器会要求一个对象，用于`ISupportErrorInfo`接口并调用`InterfaceSupportsErrorInfo`第一个，以确定对象是否支持设置错误的信息。 你可以跳过此任务。

[CComPtr](../atl/reference/ccomptr-class.md)可帮助你通过自动处理引用计数，因此不需要调用`Release`接口上。 `CComBSTR` 可帮助你使用 BSTR 处理，因此不需要执行最后一个`SysFreeString`调用。 你还使用一个不同的字符串转换类，以便可以将转换 BSTR，如有必要 （这是为什么 USES_CONVERSION 宏位于函数的开头）。

此外需要设置属性页的已更新标志以指示**应用**应启用按钮。 发生这种情况是当用户更改中的值**边**编辑框。

### <a name="to-handle-the-apply-button"></a>若要处理应用按钮

1. 在中**类视图**，右键单击`CPolyProp`然后单击**属性**快捷菜单上。

1. 在中**属性**窗口中，单击**事件**图标。

1. 展开`IDC_SIDES`节点在事件列表中。

1. 选择`EN_CHANGE`，然后从右侧的下拉列表菜单，单击 **\<添加 > OnEnChangeSides** 。 `OnEnChangeSides`处理程序声明将添加到 Polyprop.h 和到 Polyprop.cpp 的处理程序实现。

接下来，您将修改该处理程序。

### <a name="to-modify-the-onenchangesides-method"></a>若要修改 OnEnChangeSides 方法

1. 将以下代码添加到 Polyprop.cpp 中`OnEnChangeSides`（删除向导放在那里的任何代码） 的方法：

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

`OnEnChangeSides` 时将调用`WM_COMMAND`与发送消息`EN_CHANGE`通知`IDC_SIDES`控件。 `OnEnChangeSides` 然后调用`SetDirty`，并将传递 TRUE 以指示属性页现在已更新并**应用**应启用按钮。

## <a name="adding-the-property-page-to-the-control"></a>向控件添加的属性页

ATL 属性页模板和向导不属性页到您的控件为您自动添加，因为在项目中可能有多个控件。 需要将条目添加到控件的属性映射。

### <a name="to-add-the-property-page"></a>若要添加的属性页

1. 打开 PolyCtl.h 并将这些行添加到属性映射：

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

控件的属性映射现在如下所示：

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

您可以添加`PROP_PAGE`宏的属性页，但如果你将 clsid`PROP_ENTRY`宏所示，`Sides`保存控件时，也会保存属性值。

该宏的三个参数是属性说明，该属性的 DISPID 和对其具有该属性的属性页的 CLSID。 如果将该控件加载到 Visual Basic 和在设计时设置的边数等，这非常有用。 因为保存边数，重新加载 Visual Basic 项目时，将还原的边数。

## <a name="building-and-testing-the-control"></a>生成和测试控件

现在生成该控件并将其插入到 ActiveX 控件测试容器。 在中**测试容器**，然后在**编辑**菜单中，单击**PolyCtl 类对象**。 属性页将显示与您添加的信息。

**应用**按钮最初处于禁用状态。 开始键入中的值**边**框和**应用**按钮将变成启用状态。 输入值之后，请单击**应用**按钮。 控件显示更改，并**应用**按钮再次禁用。 请尝试输入无效值。 您将看到包含错误说明设置从一个消息框`put_Sides`函数。

接下来，会将您的控件在网页上。

[返回到步骤 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [到步骤 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>请参阅

[教程](../atl/active-template-library-atl-tutorial.md)

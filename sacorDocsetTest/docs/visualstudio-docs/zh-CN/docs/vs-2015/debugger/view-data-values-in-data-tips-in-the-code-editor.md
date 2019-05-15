---
title: 在代码编辑器中查看在数据提示中的数据值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
  - FSharp
  - VB
  - CSharp
  - C++
  - JScript
  - VB
  - CSharp
  - C++
helpviewer_keywords:
  - 'debugging [Visual Studio], DataTips'
  - DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>在代码编辑器中查看数据提示中的数据值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用数据提示功能，可以在调试期间方便地查看程序中变量的有关信息。 数据提示功能只能在中断模式下可用，并且只对当前执行范围内的变量有效。  
  
 在中[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]、 数据提示可以固定到源文件中的特定位置或也可以浮动在所有之上[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]windows。  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>显示数据提示（只在中断模式下）  
  
1. 在源窗口中，将鼠标指针置于当前范围内的任何变量上。  
  
    屏幕上显示数据提示。  
  
   > [!NOTE]
   > 始终在挂起执行的上下文中（而不是在光标的悬停位置）计算数据提示。 如果将鼠标指针悬停在另一函数中的变量的上方（该变量与当前上下文中的某个变量同名），则另一函数中该变量的值将显示为当前上下文中的该变量的值。  
  
2. 移开鼠标指针时，数据提示会消失。 若要固定数据提示以便它保持打开状态，请单击**固定到源**图标，或  
  
   - 右键单击一个变量，然后单击**固定到源**。  
  
     在调试会话结束时，固定的数据提示将关闭。  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>解除固定数据提示，使其浮动  
  
- 在固定数据提示中，单击**从源**图标。  
  
     图钉图标将更改为解除固定位置。 现在，数据提示浮动在任何打开的窗口上方。 在调试会话结束时，浮动数据提示将关闭。  
  
### <a name="to-repin-a-floating-datatip"></a>重新固定浮动的数据提示  
  
- 在数据提示中，单击图钉图标。  
  
     图钉图标将更改为固定位置。 如果工具提示位于源窗口外部，将禁用图钉图标，因此将无法固定数据提示。  
  
### <a name="to-close-a-datatip"></a>关闭单个数据提示  
  
- 将鼠标指针置于数据提示中，上方，然后单击**关闭**图标。  
  
### <a name="to-close-all-datatips"></a>关闭所有数据提示  
  
- 上**调试**菜单上，单击**清除所有数据提示**。  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>关闭特定文件的所有数据提示  
  
- 上**调试**菜单上，单击**清除所有数据提示固定到***文件*。  
  
## <a name="expanding-and-editing-information"></a>展开和编辑信息  
 利用数据提示功能，可以展开数组、结构或对象以查看其成员。 从数据提示还可以编辑变量的值。  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>展开变量以查看它的元素  
  
- 在数据提示中，将鼠标指针置于 **+** 变量名之前的登录。  
  
     该变量展开以树的形式显示其元素。  
  
     变量展开后，可以使用键盘上的箭头键进行上移或下移。 或者，也可使用鼠标。  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>使用数据提示功能编辑变量值  
  
1. 在数据提示中，单击值。 对于只读值，此功能是禁用的。  
  
2. 键入新值并按 Enter。  
  
## <a name="making-a-datatip-transparent"></a>使数据提示显示为透明  
 如果想要看到数据提示后面的代码，可以使数据提示暂时显示为透明。 这不适用于固定或浮动的数据提示。  
  
#### <a name="to-make-a-datatip-transparent"></a>使数据提示显示为透明  
  
- 在数据提示中，按 Ctrl。  
  
     在按住 Ctrl 键的时间内，数据提示将一直保持透明。  
  
## <a name="visualizing-complex-data-types"></a>可视化复杂数据类型  
 如果在数据提示中，一个或多个变量名称旁边会显示一个放大镜图标[创建自定义可视化工具](../debugger/create-custom-visualizers-of-data.md)可用于该数据类型的变量。 您可以使用可视化工具以更直观的方式（通常为图形）显示信息。  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>使用可视化工具查看变量的内容  
  
- 单击放大镜图标选择数据类型的默认可视化工具。  
  
     或  
  
     单击可视化工具旁的弹出箭头，然后在适用于该数据类型的可视化工具列表中选择所需的可视化工具。  
  
     可视化工具将显示信息。  
  
## <a name="adding-information-to-a-watch-window"></a>将信息添加到“监视”窗口  
 如果你想要继续监视某个变量，则可以添加到变量**监视**从数据提示窗口。  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>将变量添加到“监视”窗口  
  
- 数据提示中，右键单击，然后单击**添加监视**。  
  
     将变量添加到**监视**窗口。 如果使用的版本支持多个**Watch**变量添加到 windows，**监视 1。**  
  
## <a name="importing-and-exporting-datatips"></a>导入和导出数据提示  
 您可以将数据提示导出到 XML 文件中，然后与同事共享该文件或使用文本编辑器编辑该文件。  
  
#### <a name="to-export-datatips"></a>导出数据提示  
  
1. 在调试菜单上单击**导出数据提示**。  
  
     **导出数据提示**对话框随即出现。  
  
2. 使用标准文件技术导航到你想要保存 XML 文件中，键入的名称中的文件的位置**文件名**框中，然后依次**确定**。  
  
#### <a name="to-import-datatips"></a>导入数据提示  
  
1. 在调试菜单上单击**导入数据提示**。  
  
     **导入数据提示**对话框随即出现。  
  
2. 使用对话框的以查找 XML 文件，你想要打开，然后单击**确定**。  
  
## <a name="see-also"></a>请参阅  
 [查看调试器中的数据](../debugger/viewing-data-in-the-debugger.md)   
 [如何：使用快速监视对话框](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [创建自定义可视化工具](../debugger/create-custom-visualizers-of-data.md)   
 [如何：更改调试器 Windows 的数字格式](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)

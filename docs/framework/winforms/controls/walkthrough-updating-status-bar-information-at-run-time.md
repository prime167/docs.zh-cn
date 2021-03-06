---
title: 演练：在运行时更新状态栏信息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
ms.openlocfilehash: 670746a1b964a85bc5136d976d831c6848466797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930989"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>演练：在运行时更新状态栏信息
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar>和控件替换和添加了和控件的功能; 但是, 和<xref:System.Windows.Forms.StatusBarPanel>控件将保留以实现向后兼容性和将来使用, 前提是你<xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusStrip>.  
  
 通常情况下，程序会要求根据应用程序状态的更改或其他用户交互情况，在运行时动态更新状态栏面板的内容。 这是一种用于执行以下任务的常用方式：通知用户启用了 CAPS LOCK、NUM LOCK 或 SCROLL LOCK 之类的键，或者将日期或时钟作为方便的引用提供。  
  
 在下面的示例中, 将使用<xref:System.Windows.Forms.StatusBarPanel>类的实例来承载时钟。  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>准备更新状态栏  
  
1. 创建新的 Windows 窗体。  
  
2. 向窗体添加一个 <xref:System.Windows.Forms.StatusBar> 控件。 有关详细信息，请参阅[如何：将控件添加到](how-to-add-controls-to-windows-forms.md)Windows 窗体。  
  
3. 将状态栏面板添加到<xref:System.Windows.Forms.StatusBar>控件。 有关详细信息，请参阅[如何：向状态栏控件](how-to-add-panels-to-a-statusbar-control.md)添加面板。  
  
4. 对于已<xref:System.Windows.Forms.StatusBar>添加到窗体的控件, <xref:System.Windows.Forms.StatusBar.ShowPanels%2A>将属性设置为`true`。  
  
5. 将 Windows 窗体<xref:System.Windows.Forms.Timer>组件添加到窗体。  
  
    > [!NOTE]
    > Windows 窗体<xref:System.Windows.Forms.Timer?displayProperty=nameWithType>组件是为 Windows 窗体环境设计的。 如果需要适合服务器环境的计时器，请参阅[基于服务器的计时器介绍](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。  
  
6. 将 <xref:System.Windows.Forms.Timer.Enabled%2A> 属性设置为 `true`。  
  
7. 将的<xref:System.Windows.Forms.Timer.Interval%2A> <xref:System.Windows.Forms.Timer>属性设置为30000。  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.Timer>组件<xref:System.Windows.Forms.Timer.Interval%2A>的属性设置为30秒 (30000 毫秒), 以确保在显示的时间内反映准确的时间。  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>通过实现计时器更新状态栏  
  
1. 将以下代码插入<xref:System.Windows.Forms.Timer>组件的事件处理程序中, 以更新<xref:System.Windows.Forms.StatusBar>控件的面板。  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     此时，就可以运行该应用程序并观察在状态栏面板中运行的时钟。  
  
### <a name="to-test-the-application"></a>测试应用程序  
  
1. 调试该应用程序，然后按 F5 运行。 有关调试的详细信息，请参阅[在 Visual Studio 中进行调试](/visualstudio/debugger/debugging-in-visual-studio)。  
  
    > [!NOTE]
    > 大约 30 秒之后，时钟才会出现在状态栏上。 这样可以获得最精确的时间。 相反, 若要使时钟更快出现, 可以减少上一过程的<xref:System.Windows.Forms.Timer.Interval%2A>步骤7中设置的属性值。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [如何：向状态栏控件添加面板](how-to-add-panels-to-a-statusbar-control.md)
- [如何：确定单击 Windows 窗体状态栏控件中的哪个面板](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar 控件概述](statusbar-control-overview-windows-forms.md)

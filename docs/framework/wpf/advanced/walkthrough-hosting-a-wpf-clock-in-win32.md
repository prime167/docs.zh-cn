---
title: 演练：在 Win32 中承载 WPF 时钟
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 27e1a2e88beeacf8c2cd98f61b11542ee2341e8f
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433980"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>演练：在 Win32 中承载 WPF 时钟

若要[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]放置[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]在应用程序<xref:System.Windows.Interop.HwndSource>内, 请使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , 它提供包含内容的 HWND。 首先创建, 并<xref:System.Windows.Interop.HwndSource>为其提供类似于 CreateWindow 的参数。 然后, 告诉<xref:System.Windows.Interop.HwndSource>您所需[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的内容。 最后, 获取中的 HWND <xref:System.Windows.Interop.HwndSource>。 本演练演示了如何在重新实现 " [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]操作系统[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] **日期和时间属性**" 对话框的应用程序中创建混合。

## <a name="prerequisites"></a>系统必备

请参阅[WPF 和 Win32 互操作](wpf-and-win32-interoperation.md)。

## <a name="how-to-use-this-tutorial"></a>如何使用本教程

本教程重点介绍生成互操作应用程序的重要步骤。 本教程通过示例[Win32 时钟互操作示例](https://go.microsoft.com/fwlink/?LinkID=160051)进行了支持, 但该示例反射了最终产品。 本教程介绍的步骤如下所示: 从自己的现有[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]项目开始, 可能是预先存在的项目, 并将托管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的应用程序添加到应用程序。 可以将最终产品与[Win32 时钟互操作示例](https://go.microsoft.com/fwlink/?LinkID=160051)进行比较。

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Win32 中的 Windows Presentation Framework 的演练 (HwndSource)

下图显示了本教程的预期最终产品：

![显示 "日期和时间属性" 对话框的屏幕截图。](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

可以通过在 Visual Studio 中创建C++ Win32 项目, 并使用对话框编辑器创建以下内容来重新创建此对话框:

!["重新创建日期和时间属性" 对话框](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] (您无需<xref:System.Windows.Interop.HwndSource>使用, 也不需要使用C++来编写[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]程序, 但这是执行此操作的一种相当典型的方法, 并且非常适合逐步教程说明)。

需要完成五个特定的子步骤, 才能将[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]时钟放入对话框:

1. 通过更改[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]中[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]的项目设置, 使你的项目可以调用托管代码 ( **/clr**)。

2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 在单独<xref:System.Windows.Controls.Page>的 DLL 中创建。

3. 将其放入<xref:System.Windows.Interop.HwndSource>。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>

4. 使用属性获取的<xref:System.Windows.Controls.Page>HWND <xref:System.Windows.Interop.HwndSource.Handle%2A> 。

5. 用于[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]决定在较大[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]的应用程序中放置 HWND 的位置

## <a name="clr"></a>/clr

第一步是将此非托管[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]项目转换为可以调用托管代码的项目。 使用/clr 编译器选项, 它将链接到您想要使用的所需 Dll, 并调整 Main 方法以便与一起[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用。

若要允许在C++项目中使用托管代码:右键单击 "win32clock 项目", 然后选择 "**属性**"。 在 "**常规**" 属性页 (默认值) 上, 将 "公共语言`/clr`运行时支持" 更改为。

接下来, 添加对所需的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dll 的引用:PresentationCore、PresentationFramework、WindowsBase、Uiautomationprovider.dll、Uiautomationtypes.dll 和的链接的链接。 （以下说明假定操作系统安装在 C: 驱动器上。）

1. 右键单击 "win32clock 项目", 然后选择 "**引用 ...** ", 然后在该对话框中执行以下操作:

2. 右键单击 "win32clock 项目", 然后选择 "**引用 ...** "。

3. 单击 "**添加新引用**", 单击 "浏览" 选项卡, 输入 C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, 然后单击 "确定"。

4. 针对 PresentationFramework 重复:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll。

5. 针对 WindowsBase 重复:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll。

6. 针对 Uiautomationtypes.dll 重复:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll。

7. 针对 Uiautomationprovider.dll 重复:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll。

8. 单击 "**添加新引用**", 选择 "系统", 然后单击 **"确定"** 。

9. 单击 **"确定"** 退出用于添加引用的 Win32clock 属性页。

 最后, 将添加`STAThreadAttribute` `_tWinMain`到方法以便与一起[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

此属性告知公共语言运行时 (CLR) 当初始化组件对象模型 (COM) 时, 它应使用单线程单元模型 (STA), 这对于[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]) 是必需的。

## <a name="create-a-windows-presentation-framework-page"></a>创建 Windows Presentation Framework 页

接下来, 创建一个定义的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>DLL。 通常, 将创建[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>为独立应用程序, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]并编写和调试此部分。 完成后, 可以通过右键单击项目, 单击 "**属性**", 转到 "应用程序", 并将 "输出类型" 更改为 "Windows 类库", 将该项目转换为 DLL。

然后[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , 可以将 dll 项目[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]与项目 (一个包含两个项目的解决方案) 结合在一起-右键单击解决方案, 选择 " **Add\Existing 项目**"。

若要[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]从项目中使用该 dll, 需要添加引用:

1. 右键单击 "win32clock 项目", 然后选择 "**引用 ...** "。

2. 单击 "**添加新引用**"。

3. 单击“项目”选项卡。选择 WPFClock，单击“确定”。

4. 单击 **"确定"** 退出用于添加引用的 Win32clock 属性页。

## <a name="hwndsource"></a>HwndSource

接下来, 您<xref:System.Windows.Interop.HwndSource>将使用来[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使其<xref:System.Windows.Controls.Page>看起来像一个 HWND。 将此代码块添加到 C++ 文件中：

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;

    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
        HwndSource^ source = gcnew HwndSource(
            0, // class style
            WS_VISIBLE | WS_CHILD, // style
            0, // exstyle
            x, y, width, height,
            "hi", // NAME
            IntPtr(parent)        // parent window
            );

        UIElement^ page = gcnew WPFClock::Clock();
        source->RootVisual = page;
        return (HWND) source->Handle.ToPointer();
    }
}
}
```

 这是一长段代码，可以作一些解释。 第一部分是各种子句，无需完全限定所有调用：

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 然后定义一个函数, 用于创建[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内容, <xref:System.Windows.Interop.HwndSource>将其环绕, 然后返回 HWND:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

首先, 创建一个<xref:System.Windows.Interop.HwndSource>, 其参数与 CreateWindow 类似:

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

然后通过调用其[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]构造函数来创建内容类:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

然后, 将该页面连接到<xref:System.Windows.Interop.HwndSource>:

```cpp
source->RootVisual = page;
```

 在最后一行中, 返回的<xref:System.Windows.Interop.HwndSource>HWND:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>放置 Hwnd

现在, 你已拥有包含[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]时钟的 hwnd, 你需要将该 hwnd 放入[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]对话框中。 如果只知道放置 HWND 的位置, 只需将该大小和位置传递到前面定义的`GetHwnd`函数。 但是，由于已使用资源文件来定义对话框，因此你不完全确定任何 HWND 的放置位置。 可以使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]对话框编辑器[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]将静态控件放置在希望时钟进入的位置 ("在此处插入时钟"), 并[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用它来定位时钟。

在其中处理 WM_INITDIALOG 的情况下`GetDlgItem` , 你可以使用来检索占位符 STATIC 的 HWND:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

然后, 计算占位符的大小和位置, 以便可以[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]将该时钟放置在该位置:

RECT 矩形；

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

然后，你隐藏占位符 STATIC：

```cpp
ShowWindow(placeholder, SW_HIDE);
```

并在该[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]位置创建时钟 HWND:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

为了使本教程有趣, 并生成一个实际[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]时钟, 此时需要创建一个[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]时钟控件。 你可以在标记中执行大部分操作，代码隐藏中只有几个事件处理程序。 由于本教程介绍互操作性, 而不是关于控件设计的, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]因此在此处以代码块的形式提供了时钟的完整代码, 但没有用于构建或每个部分所代表的单独说明。 随意尝试此代码来更改控件的外观或功能。

此处为标记：

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

以下是附带的代码隐藏：

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

最终结果如下所示：

!["最终结果日期和时间属性" 对话框](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

若要将最终结果与生成此屏幕截图的代码进行比较, 请参阅[Win32 时钟互操作示例](https://go.microsoft.com/fwlink/?LinkID=160051)。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Interop.HwndSource>
- [WPF 和 Win32 互操作](wpf-and-win32-interoperation.md)
- [Win32 时钟互操作示例](https://go.microsoft.com/fwlink/?LinkID=160051)

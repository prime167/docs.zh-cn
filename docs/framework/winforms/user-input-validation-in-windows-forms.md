---
title: Windows 窗体中的用户输入验证
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: 7ee99d1b264f508882418c83da8e82759b0d95fa
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206132"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows 窗体中的用户输入验证
当用户将数据输入应用程序时, 可能需要在应用程序使用数据之前验证数据是否有效。 您可能要求某些文本字段的长度不能为零, 字段的格式设置为电话号码或其他类型格式的数据, 或者不包含任何可用于破坏数据库安全性的不安全字符的字符串。 Windows 窗体提供多种方式来验证应用程序中的输入。  
  
## <a name="validation-with-the-maskedtextbox-control"></a>MaskedTextBox 控件验证  
 如果需要要求用户以定义完善的格式输入数据, 如电话号码或部件号, 则可以通过使用<xref:System.Windows.Forms.MaskedTextBox>控件, 使用最少的代码来快速完成此过程。 *掩码*是由掩码语言中的字符组成的字符串, 用于指定可在文本框中的任何给定位置输入的字符。 控件向用户显示一组提示。 如果用户键入一个不正确的条目 (例如, 用户在需要数字时键入字母), 则控件将自动拒绝输入。  
  
 使用<xref:System.Windows.Forms.MaskedTextBox>的掩码语言非常灵活。 它允许你指定所需的字符、可选字符、文本字符, 如连字符和圆括号、货币字符和日期分隔符。 绑定到数据源时, 控件也能正常工作。 数据<xref:System.Windows.Forms.Binding.Format>绑定上的事件可用于重新设置传入数据的格式, 以符合掩码要求, 该<xref:System.Windows.Forms.Binding.Parse>事件可用于重新设置传出数据的格式, 以符合数据字段的规范。  
  
 有关详细信息, 请参阅[MaskedTextBox 控件](./controls/maskedtextbox-control-windows-forms.md)。  
  
## <a name="event-driven-validation"></a>事件驱动的验证  
 如果希望完全以编程方式控制验证, 或需要执行复杂的验证检查, 则应使用大多数 Windows 窗体控件中内置的验证事件。 接受自由格式用户输入的每个控件都有<xref:System.Windows.Forms.Control.Validating>一个事件, 每当控件需要数据验证时都会发生此事件。 <xref:System.Windows.Forms.Control.Validating>在事件处理方法中, 可以通过多种方式来验证用户输入。 例如, 如果您有一个必须包含邮政编码的文本框, 则可以通过以下方式执行验证:  
  
- 如果邮政编码必须属于特定的邮政编码组, 则可以对输入执行字符串比较, 以验证用户输入的数据。 例如, 如果邮政编码必须在集 {10001, 10002, 10003} 中, 则可以使用字符串比较来验证数据。  
  
- 如果邮政编码必须是特定的形式, 则可以使用正则表达式来验证用户输入的数据。 例如, 若要验证窗体`#####`或`#####-####`, 可以使用正则表达式`^(\d{5})(-\d{4})?$`。 若要验证窗`A#A #A#`体, 可以使用正则表达式`[A-Z]\d[A-Z] \d[A-Z]\d`。 有关正则表达式的详细信息, 请参阅[.NET Framework 正则表达式](../../standard/base-types/regular-expressions.md)和[正则表达式示例](../../standard/base-types/regular-expression-examples.md)。  
  
- 如果邮政编码必须是有效的美国邮政编码, 则可以调用 Zip 代码 Web 服务来验证用户输入的数据。  
  
 为事件提供类型<xref:System.ComponentModel.CancelEventArgs>的对象。 <xref:System.Windows.Forms.Control.Validating> 如果您确定控件的数据无效, 则可以通过将该对象的<xref:System.Windows.Forms.Control.Validating> <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>属性设置为来`true`取消该事件。 如果未设置<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>属性, Windows 窗体将假定该控件的验证成功, 并<xref:System.Windows.Forms.Control.Validated>引发事件。  
  
 有关验证中<xref:System.Windows.Controls.TextBox>的电子邮件地址的代码示例, 请参阅<xref:System.Windows.Forms.Control.Validating>。  
  
### <a name="data-binding-and-event-driven-validation"></a>数据绑定和事件驱动的验证  
 将控件绑定到数据源 (如数据库表) 时, 验证非常有用。 通过使用验证, 可以确保控件的数据满足数据源所需的格式, 并且不包含任何特殊字符 (如引号和可能不安全的反斜杠)。  
  
 使用数据绑定时, 控件中的数据将在<xref:System.Windows.Forms.Control.Validating>事件执行期间与数据源同步。 如果取消该<xref:System.Windows.Forms.Control.Validating>事件, 则数据不会与数据源同步。  
  
> [!IMPORTANT]
> 如果你具有在<xref:System.Windows.Forms.Control.Validating>事件发生后发生的自定义验证, 则它不会影响数据绑定。 例如, 如果在事件中有一个<xref:System.Windows.Forms.Control.Validated>尝试取消数据绑定的代码, 则仍将发生数据绑定。 在这种情况下, 若要在<xref:System.Windows.Forms.Control.Validated>事件中执行验证, 请将控件的 "**数据源更新模式**" 属性 (**在 "(数据绑定)** \\" 下, 从 " **OnValidation** " 更改为 "**从不**", 并添加 *控制*`.DataBindings["`yourfield'>`"].WriteValue()`验证代码。 *\<*  
  
### <a name="implicit-and-explicit-validation"></a>隐式和显式验证  
 那么, 何时验证控件的数据？ 这由开发人员来负责。 可以根据应用程序的需要, 使用隐式或显式验证。  
  
#### <a name="implicit-validation"></a>隐式验证  
 隐式验证方法会在用户输入数据时对数据进行验证。 在控件中输入数据时, 可以通过读取键来验证数据, 也可以在用户从一个控件中将输入焦点移到下一个控件时更常见地使用。 当你希望用户在工作时立即获得有关数据的反馈时, 此方法非常有用。  
  
 如果要对控件使用隐式验证, 则必须将控件的<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>属性设置为。 `true` 如果取消该<xref:System.Windows.Forms.Control.Validating>事件, 则将根据您分配给的值来<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>确定该控件的行为。 如果已分配<xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>, 则取消事件将<xref:System.Windows.Forms.Control.Validated>导致事件不会发生。 输入焦点将保留在当前控件上, 直到用户将数据更改为有效输入。 如果分配<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>了, 则<xref:System.Windows.Forms.Control.Validated>在取消事件时不会发生该事件, 但焦点仍将更改为下一个控件。  
  
 <xref:System.Windows.Forms.AutoValidate.Disable> 分配<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>给属性可防止隐式验证。 若要验证控件, 则必须使用显式验证。  
  
#### <a name="explicit-validation"></a>显式验证  
 显式验证方法一次验证数据。 您可以验证数据以响应用户操作, 例如单击 "保存" 按钮或 "下一步" 链接。 用户操作发生时, 可以通过以下方式之一触发显式验证:  
  
- 调用<xref:System.Windows.Forms.ContainerControl.Validate%2A>以验证最后一个控件失去焦点。  
  
- 调用<xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A>以验证窗体或容器控件中的所有子控件。  
  
- 调用自定义方法以手动验证控件中的数据。  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Windows 窗体控件的默认隐式验证行为  
 不同 Windows 窗体控件的<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>属性具有不同的默认值。 下表显示了最常见的控件及其默认值。  
  
|控件|默认验证行为|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Visual Studio 中未公开的属性|  
|<xref:System.Windows.Forms.ToolStripContainer>|Visual Studio 中未公开的属性|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>关闭窗体并重写验证  
 当控件由于其包含的数据无效而维持焦点时, 无法通过通常的方式之一关闭父窗体:  
  
- 单击 "**关闭**" 按钮。  
  
- 选择 "**系统**" 菜单中的 "**关闭**"。  
  
- 通过以编程<xref:System.Windows.Forms.Form.Close%2A>方式调用方法。  
  
 但是, 在某些情况下, 您可能需要让用户关闭窗体, 无论控件中的值是否有效。 您可以通过为窗体的<xref:System.Windows.Forms.Form.FormClosing>事件创建处理程序来覆盖验证并关闭仍包含无效数据的窗体。 在此事件中, 将<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>属性设置`false`为。 这会强制关闭窗体。 有关详细信息及示例，请参阅<xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>。  
  
> [!NOTE]
> 如果以这种方式强制关闭窗体, 则尚未保存窗体控件中的所有数据都将丢失。 此外, 模式窗体在关闭时不会验证控件的内容。 你仍可以使用控件验证将焦点锁定到控件, 但你不必担心与关闭窗体相关联的行为。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox 控件](./controls/maskedtextbox-control-windows-forms.md)
- [正则表达式示例](../../standard/base-types/regular-expression-examples.md)

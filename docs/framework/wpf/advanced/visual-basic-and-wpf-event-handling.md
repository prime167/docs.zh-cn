---
title: Visual Basic 和 WPF 事件处理
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 8407958ec76be7e402025ece57371e67581e5291
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942120"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic 和 WPF 事件处理
具体而言, 对于 Microsoft Visual Basic .net 语言, 可以使用特定`Handles`于语言的关键字将事件处理程序与实例关联, 而不是将事件处理程序附加到特性或<xref:System.Windows.UIElement.AddHandler%2A>使用方法。 但是，用于将处理程序附加到实例的 `Handles` 技术存在一些限制，因为 `Handles` 语法不支持 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件系统的某些特定路由事件功能。  
  
## <a name="using-handles-in-a-wpf-application"></a>在 WPF 应用程序中使用“Handles”  
 通过 `Handles` 连接到实例和事件的事件处理程序必须全部在实例的分部类声明中定义，此要求也适用于通过元素上的特性值进行分配的事件处理程序。 只能为`Handles` <xref:System.Windows.FrameworkContentElement.Name%2A>具有属性值 (或声明了[x:Name 指令](../../xaml-services/x-name-directive.md)) 的页上的元素指定。 这是因为中<xref:System.Windows.FrameworkContentElement.Name%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的会创建支持实例所必需的实例引用 *。* `Handles`语法所需的事件引用格式。 `Handles` 无<xref:System.Windows.FrameworkContentElement.Name%2A>需引用即可使用的唯一元素是用于定义分部类的根元素实例。  
  
 可以通过使用逗号分隔 `Handles` 后面的 Instance.Event 引用，向多个元素分配相同的处理程序。  
  
 可以使用 `Handles` 将多个处理程序分配给同一 Instance.Event 引用。 请勿对 `Handles` 引用中特定处理程序的提供顺序赋予任何重要性；应假定可按任何顺序调用处理相同事件的处理程序。  
  
 若要删除在声明中添加的`Handles`处理程序, 可以调用。 <xref:System.Windows.UIElement.RemoveHandler%2A>  
  
 如果要将处理程序附加到实例成员表中用于定义要处理的事件的实例，可使用 `Handles` 附加路由事件的处理程序。 对于路由事件, 附加了`Handles`的处理程序遵循的路由规则与作为[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]特性附加的处理程序或的公共签名<xref:System.Windows.UIElement.AddHandler%2A>相同。 这意味着, 如果事件已标记为已处理 (事件<xref:System.Windows.RoutedEventArgs.Handled%2A>数据中的属性为`True`), 则不会调用附加`Handles`的处理程序来响应该事件实例。 可通过路由中另一个元素上的实例处理程序，或通过在路由中当前元素或更早元素上进行类处理，将事件标记为已处理。 对于可支持成对的隧道事件/冒泡事件的输入事件，隧道路由可能已将事件对标记为已处理。 有关路由事件的详细信息，请参阅[路由事件概述](routed-events-overview.md)。  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>添加处理程序时的“Handles”限制  
 `Handles` 无法引用附加事件的处理程序。 必须对该附加事件使用 `add` 访问方法，或使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的 typename.eventname事件特性。 有关详细信息，请参阅[路由事件概述](routed-events-overview.md)。  
  
 对于路由事件，只能使用 `Handles` 为实例成员表中存在该事件的实例分配处理程序。 但是，对于一般的路由事件，父元素可以是来自子元素的事件的侦听器，即使该父元素的成员表中没有此事件也是如此。 在特性语法中，这可以通过 typename.membername 特性形式来指定，此形式限定哪种类型实际定义要处理的事件。 例如, 父代`Page` (没有`Click`定义事件) 可以通过在表单`Button.Click`中分配属性处理程序来侦听按钮单击事件。 但 `Handles` 不支持 typename.membername 形式，因为它必须支持与该形式冲突的 Instance.Event 形式。 有关详细信息，请参阅[路由事件概述](routed-events-overview.md)。  
  
 `Handles` 无法附加针对标记为已处理的事件而调用的处理程序。 相反, 您必须使用代码并调用`handledEventsToo`的<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>重载。  
  
> [!NOTE]
> 在 XAML 中为`Handles`同一事件指定事件处理程序时, 请不要在 Visual Basic 代码中使用语法。 在这种情况下，将调用事件处理程序两次。  
  
## <a name="how-wpf-implements-handles-functionality"></a>WPF 如何实现“Handles”功能  
 `Friend` `WithEvents` <xref:System.Windows.FrameworkContentElement.Name%2A> 编译页面时, 中间文件声明对页面上设置了属性 (或声明了 [x:Name](../../xaml-services/x-name-directive.md) 指令) 的每个元素的引用。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 每个命名实例都可能是可通过 `Handles` 分配给处理程序的元素。  
  
> [!NOTE]
> 在[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]中, IntelliSense 可以显示已完成的元素, 可`Handles`用于页面中的引用。 但是，这可能需要执行一个编译传递，以便中间文件可以填充所有 `Friends` 引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.UIElement.AddHandler%2A>
- [将路由事件标记为“已处理”和“类处理”](marking-routed-events-as-handled-and-class-handling.md)
- [路由事件概述](routed-events-overview.md)
- [XAML 概述 (WPF)](xaml-overview-wpf.md)

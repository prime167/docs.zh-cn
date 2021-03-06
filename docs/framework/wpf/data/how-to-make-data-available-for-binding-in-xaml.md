---
title: 如何：让数据可供 XAML 中的绑定使用
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 3487a160cc49ab6b779a20157668915c2da33900
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401489"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>如何：让数据可供 XAML 中的绑定使用
本主题讨论使数据可用于 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 绑定的各种方法，取决于应用程序的需求。  
  
## <a name="example"></a>示例  
 如果你要从[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]绑定到的公共语言运行时 (CLR) 对象, 则可以使对象可用于绑定的一种方法是将其定义为资源, 并为`x:Key`其提供。 以下示例中提供一个`Person`对象，它具有名为 `PersonName` 的字符串属性。           `Person`对象 (在突出显示且包含 `<src>` 元素的行中) 在名为 `SDKSample` 的命名空间中定义。  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 然后就可以将 <xref:System.Windows.Controls.TextBlock> 控件绑定到 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的对象，如突出显示的包含 `<TextBlock>` 元素的行所示。 
  
 或者，可以使用 <xref:System.Windows.Data.ObjectDataProvider> 类，如以下示例所示：  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 以相同的方式定义绑定，如突出显示的包含 `<TextBlock>` 元素的行所示。  
  
 在此特定示例中，结果是相同的：<xref:System.Windows.Controls.TextBlock> 的文本内容为 `Joe`。 但是，<xref:System.Windows.Data.ObjectDataProvider> 类还提供了其他功能，例如能够绑定到方法的结果。 如果需要 <xref:System.Windows.Data.ObjectDataProvider> 类提供的功能，则可以选用它。  
  
 但是，如果要绑定到已创建的对象，则需要在代码中设置 `DataContext`，如以下示例所示。  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 若要使用 <xref:System.Windows.Data.XmlDataProvider> 类访问 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 数据以进行绑定，请参阅[使用 XMLDataProvider 和 XPath 查询绑定到 XML 数据](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。 若要使用 <xref:System.Windows.Data.ObjectDataProvider> 类访问 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 数据以进行绑定，请参阅[绑定到 XDocument、XElement 或 LINQ for XML 查询结果](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。  
  
 有关指定要绑定到的数据的多种方法的相关信息，请参阅[指定绑定源](how-to-specify-the-binding-source.md)。 有关可以绑定到的数据类型或者如何实现您自己的公共语言运行时 (CLR) 对象进行绑定的信息, 请参阅[绑定源概述](binding-sources-overview.md)。  
  
## <a name="see-also"></a>请参阅

- [数据绑定概述](data-binding-overview.md)
- [帮助主题](data-binding-how-to-topics.md)

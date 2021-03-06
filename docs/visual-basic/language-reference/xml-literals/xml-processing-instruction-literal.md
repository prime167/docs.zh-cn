---
title: XML 处理指令文本 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: c589d3f4ac6bbb9aa9b2b8f2535888bddbf9c934
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958479"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML 处理指令文本 (Visual Basic)
表示<xref:System.Xml.Linq.XProcessingInstruction>对象的文本。  
  
## <a name="syntax"></a>语法  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>部件  
 `<?`  
 必需。 表示 XML 处理指令文本的开头。  
  
 `piName`  
 必需。 指示处理指令的目标应用程序的名称。 不能以 "xml" 或 "XML" 开头。  
  
 `piData`  
 可选。 字符串, 指示的`piName`目标应用程序应如何处理 XML 文档。  
  
 `?>`  
 必需。 表示处理指令的结束。  
  
## <a name="return-value"></a>返回值  
 一个 <xref:System.Xml.Linq.XProcessingInstruction> 对象。  
  
## <a name="remarks"></a>备注  
 XML 处理指令文本指示应用程序应如何处理 XML 文档。 当应用程序加载 XML 文档时, 应用程序可以检查 XML 处理指令以确定如何处理文档。 应用程序解释`piName`和`piData`的含义。  
  
 XML 文档文本使用类似于 XML 处理指令的语法。 有关详细信息, 请参阅[XML 文档文本](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。  
  
> [!NOTE]
> `piName`元素不能以字符串 "xml" 或 "xml" 开头, 因为 xml 1.0 规范保留这些标识符。  
  
 可以将 XML 处理指令文本分配给变量或将其包含在 XML 文档文本中。  
  
> [!NOTE]
> XML 文本可以跨多个行, 而不需要行继续符。 这使你可以从 XML 文档复制内容并将其直接粘贴到 Visual Basic 程序。  
  
 Visual Basic 编译器将 XML 处理指令文本转换为对<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>构造函数的调用。  
  
## <a name="example"></a>示例  
 下面的示例创建一个处理指令, 该指令标识 XML 文档的样式表。  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XProcessingInstruction>
- [XML 文档文本](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中创建 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

---
title: Select 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 087472c51d203be083fea0d39ade6f12066cfcb4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004748"
---
# <a name="select-clause-visual-basic"></a>Select 子句 (Visual Basic)
定义查询的结果。  
  
## <a name="syntax"></a>语法  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>部件  
 `var1`  
 可选。 可用于引用列表达式的结果的别名。  
  
 `fieldName1`  
 必需。 要在查询结果中返回的字段的名称。  
  
## <a name="remarks"></a>备注  
 您可以使用 `Select` 子句来定义从查询返回的结果。 这使您可以定义由查询创建的新匿名类型的成员，或指定查询所返回的命名类型的成员。 查询不需要 `Select` 子句。 如果未指定 `Select` 子句，则查询将基于为当前作用域标识的范围变量的所有成员返回一个类型。 有关详细信息，请参阅[匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。 当查询创建命名类型时，它将返回类型为 <xref:System.Collections.Generic.IEnumerable%601> 的结果，其中 @no__t 为创建的类型。  
  
 @No__t-0 子句可以引用当前作用域中的任何变量。 这包括 `From` 子句中标识的范围变量（或 `From` 子句）。 它还包括使用别名创建的任何新变量，这些变量由 `Aggregate`、`Let`、`Group By` 或 `Group Join` 子句创建，或者是查询表达式中先前 `Select` 子句中的变量。 @No__t-0 子句还可以包括静态值。 例如，下面的代码示例演示一个查询表达式，其中 `Select` 子句将查询结果定义为具有四个成员的新匿名类型： `ProductName`、`Price`、`Discount` 和 @no__t。 @No__t 0 和 @no__t 1 成员值取自 `From` 子句中定义的产品范围变量。 在 @no__t 子句中计算 @no__t 的成员值。 @No__t 0 成员是一个静态值。  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 @No__t-0 子句为后面的查询子句引入了一组新的范围变量，并且以前的范围变量不再位于范围内。 查询表达式中的最后一个 `Select` 子句决定了查询的返回值。 例如，以下查询将返回总计超过500的每个客户订单的公司名称和订单 ID。 第一个 `Select` 子句标识了 @no__t 子句和第二个 @no__t 为2子句的范围变量。 第二个 `Select` 子句将查询返回的值标识为新的匿名类型。  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 如果 @no__t 0 子句标识要返回的单个项，则查询表达式返回该项的类型的集合。 如果 `Select` 子句标识要返回的多个项，则查询表达式将返回基于选定项的新匿名类型的集合。 例如，以下两个查询根据 @no__t 的子句返回两个不同类型的集合。 第一个查询以字符串的形式返回公司名称的集合。 第二个查询返回使用公司名称和地址信息填充的 @no__t 0 对象的集合。  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>示例  
 下面的查询表达式使用 `From` 子句为 `customers` 集合声明范围变量 `cust`。 @No__t-0 子句选择客户名称和 ID 值，并填充新范围变量的 @no__t 1 和 @no__t 2 列。 @No__t-0 语句会遍历返回的每个对象，并为每个记录显示 @no__t 1 和 @no__t 2 列。  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

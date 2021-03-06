---
title: Take While 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004678"
---
# <a name="take-while-clause-visual-basic"></a>Take While 子句 (Visual Basic)
包括集合中指定条件为 `true` 的任何元素，并绕过剩余元素。  
  
## <a name="syntax"></a>语法  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`expression`|必需。 表示要为其测试元素的条件的表达式。 表达式必须返回 @no__t 0 值或函数等效项，例如，要将 `Integer` 计算为 `Boolean`。|  
  
## <a name="remarks"></a>备注  
 @No__t-0 子句包括从查询结果开始的元素，直到提供的 @no__t 返回 `false`。 @No__t 返回 `false` 后，查询将跳过所有剩余的元素。 对于剩余的结果，将忽略 `expression`。  
  
 @No__t-0 子句与 @no__t 子句不同，因为 `Where` 子句可用于包括查询中满足特定条件的所有元素。 @No__t-0 子句仅包含元素，直到第一次未满足条件。 当使用排序的查询结果时，`Take While` 子句最有用。  
  
## <a name="example"></a>示例  
 下面的代码示例使用 `Take While` 子句来检索结果，直到找到第一个不含任何订单的客户。  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)

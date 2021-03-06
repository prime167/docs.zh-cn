---
title: '- 运算符（Visual Basic）'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 5f6b6b67e2999d380cfca078a43162b3e1db2206
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701303"
---
# <a name="--operator-visual-basic"></a>- 运算符 (Visual Basic)
返回数值表达式的两个数值表达式或负值之间的差。  
  
## <a name="syntax"></a>语法  
  
```vb  
expression1 – expression2
```
  
或

```vb  
–expression1  
```  
  
## <a name="parts"></a>部件  
 `expression1`  
 必需。 任何数值表达式。  
  
 `expression2`  
 必需， `–`除非操作员计算负值。 任何数值表达式。  
  
## <a name="result"></a>结果  
 结果是`expression1`与`expression2`的差`expression1`或的求反值。  
  
 Result 数据类型是适用于`expression1`和`expression2`的数据类型的数值类型。 请参阅[运算符结果的数据类型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的 "整数算法" 表。  
  
## <a name="supported-types"></a>支持的类型  
 所有数值类型。 这包括无符号和浮点类型和`Decimal`。  
  
## <a name="remarks"></a>备注  
 在前面所示的语法中所示的第一个用法中，`–` 运算符是两个数值表达式之差的*二进制*算术减法运算符。  
  
 在前面所示的语法中所示的第二个用法中，`–` 运算符是表达式的负值的*一元*求反运算符。 在这种意义上，否定包含反转的符号`expression1` ，因此如果`expression1`为负，则结果为正。  
  
 如果其中一个表达式的计算结果为 [Nothing](../../../visual-basic/language-reference/nothing.md)，则 `–` 运算符将其视为零。  
  
> [!NOTE]
> @No__t-0 运算符可*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。 如果代码对这样的类或结构使用此运算符，请确保了解其重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`–`运算符计算并返回两个数字之间的差，然后对数字求反。  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 执行这些语句后，`binaryResult` 包含124.45，`unaryResult` 包含–334.90。  
  
## <a name="see-also"></a>请参阅

- [-= 运算符（Visual Basic）](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的算术运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

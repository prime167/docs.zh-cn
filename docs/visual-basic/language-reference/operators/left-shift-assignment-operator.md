---
title: < < = 运算符（Visual Basic）
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: aae71069bdcb88efa5842526dd7eb47806f248d0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701109"
---
# <a name="-operator-visual-basic"></a>\< @ no__t = 运算符（Visual Basic）
对变量或属性的值执行算术左移位，并将结果赋回变量或属性。  
  
## <a name="syntax"></a>语法  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>部件  
 `variableorproperty`  
 必需。 整型类型的变量或属性（`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 @no__t 7）。  
  
 `amount`  
 必需。 扩大到 `Integer` 的数据类型的数值表达式。  
  
## <a name="remarks"></a>备注  
 @No__t-0 运算符左侧的元素可以是简单的标量变量、属性或数组元素。 变量或属性不能是[只读](../../../visual-basic/language-reference/modifiers/readonly.md)的。  
  
 @No__t-0 运算符首先对变量或属性的值执行算术左移位运算。 然后，运算符将该操作的结果赋给该变量或属性。  
  
 算术移位不是循环的，这意味着，不会在另一端重新引入结果的末尾以外的位。 在算术左移位中，将丢弃超出结果数据类型范围的位，并将在右侧空出的位位置设置为零。  
  
## <a name="overloading"></a>重载  
 [< < 运算符](../../../visual-basic/language-reference/operators/left-shift-operator.md)可*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。 重载 `<<` 运算符会影响 @no__t 1 运算符的行为。 如果你的代码在重载 @no__t 的类或结构上使用 `<<=`，请确保了解其重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用 @no__t 0 运算符将 @no__t 1 变量的位模式向左移动指定的量，并将结果赋给该变量。  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>请参阅

- [<< 运算符](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [赋值运算符](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [移位运算符](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)

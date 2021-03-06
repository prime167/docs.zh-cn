---
title: 可以为 null 的值类型 - C# 编程指南
ms.custom: seodec18
description: 了解 C# 中可以为 null 的值类型及其使用方法
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#]
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: b8b52e7fb34adf65d5c76d59811ea6dd0ab16a98
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396215"
---
# <a name="nullable-value-types-c-programming-guide"></a>可以为 null 的值类型（C# 编程指南）

可以为 null 的值类型是 <xref:System.Nullable%601?displayProperty=nameWithType> 结构的实例。 可以为 null 的值类型可表示基础类型 `T` 的所有值，还可再表示一个 [null](../../language-reference/keywords/null.md) 值。 基础类型 `T` 可以是任何不可为 null 的[值类型](../../language-reference/keywords/value-types.md)。 `T` 不能是引用类型。

> [!NOTE]
> C# 8.0 引入了可为空引用类型功能。 有关详细信息，请参阅[可为空引用类型](../../nullable-references.md)。 自 C# 2 起，提供可以为 null 的值类型。

例如，可以将 `null` 或任何整数值（从 <xref:System.Int32.MinValue?displayProperty=nameWithType> 到 <xref:System.Int32.MaxValue?displayProperty=nameWithType>）赋给 `Nullable<int>`，并可将 [true](../../language-reference/keywords/true-literal.md)[false](../../language-reference/keywords/false-literal.md) 或 `null` 赋给`Nullable<bool>`。

需要表示基础类型的未定义的值时，请使用可以为 null 的值类型。 布尔变量只能有两个值：`true` 和 `false`。 没有“未定义”的值。 在许多编程应用程序中，尤其是数据库交互中，变量值可能未定义或缺失。 例如，数据库中的字段可能包含值 true 或 false，但它也可能根本不包含任何值。 这种情况下要使用 `Nullable<bool>` 类型。

可以为 null 的值类型具有以下特征：

- 可以为 null 的值类型表示可向其赋值 `null` 的值类型变量。

- 语法 `T?` 是 `Nullable<T>` 的简写。 这两种形式是可互换的。

- 向可以为 null 的值类型赋值的方法与向基础值类型赋值的方法相同：`int? x = 10;` 或 `double? d = 4.108;`。 还可赋予 `null` 值：`int? x = null;`。

- 使用 <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 和 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 只读属性可测试是否存在 null 值并检索值，如以下示例所示：`if (x.HasValue) y = x.Value;`

  - 如果变量包含值，则 <xref:System.Nullable%601.HasValue%2A> 属性返回 `true`；如果值为 `null`，则返回 `false`。

  - 如果 <xref:System.Nullable%601.HasValue%2A> 返回 `true`，则 <xref:System.Nullable%601.Value%2A> 属性返回值。 否则会引发 <xref:System.InvalidOperationException>。

- 还可将 `==` 和 `!=` 运算符用于可以为 null 的值类型，如以下示例所示：`if (x != null) y = x.Value;`。 如果 `a` 和 `b` 均为 null，则 `a == b` 的计算结果为 `true`。

- 从 C# 7.0 开始，可以使用[模式匹配](../../pattern-matching.md#the-is-type-pattern-expression)来检查和获取可以为 null 的类型的值：`if (x is int valueOfX) y = valueOfX;`。

- `T?` 的默认值是一个实例，其 <xref:System.Nullable%601.HasValue%2A> 属性返回 `false`。

- 使用 <xref:System.Nullable%601.GetValueOrDefault> 方法可返回赋予的值，如果可以为 null 的类型的值为 `null`，它还可返回基础值类型的[默认](../../language-reference/keywords/default-values-table.md)值。

- 使用 <xref:System.Nullable%601.GetValueOrDefault(%600)> 方法可返回赋予的值，如果可以为 null 的类型的值为 `null`，它还可返回提供的默认值。

- 借助 [null 合并运算符](../../language-reference/operators/null-coalescing-operator.md) `??`，基于可以为 null 类型值向基础值类型的变量赋值：`int? x = null; int y = x ?? -1;`。 在示例中，由于 `x` 为 `null`，因此 `y` 的结果值为 `-1`。

- 如果在两种值类型之间定义了用户定义的转换，则还可将同一转换用于相应的可以为 null 的类型。

- 不得嵌套可以为 null 的值类型。 不会编译下面的一行代码：`Nullable<Nullable<int>> n;`

有关详细信息，请参阅[使用可以为 null 的值类型](using-nullable-types.md)以及[如何：标识可以为 null 的值类型](how-to-identify-a-nullable-type.md)主题。

## <a name="see-also"></a>请参阅

- [C# 编程指南](../index.md)
- [??运算符](../../language-reference/operators/null-coalescing-operator.md)
- [可以为 Null 的值类型 (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>

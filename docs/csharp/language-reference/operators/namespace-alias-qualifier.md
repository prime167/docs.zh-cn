---
title: ':: 运算符 - C# 参考'
ms.custom: seodec18
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2aceb51747708b12fb3059b097b72206c78a9d5d
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971242"
---
# <a name="-operator-c-reference"></a>:: 运算符（C# 参考）

使用命名空间别名限定符 `::` 访问已设置别名的命名空间的成员。 使用两个标识符之间的 `::` 限定符。 左侧标识符可以是以下任意别名：

- 使用 [using 别名指令](../keywords/using-directive.md)创建的命名空间别名：
  
  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- [外部别名](../keywords/extern-alias.md)。
- `global` 别名，该别名是全局命名空间别名。 全局命名空间是包含未在命名空间中声明的命名空间和类型的命名空间。 与 `::` 限定符一起使用时，`global` 别名始终引用全局命名空间，即使存在用户定义的 `global` 命名空间别名也是如此。
  
  以下示例使用 `global` 别名访问 .NET <xref:System> 命名空间，该命名空间是全局命名空间的成员。 如果没有 `global` 别名，则将访问用户定义的 `System` 命名空间（该命名空间是 `MyCompany.MyProduct` 命名空间的成员）：

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }
  
      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```
  
  > [!NOTE]
  > 仅当 `global` 关键字是 `::` 限定符的左侧标识符时，该关键字才是全局命名空间别名。

你还可以使用[成员访问 `.` 运算符](member-access-operators.md#member-access-operator-)来访问别名命名空间的成员。 但是，`.` 运算符还用于访问类型的成员。 `::` 限定符确保其左侧标识符始终引用命名空间别名，即使存在同名的类型或命名空间也是如此。

## <a name="c-language-specification"></a>C# 语言规范

有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[命名空间别名限定符](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers)部分。

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 运算符](index.md)
- [using 命名空间](../../programming-guide/namespaces/using-namespaces.md)

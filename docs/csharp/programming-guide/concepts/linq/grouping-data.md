---
title: 对数据分组 (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 15dafdb144ee9fd4184d4c8281d041e03161a16b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594201"
---
# <a name="grouping-data-c"></a>对数据分组 (C#)
分组是指将数据分到不同的组，使每组中的元素拥有公共的属性。  
  
 下图演示了对字符序列进行分组的结果。 每个组的键是字符。  
  
 ![关系图显示 LINQ 分组操作。](./media/grouping-data/linq-group-operation.png)  
  
 下一节列出了对数据元素进行分组的标准查询运算符方法。  
  
## <a name="methods"></a>方法  
  
|方法名|说明|C# 查询表达式语法|详细信息|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|对共享通用属性的元素进行分组。 每组由一个 <xref:System.Linq.IGrouping%602> 对象表示。|`group … by`<br /><br /> -或-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|将元素插入基于键选择器函数的 <xref:System.Linq.Lookup%602>（一种一对多字典）。|不适用。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>查询表达式语法示例  
 下列代码示例根据奇偶性，使用 `group by` 子句对列表中的整数进行分组。  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Linq>
- [标准查询运算符概述 (C#)](./standard-query-operators-overview.md)
- [group 子句](../../../language-reference/keywords/group-clause.md)
- [如何：创建嵌套组](../../linq-query-expressions/how-to-create-a-nested-group.md)
- [如何：按扩展名对文件进行分组 (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)
- [如何：对查询结果进行分组](../../linq-query-expressions/how-to-group-query-results.md)
- [如何：对分组操作执行子查询](../../linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
- [如何：使用组将一个文件拆分成多个文件 (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)

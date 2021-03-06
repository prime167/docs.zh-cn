---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: d54c350196ad1ef7cfafa6d931d9d1ad8f267177
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250560"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
确定查询表达式是否为 null。  
  
## <a name="syntax"></a>语法  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>自变量  
 `expression`  
 任何有效的查询表达式。 不可以是集合，不可含有集合成员，也不可以是具有集合类型属性的记录类型。  
  
 NOT  
 对 IS NULL 的 EDM.Boolean 结果取反。  
  
## <a name="return-value"></a>返回值  
 如果 `true` 返回 null，则为 `expression`；否则为 `false`。  
  
## <a name="remarks"></a>备注  
 使用 `IS NULL` 可确定外部联接的元素是否为 null：  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 使用 `IS NULL` 可确定成员是否有实际值：  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 下表显示了 `IS NULL` 对于某些模式的行为。 所有异常都在调用提供程序之前从客户端引发：  
  
|模式|行为|  
|-------------|--------------|  
|null IS NULL|返回 `true`。|  
|TREAT (null AS EntityType) IS NULL|返回 `true`。|  
|TREAT (null AS ComplexType) IS NULL|引发错误。|  
|TREAT (null AS RowType) IS NULL|引发错误。|  
|EntityType IS NULL|返回 `true` 或 `false`。|  
|ComplexType IS NULL|引发错误。|  
|RowType IS NULL|引发错误。|  
  
## <a name="example"></a>示例  
 下面的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询使用 IS NOT NULL 运算符来确定查询表达式是否不为 null。 此查询基于 AdventureWorks 销售模型。 若要编译并运行此查询，请执行下列步骤：  
  
1. [按照如何：执行返回 StructuralType 结果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查询。  
  
2. 将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>请参阅

- [实体 SQL 引用](entity-sql-reference.md)

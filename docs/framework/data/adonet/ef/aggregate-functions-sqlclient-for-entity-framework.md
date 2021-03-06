---
title: 聚合函数（用于实体框架的 SqlClient）
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 3dbd4c0a24a5fc41153ea16747325e824669b0e5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700046"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>聚合函数（用于实体框架的 SqlClient）
SQL Server .NET Framework 数据提供程序 (SqlClient) 提供聚合函数。 聚合函数对一组输入值执行计算并返回一个值。 这些函数位于 SqlServer 命名空间中，该命名空间在您使用 SqlClient 时可用。 提供程序的命名空间属性使实体框架可以确定此提供程序对特定构造（如类型和函数）使用哪个前缀。  
  
 下面是 SqlClient 聚合函数。  

## <a name="avgexpression"></a>AVG （expression）

返回集合中各值的平均值。 空值将被忽略。

**参数**

@No__t-0、`Int64`、`Double` 和 @no__t。

**返回值**

`expression` 的类型。

**示例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG （集合）
 
 返回集合中各值的校验和。 空值将被忽略。
 
 **参数**
 
 集合（`Int32`）。
 
 **返回值**
 
 一个 `Int32`。
 
 **示例**
 
[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a>COUNT （expression）

以 `Int32` 形式返回集合中的项数。

**参数**

集合 @ no__t-0T >，其中 T 为以下类型之一：

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` （在 SQL Server 2000 中未返回）|

**返回值**

一个 `Int32`。

**示例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]
 
## <a name="count_bigexpression"></a>COUNT_BIG （expression）
 
以 `bigint` 形式返回集合中的项数。
 
 **参数**
 
 集合（T），其中 T 为以下类型之一：
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` （在 SQL Server 2000 中未返回）|

**返回值**

一个 `Int64`。

**示例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX （expression）

返回集合中的最大值。

**参数**

集合（T），其中 T 为以下类型之一： 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**返回值**

`expression` 的类型。

**示例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN （expression）

返回集合中的最小值。

**参数**

集合（T），其中 T 为以下类型之一： 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**返回值**

`expression` 的类型。

**示例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV （expression）

返回指定表达式中所有值的统计标准偏差。

**参数**

集合（`Double`）。

**返回值**

`Double`。

**示例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDEVP （expression）

返回指定表达式中所有值的总体标准偏差。

**参数**

集合（`Double`）。

**返回值**

`Double`。

**示例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM （expression）

返回集合中所有值的总和。

**参数**

集合（T），其中 T 为以下类型之一： `Int32`，`Int64`，`Double`，@no__t 为3。

**返回值**

`expression` 的类型。

**示例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR （expression）

返回指定表达式中所有值的方差。

**参数**

集合（`Double`）。

**返回值**

`Double`。

**示例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP （expression）

返回指定表达式中所有值的总体方差。

**参数**

集合（`Double`）。

**返回值**

`Double`。

**示例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a>请参阅

- [聚合函数（Transact-sql）](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [实体 SQL 语言](./language-reference/entity-sql-language.md)
- [聚合 Canonical 函数](./language-reference/aggregate-canonical-functions.md)

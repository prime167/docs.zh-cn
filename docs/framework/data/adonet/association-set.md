---
title: Association Set — 关联集
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 43ab6cf9f1ee8cb971810add6b9a89467726f3e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785039"
---
# <a name="association-set"></a>Association Set — 关联集
*关联集*是同一类型的[关联](association-type.md)实例的逻辑容器。 关联集不是一种数据建模构造，也就是说，它没有描述数据结构或关系。 相反，关联集提供了一种承载或存储环境构造（例如公共语言运行库或 SQL Server 数据库）来分组关联实例，以便可以将它们映射到某个数据存储区。  
  
 关联集是在实体容器中定义的，[实体容器](entity-container.md)是[实体集](entity-set.md)和关联集的逻辑分组。  
  
 关联集的定义包含以下信息：  
  
- 关联集名称。 （必需）  
  
- 要包含其实例的关联。 （必需）  
  
- 两个[关联集结束](association-set-end.md)。  
  
## <a name="example"></a>示例  
 下图显示了一个具有两个关联的概念模型：`PublishedBy` 和 `WrittenBy`。 上图没有传达有关关联集的信息，但下图显示了一个基于此模型的关联集和实体集的示例。  
  
 ![具有三个实体类型的示例模型](./media/association-set/example-model-three-entity-types.gif)  
  
 下面的示例显示了基于上面所示的概念模型的一个关联集 (`PublishedBy`) 和两个实体集（`Books` 和 `Publishers`）。 实体集中的`Books` Bi 表示运行时`Book`实体类型的实例。 同样，Pj 表示`Publisher` `Publishers`实体集中的实例。 BiPj 表示`PublishedBy` `PublishedBy`关联集中关联的实例。  
  
 ![显示集合示例的屏幕截图。](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET 实体框架](./ef/index.md)使用一种称为概念架构定义语言（[CSDL](./ef/language-reference/csdl-specification.md)）的域特定语言（DSL）来定义概念模型。 下面的 CSDL 定义了一个实体容器，其中对于上图所示的每个关联都有一个关联集。 请注意，每个关联集的名称和关联都是使用 XML 特性定义的。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 只要没有两个关联集共享一个[关联集端](association-set-end.md)，就可以为每个关联定义多个关联集。 下面的 CSDL 定义了一个实体容器，其中包含 `WrittenBy` 关联的两个关联集。 请注意，为 `Book` 和 `Author` 实体类型定义了多个实体集，并且没有关联集共享关联集端。  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>请参阅

- [实体数据模型关键概念](entity-data-model-key-concepts.md)
- [实体数据模型](entity-data-model.md)
- [外键属性](foreign-key-property.md)

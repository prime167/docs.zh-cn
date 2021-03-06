---
title: IReferenceIdentity 接口
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796356"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity 接口
表示对代码对象的唯一签名的引用。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|获取一个指向与此`IReferenceIdentity` `IReferenceIdentity`相同的新实例的接口指针，指定的特性更改除外。|  
|`IReferenceIdentity::EnumAttributes`|获取一个接口指针，该`IEnumIDENTITY_ATTRIBUTE`指针指向包含与此`IReferenceIdentity`关联的特性的实例。|  
|`IReferenceIdentity::GetAttribute`|获取指定命名空间中具有指定名称的特性的值。|  
|`IReferenceIdentity::SetAttribute`|将具有指定命名空间和指定名称的特性设置为指定值。|  
  
## <a name="requirements"></a>要求  
 **适用**请参阅[系统需求](../../get-started/system-requirements.md)。  
  
 **标头：** 隔离。h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [合成接口](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE 接口](ienumidentity-attribute-interface.md)

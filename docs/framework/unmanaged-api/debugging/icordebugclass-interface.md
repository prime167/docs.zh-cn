---
title: ICorDebugClass 接口
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5099af23a2b706694bfcb655d295607c97ea8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969272"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass 接口

表示基类型或复杂类型（即用户定义的类型）。 如果该类型为泛型类型，则 `ICorDebugClass` 表示实例化的泛型类型。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|获取定义此类的模块。|  
|[GetStaticFieldValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|获取指定的静态字段的值。|  
|[GetToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|获取此`TypeDef`类的元数据标记。|  
  
## <a name="remarks"></a>备注  
 `ICorDebugClass`接口表示未实例化的泛型类型。 ICorDebugType 接口表示一个实例化的泛型类型。 例如, `Hashtable<K, V>`将由`ICorDebugClass`表示`Hashtable<Int32, String>` ,`ICorDebugType`而将由表示。  
  
 非泛型类型由`ICorDebugClass`和`ICorDebugType`表示。 后一种接口在 .NET Framework 版本2.0 中引入, 用于处理类型实例化。  
  
> [!NOTE]
> 此接口不支持跨计算机或跨进程远程调用。  
  
## <a name="requirements"></a>要求  
 **适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cordebug.idl, Cordebug.idl  
  
 **类库**CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

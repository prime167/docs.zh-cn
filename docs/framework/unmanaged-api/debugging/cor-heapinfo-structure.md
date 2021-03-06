---
title: COR_HEAPINFO 结构
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7b340a73aa9eaebca9c0d78563ae298557039b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274193"
---
# <a name="cor_heapinfo-structure"></a>COR_HEAPINFO 结构
提供有关垃圾回收堆的常规信息，包括它是否是可枚举的。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`areGCStructuresValid`|`true`如果垃圾回收结构有效并且可以枚举堆，则为;否则为`false`。|  
|`pointerSize`|目标体系结构上指针的大小（以字节为单位）。|  
|`numHeaps`|进程中逻辑垃圾回收堆的数目。|  
|`concurrent`|`TRUE`如果启用并发（后台）垃圾回收，则为;否则为`FALSE`。|  
|`gcType`|[CorDebugGCType](cordebuggctype-enumeration.md)枚举的成员，它指示垃圾回收器是在工作站上运行还是在服务器上运行。|  
  
## <a name="remarks"></a>备注  
 使用`COR_HEAPINFO` [ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md)方法返回结构的实例。  
  
 枚举垃圾回收堆上的对象之前，必须始终检查`areGCStructuresValid`字段以确保堆处于可枚举状态。 有关详细信息，请参阅[ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md)方法。  
  
## <a name="requirements"></a>要求  
 **适用**请参阅[系统需求](../../get-started/system-requirements.md)。  
  
 **标头：** Cordebug.idl，Cordebug.idl  
  
 **类库**CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试结构](debugging-structures.md)
- [调试](index.md)

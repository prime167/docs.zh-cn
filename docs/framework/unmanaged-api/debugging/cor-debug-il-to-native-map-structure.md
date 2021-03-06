---
title: COR_DEBUG_IL_TO_NATIVE_MAP 结构
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: babb1ace1385c241b782691f22bfb4fbb689e310
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274075"
---
# <a name="cor_debug_il_to_native_map-structure"></a>COR_DEBUG_IL_TO_NATIVE_MAP 结构
包含用于将 Microsoft 中间语言 (MSIL) 代码映射到本机代码的偏移量。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`ilOffset`|MSIL 代码的偏移量。|  
|`nativeStartOffset`|本机代码起始位置的偏移量。|  
|`nativeEndOffset`|本机代码末尾的偏移量。|  
  
## <a name="requirements"></a>要求  
 **适用**请参阅[系统需求](../../get-started/system-requirements.md)。  
  
 **标头：** Corprof.idl、Cordebug.idl  
  
 **类库**CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [GetILToNativeMapping 方法](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [GetILToNativeMapping 方法](icordebugcode-getiltonativemapping-method.md)
- [调试结构](debugging-structures.md)
- [调试](index.md)

---
title: ICorDebugModule 接口
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dce4f5859568c1288610e171286a5919dc8b19b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962434"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule 接口

表示公共语言运行时 (CLR) 模块, 该模块可以是可执行文件或动态链接库 (DLL)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|未实现。|  
|[EnableClassLoadCallbacks 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|确定是否为此模块调用[ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)和[ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)回调。|  
|[EnableJITDebugging 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|确定实时 (JIT) 编译器是否保留此模块内方法的调试信息。|  
|[GetAssembly 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|获取包含此模块的程序集。|  
|[GetBaseAddress 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|获取模块的基址。|  
|[GetClassFromToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|从元数据中获取 ICorDebugClass。|  
|[GetEditAndContinueSnapshot 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|已否决。|  
|[GetFunctionFromRVA 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|未实现。|  
|[GetFunctionFromToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|获取元数据标记指定的函数。|  
|[GetGlobalVariableValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|获取指定全局变量的值对象。|  
|[GetMetaDataInterface 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|获取可用于检查模块的元数据的元数据接口指针。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|获取模块的文件名。|  
|[GetProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|获取此模块的包含进程。|  
|[GetSize 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|获取模块的大小 (以字节为单位)。|  
|[GetToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|获取此模块的表项的标记。|  
|[IsDynamic 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|指示模块是否为动态模块。|  
|[IsInMemory 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|指示此模块是否仅存在于内存中。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
> 此接口不支持跨计算机或跨进程远程调用。  
  
## <a name="requirements"></a>要求  
 **适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cordebug.idl, Cordebug.idl  
  
 **类库**CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebug 接口](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

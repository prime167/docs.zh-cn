---
title: ICorDebugController::Detach 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f687e48413cb227ad715720e24bd645065309553
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748841"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach 方法
从分离调试器进程或应用程序域。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>备注  
 进程或应用程序域将继续执行正常，但"ICorDebugProcess"或"ICorDebugAppDomain"对象不再有效，会进行任何进一步的回调。  
  
 在.NET Framework 2.0 版中，如果启用非托管调试，则此方法将失败由于操作系统限制。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

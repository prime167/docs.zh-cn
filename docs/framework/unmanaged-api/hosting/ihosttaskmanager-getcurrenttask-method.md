---
title: IHostTaskManager::GetCurrentTask 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3044927e0d9975ed9347cd4f4896b3b75d3e29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749632"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a>IHostTaskManager::GetCurrentTask 方法
获取从其进行此调用的操作系统线程当前正在执行的任务的接口指针。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a>参数  
 `pTask`  
 [out]指向的地址的指针[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)实例，它表示当前正在执行的任务中，则为 null，如果没有任何任务当前正在执行。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetCurrentTask` 已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。|  
|HOST_E_TIMEOUT|呼叫已超时。|  
|HOST_E_NOT_OWNER|调用方不拥有该锁。|  
|HOST_E_ABANDONED|事件已取消时被阻塞的线程或纤程正在等待它。|  
|E_FAIL|发生未知的灾难性故障。 如果某方法返回 E_FAIL，CLR 不再在进程内可用。 对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_INVALIDOPERATION|`GetCurrentTask` 主机控件范围之外的操作系统线程上调用。|  
  
## <a name="remarks"></a>备注  
 主机还可以设置`pTask`参数为 null，以防止它未启动的任务输入 CLR。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRTask 接口](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 接口](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 接口](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 接口](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

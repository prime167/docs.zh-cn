---
title: PreBindAssemblyEx 函数
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aa2d174200db76f5c7a6db43e14bb6904604226
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796338"
---
# <a name="prebindassemblyex-function"></a>PreBindAssemblyEx 函数
获取程序集的策略后显示名称。  
  
 此函数支持 .NET Framework 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a>参数  
 `pAppCtx`  
 中标识应用程序上下文。  
  
 `pName`  
 中标识程序集名称。  
  
 `pAsmParent`  
 中标识父程序集。 忽略此参数。  
  
 `pwzRuntimeVersion`  
 中标识运行时版本。  
  
 `ppNamePostPolicy`  
 弄包含策略后显示名称。  
  
 `pvReserved`  
 中保留以供将来进行扩展。 `pvReserved`必须为空引用。  
  
## <a name="remarks"></a>备注  
 仅当函数返回 HRESULT FUSION_E_REF_DEF_MISMATCH 时才设置output参数。`ppNamePostPolicy` 否则为 null。  
  
## <a name="requirements"></a>要求  
 **适用**请参阅[系统需求](../../get-started/system-requirements.md)。  
  
 **标头：** 合成。h  
  
 **类库**作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [合成全局静态函数](fusion-global-static-functions.md)

---
title: GetHistoryFileDirectory 函数
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adbbf94dc36c6d82360ed532b283cd666a1a52ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796848"
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory 函数
检索应用程序历史记录目录的路径。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a>参数  
 `wzDir`  
 弄用于保存应用程序历史记录目录路径的缓冲区。  
  
 `pdwSize`  
 [in，out]缓冲区的长度。  
  
## <a name="return-value"></a>返回值  
 除以下值外，此方法还返回 Winerror.h 文件中定义的标准 COM 错误代码。  
  
|返回代码|描述|  
|-----------------|-----------------|  
|S_OK|该方法已成功完成。|  
|E_INVALIDARG|`wzDir`或`pdwSize`为 null，或者版本字符串不正确。|  
  
## <a name="remarks"></a>备注  
 成功完成后， `pdwSize`参数设置为路径字符串的长度。  
  
## <a name="requirements"></a>要求  
 **适用**请参阅[系统需求](../../get-started/system-requirements.md)。  
  
 **标头：** 合成。h  
  
 **类库**合成 .dll 和 Mscorwks.dll。 使用 Mscorwks.dll 而不是来确保目标为正确的 .NET Framework 版本。  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [CreateHistoryReader 函数](createhistoryreader-function.md)
- [NukeDownloadedCache 函数](nukedownloadedcache-function.md)
- [合成全局静态函数](fusion-global-static-functions.md)

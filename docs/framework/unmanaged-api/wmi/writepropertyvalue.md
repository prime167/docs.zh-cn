---
title: WritePropertyValue 函数（非托管 API 参考）
description: WritePropertyValue 函数将字节写入属性。
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3c42129835f9b30bed493a0992d49d7e2a458e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798180"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue 函数
将指定数量的字节写入由属性句柄标识的属性。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a>参数

`vFunc`  
中此参数未使用。

`ptr`  
中指向[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)实例的指针。

`lHandle`  
中一个整数，其中包含用于标识此属性的句柄。 可以通过调用[GetPropertyHandle](getpropertyhandle.md)函数来检索句柄。   

`lNumBytes`  
中要写入属性的字节数。 有关详细信息，请参阅 "[备注](#remarks)" 部分。

`pHandle`   
弄指向包含数据的字节数组的指针。

## <a name="return-value"></a>返回值

此函数返回的以下值是在*WbemCli*头文件中定义的，也可以在代码中将它们定义为常量：

|返回的常量  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 参数无效。 |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | 出现类型不匹配。 |
|`WBEM_S_NO_ERROR` | 0 | 函数调用成功。  |
  
## <a name="remarks"></a>备注

此函数包装对[IWbemClassObject：： WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)方法的调用。

使用此函数可设置字符串和所有其他非`DWORD` `QWORD`数据或非数据。

对于非字符串属性值， `lNumBytes`必须是指定的属性类型的正确数据大小。 对于字符串属性值， `lNumBytes`必须为指定字符串的长度（以字节为单位），并且字符串本身的长度必须为偶数（以字节为单位），后跟 null 终止字符。

## <a name="requirements"></a>要求  
**适用**请参阅[系统需求](../../get-started/system-requirements.md)。  
  
 **标头：** WMINet_Utils.idl  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>请参阅

- [WMI 和性能计数器（非托管 API 参考）](index.md)

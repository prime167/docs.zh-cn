---
title: LoadTypeLibWithResolver 函数
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b78789344050fd5e1cb0ee3492bf330fbf92bc88
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798933"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver 函数
加载类型库，并使用提供的[ITypeLibResolver 接口](itypelibresolver-interface.md)解析任何内部引用的类型库。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>参数  
 `szFile`  
 中类型库的文件路径。  
  
 `regkind`  
 中用于控制如何注册类型库的[REGKIND 枚举](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind)标志。 其可能的值为：  
  
- `REGKIND_DEFAULT`：使用默认注册行为。  
  
- `REGKIND_REGISTER`：注册此类型库。  
  
- `REGKIND_NONE`：不要注册此类型库。  
  
 `pTlbResolver`  
 中指向[ITypeLibResolver 接口](itypelibresolver-interface.md)的实现的指针。  
  
 `pptlib`  
 弄对正在加载的类型库的引用。  
  
## <a name="return-value"></a>返回值  
 下表中列出的其中一个 HRESULT 值。  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|内存不足。|  
|`E_POINTER`|一个或多个指针无效。|  
|`E_INVALIDARG`|一个或多个参数无效。|  
|`TYPE_E_IOERROR`|函数无法写入文件。|  
|`TYPE_E_REGISTRYACCESS`|无法打开系统注册数据库。|  
|`TYPE_E_INVALIDSTATE`|无法打开类型库。|  
|`TYPE_E_CANTLOADLIBRARY`|未能加载类型库或 DLL。|  
  
## <a name="remarks"></a>备注  
 [Tlbexp.exe （类型库导出程序）](../../tools/tlbexp-exe-type-library-exporter.md)在程序集到`LoadTypeLibWithResolver`类型库转换过程中调用函数。  
  
 此函数加载指定的类型库，并对注册表的访问权限降至最低。 然后，该函数检查类型库以查找内部引用的类型库，其中每个库必须加载并添加到父类型库中。  
  
 在可以加载引用的类型库之前，必须将其引用文件路径解析为完整文件路径。 这是通过[ITypeLibResolver 接口](itypelibresolver-interface.md)提供的`pTlbResolver` [ResolveTypeLib 方法](resolvetypelib-method.md)实现的，该方法是在参数中传递的。  
  
 当所引用的类型库的完整文件路径已知时， `LoadTypeLibWithResolver`函数将加载引用的类型库并将其添加到父类型库中，从而创建组合的主类型库。  
  
 函数解析并加载所有内部引用的`pptlib`类型库后，将在参数中返回对主解析类型库的引用。  
  
 函数通常由[tlbexp.exe （类型库导出程序）](../../tools/tlbexp-exe-type-library-exporter.md)调用，后者在`pTlbResolver`参数中提供自己的内部[ITypeLibResolver 接口](itypelibresolver-interface.md)实现。 `LoadTypeLibWithResolver`  
  
 如果直接调用`LoadTypeLibWithResolver` ，则必须提供自己的[ITypeLibResolver 接口](itypelibresolver-interface.md)实现。  
  
## <a name="requirements"></a>要求  
 **适用**请参阅[系统需求](../../get-started/system-requirements.md)。  
  
 **标头：** TlbRef  
  
 **类库**TlbRef.lib  
  
 **.NET Framework 版本：** 3.5、3.0、2。0  
  
## <a name="see-also"></a>请参阅

- [Tlbexp Helper 函数](index.md)
- [LoadTypeLibEx 函数](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)

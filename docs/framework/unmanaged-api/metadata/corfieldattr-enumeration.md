---
title: CorFieldAttr 枚举
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e909680428c7957da2283d13f5676329d953bf22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781895"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr 枚举
包含一些值，用于描述字段的相应元数据。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`fdFieldAccessMask`|指定可访问性信息。|  
|`fdPrivateScope`|指定不能引用的字段。|  
|`fdPrivate`|指定字段只能由其父类型访问。|  
|`fdFamANDAssem`|指定字段是由其程序集中的派生类可访问。|  
|`fdAssembly`|指定该字段是可由其程序集中的所有类型访问。|  
|`fdFamily`|指定该字段只能由其类型访问和派生类。|  
|`fdFamORAssem`|指定该字段可由派生类中它的程序集的所有类型访问。|  
|`fdPublic`|指定字段具有可见性的所有类型，此作用域的访问。|  
|`fdStatic`|指定字段及其类型的成员，而不是实例成员。|  
|`fdInitOnly`|指定在初始化后，无法更改该字段。|  
|`fdLiteral`|指定字段值是一个编译时常量。|  
|`fdNotSerialized`|指定项目扩展其类型时，该字段不会序列化。|  
|`fdSpecialName`|指定该字段是特殊的并且其名称描述如何。|  
|`fdPinvokeImpl`|指定字段实现通过 PInvoke 转发。|  
|`fdReservedMask`|公共语言运行时，保留供内部使用。|  
|`fdRTSpecialName`|指定公共语言运行时元数据内部 Api 应检查该名称的编码。|  
|`fdHasFieldMarshal`|指定该字段包含封送处理信息。|  
|`fdHasDefault`|指定该字段具有默认值。|  
|`fdHasFieldRVA`|指定该字段具有相对虚拟地址。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [Metadata 枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

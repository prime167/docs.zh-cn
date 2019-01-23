---
title: IXCLRDataMethodDefinition::EndEnumInstances 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4a7cd8850778e9bbbc7d8d67f464c7787e40bc13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566084"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="ad1bf-102">IXCLRDataMethodDefinition::EndEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="ad1bf-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="ad1bf-103">释放使用的内部实例枚举过程中使用的迭代器的资源。</span><span class="sxs-lookup"><span data-stu-id="ad1bf-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ad1bf-104">语法</span><span class="sxs-lookup"><span data-stu-id="ad1bf-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="ad1bf-105">参数</span><span class="sxs-lookup"><span data-stu-id="ad1bf-105">Parameters</span></span>

<span data-ttu-id="ad1bf-106">`handle` [out]枚举的实例句柄。</span><span class="sxs-lookup"><span data-stu-id="ad1bf-106">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad1bf-107">备注</span><span class="sxs-lookup"><span data-stu-id="ad1bf-107">Remarks</span></span>

<span data-ttu-id="ad1bf-108">提供的方法属于`IXCLRDataMethodDefinition`接口，并对应于虚拟方法表的第五个槽。</span><span class="sxs-lookup"><span data-stu-id="ad1bf-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ad1bf-109">要求</span><span class="sxs-lookup"><span data-stu-id="ad1bf-109">Requirements</span></span>

<span data-ttu-id="ad1bf-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad1bf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ad1bf-111">**标头：** 无</span><span class="sxs-lookup"><span data-stu-id="ad1bf-111">**Header:** None</span></span>  
<span data-ttu-id="ad1bf-112">**库：** 无</span><span class="sxs-lookup"><span data-stu-id="ad1bf-112">**Library:** None</span></span>  
<span data-ttu-id="ad1bf-113">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ad1bf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ad1bf-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad1bf-114">See also</span></span>

- [<span data-ttu-id="ad1bf-115">调试</span><span class="sxs-lookup"><span data-stu-id="ad1bf-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="ad1bf-116">IXCLRDataMethodDefinition 接口</span><span class="sxs-lookup"><span data-stu-id="ad1bf-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
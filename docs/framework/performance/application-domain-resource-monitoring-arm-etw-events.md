---
title: 应用程序域资源监视 (ARM) ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e4002ae248022a9e4380c79174109494b5e4ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046772"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>应用程序域资源监视 (ARM) ETW 事件
<a name="top"></a> 这些事件提供有关应用程序域的状态的详细诊断信息。 你可以使用这些事件，或使用应用程序域资源监视 (ARM) 功能来获取相同的信息。  
  
 此类别包含以下事件：  
  
- [ThreadCreated 事件](#threadcreated_event)  
  
- [AppDomainMemAllocated 事件](#appdomainmemallocated_event)  
  
- [AppDomainMemSurvived 事件](#appdomainmemsurvived_event)  
  
- [ThreadAppDomainEnter 事件](#threadappdomainenter_event)  
  
- [ThreadTerminated 事件](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>ThreadCreated 事件  
 在断开的提供程序下此事件也会作为 `ThreadDC` 引发（在 `AppDomainResourceManagementRundownKeyword` 关键字下）。 这是此类别的断开提供程序下引发的唯一事件。  
  
 下表显示了关键字和级别。 （有关详细信息，请参阅 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)。）  
  
|引发事件的关键字|Level|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|信息性 (4)|  
|`ThreadingKeyword` (0x10000)|信息性 (4)|  
  
 下表显示了事件信息。  
  
|Event|事件 ID|在发生以下情况时引发|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|已为应用程序域创建了一个线程。|  
  
 下表显示了事件数据。  
  
|字段名|数据类型|描述|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|已创建的线程 ID。|  
|AppDomainID|win:UInt64|正在报告其线程活动的应用程序域的标识符。|  
|标志|win:UInt32|线程创建标志。|  
|ManagedThreadIndex|win:UInt32|已创建线程的托管索引。|  
|OSThreadID|win:UInt32|已创建线程的操作系统 ID。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 的实例的唯一 ID。|  
  
 [返回页首](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>AppDomainMemAllocated 事件  
 下表显示了关键字和级别。  
  
|引发事件的关键字|Level|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|信息性 (4)|  
  
 下表显示了事件信息。  
  
|Event|事件 ID|在发生以下情况时引发|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|应用程序域中分配每 4 MB 的内存（大约）。|  
  
 下表显示了事件数据。  
  
|字段名|数据类型|描述|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|正在报告其资源使用情况的应用程序域的标识符。|  
|已分配|win:UInt64|自应用程序域创建以来在此应用程序域中分配的字节总数（不减去已释放的内存量）。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 的实例的唯一 ID。|  
  
 [返回页首](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>AppDomainMemSurvived 事件  
 下表显示了关键字和级别。  
  
|引发事件的关键字|Level|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|信息性 (4)|  
  
 下表显示了事件信息。  
  
|Event|事件 ID|在发生以下情况时引发|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|每个垃圾回收已结束。|  
  
 下表显示了事件数据。  
  
|字段名|数据类型|描述|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|正在报告其资源使用情况的域的标识符。|  
|已保留|win:UInt64|上次回收后保留下来的、已知由此应用程序域保留的字节数。 此数字在完整回收之后准确且完整，但在暂时的回收之后可能不完整。|  
|ProcessSurvived|win:UInt64|从上一次回收中保留的总字节数。 完整回收之后，该数字表示托管堆中实时保留的字节数。 暂时回收之后，该数字表示暂时生成中实时保留的字节数。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 的实例的唯一 ID。|  
  
 [返回页首](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>ThreadAppDomainEnter 事件  
 下表显示了关键字和级别。  
  
|引发事件的关键字|Level|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|信息性 (4)|  
|`ThreadingKeyword` (0x10000)|信息性 (4)|  
  
 下表显示了事件信息。  
  
|Event|事件 ID|在发生以下情况时引发|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|线程进入应用程序域。|  
  
 下表显示了事件数据。  
  
|字段名|数据类型|描述|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|线程标识符。|  
|AppDomainID|win:UInt64|应用程序域标识符。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 的实例的唯一 ID。|  
  
 [返回页首](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>ThreadTerminated 事件  
 下表显示了关键字和级别。  
  
|引发事件的关键字|Level|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|信息性 (4)|  
|`ThreadingKeyword` (0x10000)|信息性 (4)|  
  
 下表显示了事件信息。  
  
|Event|事件 ID|在发生以下情况时引发|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|线程终止。|  
  
 下表显示了事件数据：  
  
|字段名|数据类型|描述|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|线程标识符。|  
|AppDomainID|win:UInt64|应用程序域标识符。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 的实例的唯一 ID。|  
  
## <a name="see-also"></a>请参阅

- [CLR ETW 事件](clr-etw-events.md)

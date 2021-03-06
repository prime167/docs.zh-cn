---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e56a9ed1d837af27d481282e0e106d537ec41ee3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997745"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
WS-AT 协议服务未能注册某个控制协议的参与者。  
  
## <a name="description"></a>描述  
 跟踪 MSDTC 是否检测到无效的注册请求。 这可能是由于多个完成注册请求和内部错误造成的。  
  
## <a name="troubleshooting"></a>疑难解答  
 不要尝试多次“为完成而注册”。  此外，检查跟踪消息中的状态字符串以确定是否存在任何可操作的项。  
  
## <a name="see-also"></a>请参阅

- [跟踪](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [使用跟踪来排除应用程序故障](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理和诊断](../../../../../docs/framework/wcf/diagnostics/index.md)

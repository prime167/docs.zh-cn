---
title: 如何：创建不含调整规则的时区
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 510112c8b19ec002d1dcf918eb983b55dee68fd0
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106658"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>如何：创建不含调整规则的时区

由于以下几个原因, 应用程序所需的确切时区信息在特定系统上可能不存在:

- 本地系统的注册表中从未定义过该时区。

- 已修改或删除注册表中有关时区的数据。

- 存在时区, 但没有特定历史时间段的准确信息。

在这些情况下, 可以调用<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法来定义应用程序所需的时区。 您可以使用此方法的重载来创建具有或不带调整规则的时区。 如果时区支持夏令时, 则可以用固定或浮动调整规则定义调整。 (有关这些术语的定义, 请参阅时区[概述](../../../docs/standard/datetime/time-zone-overview.md)中的 "时区术语" 部分。)

> [!IMPORTANT]
> 通过调用<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法创建的自定义时区未添加到注册表中。 相反, 只能通过<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法调用返回的对象引用来访问这些对象。

本主题说明如何创建不带调整规则的时区。 若要创建支持夏令时调整规则的时区, 请参阅[如何:创建具有调整规则](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)的时区。

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>创建不含调整规则的时区

1. 定义时区的显示名称。

   显示名称采用相当标准的格式, 在此格式中, 时区与协调世界时 (UTC) 的偏移量括在括号中, 后面跟有标识时区的字符串、时区中的一个或多个城市, 或者一个或多个 cou时区中的 ntries 或区域。

2. 定义时区标准时间的名称。 通常, 此字符串还用作时区的标识符。

3. 如果要使用不同于时区的标准名称的标识符, 请定义时区标识符。

4. 实例化定义时区与 UTC 的偏移量的对象。<xref:System.TimeSpan> 时间时区晚于 UTC 的时区具有正偏移量。 其时间早于 UTC 的时区具有负偏移量。

5. <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>调用方法以实例化新时区。

## <a name="example"></a>示例

下面的示例定义了莫森, 南极洲的自定义时区, 该时区没有调整规则。

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

分配<xref:System.TimeZoneInfo.DisplayName%2A>给属性的字符串遵循标准格式, 其中, 时区与 UTC 的偏移量后跟时区的友好说明。

## <a name="compiling-the-code"></a>编译代码

此示例需要：

- 导入以下命名空间:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>请参阅

- [日期、时间和时区](../../../docs/standard/datetime/index.md)
- [时区概述](../../../docs/standard/datetime/time-zone-overview.md)
- [如何：创建具有调整规则的时区](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)

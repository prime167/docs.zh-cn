---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182101"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>不支持 Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue 兼容性开关

已在 .NET Framework 4.7.2 中引入 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 兼容性开关，但它在 .NET Core 3.0 上的 Windows 窗体中尚不受支持。

#### <a name="change-description"></a>更改描述

自 .NET Framework 4.7.2 起，开发人员可使用 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 兼容性开关选择退出 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 属性的新行为 - 新行为是返回对源控件的引用。 该属性之前的行为是返回 `null`。 有关详细信息，请参阅 [\<AppContextSwitchOverrides> 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

.NET Core 中尚不支持 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 开关。

#### <a name="version-introduced"></a>引入的版本

3.0 预览版 9

#### <a name="recommended-action"></a>建议的操作

删除此开关。 此开关不受支持，且未提供替代功能。

#### <a name="category"></a>类别

Windows 窗体

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->

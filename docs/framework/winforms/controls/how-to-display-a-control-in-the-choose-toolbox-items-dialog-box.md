---
title: 如何：在“选择工具箱项”对话框中显示控件
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86ec8f9ae76f010ebbc3be393d8d257ba5cfc6b6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834614"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>如何：在“选择工具箱项”对话框中显示控件

开发和分发控件时，可能希望这些控件出现在 Visual Studio 的 "**选择工具箱项**" 对话框中，当您右键单击 "**工具箱**" 并选择 "**选择项**" 时，将显示该对话框。 可以通过使用 AssemblyFoldersEx 注册过程，使控件显示在此对话框中。

若要在 "选择工具箱项" 对话框中显示控件：

- 将控件程序集安装到全局程序集缓存中。 有关详细信息，请参阅[如何：将程序集安装到全局程序集缓存](../../app-domains/install-assembly-into-gac.md)。

  -或-

- 使用 AssemblyFoldersEx 注册过程注册控件及其关联的设计时程序集。 AssemblyFoldersEx 是一个注册表位置，其中第三方供应商为其支持的每个框架版本存储路径。 设计时解决方案可以在此注册表位置查找引用程序集。 注册表脚本可以指定想要在 "工具箱" 中显示的控件。

## <a name="see-also"></a>请参阅

- [设计时开发 Windows 窗体控件](developing-windows-forms-controls-at-design-time.md)
- [如何：将程序集安装到全局程序集缓存](../../app-domains/install-assembly-into-gac.md)
- [演练：用自定义组件自动填充工具箱](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)

---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: fbe3634d1fbc03acd56ef7276d65fd54493b9806
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002412"
---
# <a name="-addmodule"></a>-addmodule
使编译器让指定文件中的所有类型信息可供当前正在编译的项目使用。  
  
## <a name="syntax"></a>语法  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>参数  
 `fileList`  
 必需。 包含元数据但不包含程序集清单的文件的逗号分隔列表。 包含空格的文件名应括在引号（""）中。  
  
## <a name="remarks"></a>备注  
 @No__t-0 参数列出的文件必须使用 `-target:module` 选项创建，或与另一个编译器等效于 `-target:module`。  
  
 与 @no__t 一起添加的所有模块在运行时必须位于与输出文件相同的目录中。 也就是说，您可以在编译时在任何目录中指定一个模块，但该模块必须在运行时在应用程序目录中。 如果不是，则会出现 <xref:System.TypeLoadException> 错误。  
  
 如果指定（隐式或显式）除 `-addmodule` @no__t 以外的任何[目标（Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)选项，则传递到 @no__t 的文件将成为项目的程序集的一部分。 需要一个程序集来运行一个输出文件，其中包含一个或多个文件，并 `-addmodule`。  
  
 使用[/reference （Visual Basic）](../../../visual-basic/reference/command-line-compiler/reference.md)从包含程序集的文件导入元数据。  
  
> [!NOTE]
> 在 Visual Studio 开发环境中，不能使用 `-addmodule` 选项;仅当从命令行进行编译时，它才可用。  
  
## <a name="example"></a>示例  
 下面的代码将创建一个模块。  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 下面的代码将导入模块的类型。  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 当你运行 `t1` 时，它将输出 `802`。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)
- [-reference （Visual Basic）](../../../visual-basic/reference/command-line-compiler/reference.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

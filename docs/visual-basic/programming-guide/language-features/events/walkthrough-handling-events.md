---
title: 处理事件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 12267e0a70419298bc581421c4f3a220088d205f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956303"
---
# <a name="walkthrough-handling-events-visual-basic"></a>演练：处理事件 (Visual Basic)
这是演示如何处理事件的两个主题中的第二个。 第一主题[演练:声明和引发事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), 演示如何声明和引发事件。 本部分使用该演练中的窗体和类来演示如何在事件发生时对其进行处理。  
  
 `Widget`类示例使用传统的事件处理语句。 Visual Basic 提供了用于处理事件的其他技术。 作为练习, 您可以修改此示例以使用`AddHandler`和`Handles`语句。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>处理小组件类的 PercentDone 事件  
  
1. 将以下代码放入`Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     关键字指定该变量`mWidget`用于处理对象的事件。 `WithEvents` 通过提供要从中创建对象的类的名称, 指定对象的类型。  
  
     变量`mWidget`在中`Form1`声明, 因为`WithEvents`变量必须是类级别。 无论你将其放入哪类类型, 都是如此。  
  
     变量`mblnCancel` 用于`LongTask`取消方法。  
  
## <a name="writing-code-to-handle-an-event"></a>编写代码来处理事件  
 一旦使用`WithEvents`声明变量, 变量名称就会出现在类的**代码编辑器**的左侧下拉列表中。 选择`mWidget`后`Widget` , 类的事件将出现在右侧下拉列表中。 选择事件会显示相应的事件过程, 其中包含前缀`mWidget`和下划线。 与`WithEvents`变量关联的所有事件过程都被赋予变量名称作为前缀。  
  
#### <a name="to-handle-an-event"></a>处理事件  
  
1. 从`mWidget` **代码编辑器**的左侧下拉列表中选择。  
  
2. 从右侧下拉列表中选择事件。`PercentDone` "**代码编辑器**" 将`mWidget_PercentDone`打开事件过程。  
  
    > [!NOTE]
    > **代码编辑器**对于插入新的事件处理程序非常有用, 但不是必需的。 在本演练中, 只需直接将事件处理程序复制到代码中即可。  
  
3. 将以下代码添加到 `mWidget_PercentDone` 事件处理程序中：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     每当引发`Label`事件时, 事件过程就会在控件中显示完成百分比。 `PercentDone` 方法允许重绘标签, 并为用户提供单击 "取消" 按钮的机会。 `DoEvents`  
  
4. 为`Button2_Click`事件处理程序添加以下代码:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 如果用户在运行时 `LongTask`单击 "取消" 按钮, 则`Button2_Click`只要`DoEvents`语句允许事件处理, 就会立即执行该事件。 类级别`mblnCancel`变量设置为`mWidget_PercentDone` `True`, 然后事件对其进行测试, 并将`ByRef Cancel`参数设置为`True`。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>将 WithEvents 变量连接到对象  
 `Form1`现已设置为处理`Widget`对象的事件。 剩下的就是找到某个`Widget`地方。  
  
 当在设计时声明`WithEvents`变量时, 没有与之关联的对象。 `WithEvents`变量与任何其他对象变量一样。 您必须创建一个对象, 并使用`WithEvents`变量为其分配一个引用。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>创建对象并为其分配引用  
  
1. 从**代码编辑器**的左侧下拉列表中选择 " **(Form1 事件)** "。  
  
2. 从右侧下拉列表中选择事件。`Load` "**代码编辑器**" 将`Form1_Load`打开事件过程。  
  
3. 为`Form1_Load`事件过程添加以下代码以`Widget`创建:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 执行此代码时, Visual Basic 将创建`Widget`一个对象, 并将其事件连接到与`mWidget`关联的事件过程。 从该点开始, 无论何时`Widget` `PercentDone`引发事件, `mWidget_PercentDone`都将执行事件过程。  
  
#### <a name="to-call-the-longtask-method"></a>调用 LongTask 方法  
  
- 将以下代码添加到 `Button1_Click` 事件处理程序中：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 在调用`Boolean` `False`方法之前, 必须初始化显示完成百分比的标签, 并且用于取消方法的类级别标志必须设置为。 `LongTask`  
  
 `LongTask`调用时, 任务持续时间为12.2 秒。 每隔一秒引发一次事件。`PercentDone` 每次引发事件时, `mWidget_PercentDone`都会执行事件过程。  
  
 `mblnCancel` `LongTask` `mblnCancel`完成后, 将测试, 以查看是否正常结束, 或是否由于设置为`True`而停止。 `LongTask` 只有在前一种情况下才会更新完成百分比。  
  
#### <a name="to-run-the-program"></a>运行程序  
  
1. 按 F5 将项目置于运行模式。  
  
2. 单击 "**启动任务**" 按钮。 每次`PercentDone`引发事件时, 都会将标签更新为已完成的任务的百分比。  
  
3. 单击 "**取消**" 按钮停止任务。 请注意, 当你单击 "**取消**" 按钮时, 该按钮的外观不会立即更改。 只有语句允许事件处理后, 才能发生事件。`Click` `My.Application.DoEvents`  
  
    > [!NOTE]
    > `My.Application.DoEvents`方法不以与窗体相同的方式处理事件。 例如, 在本演练中, 必须单击 "**取消**" 按钮两次。 若要允许窗体直接处理事件, 可以使用多线程处理。 有关详细信息, 请参阅[托管线程处理](../../../../standard/threading/index.md)。
  
 你可能会发现, 通过 F11 运行程序并单步执行代码行来单步执行代码是有益的。 您可以清楚地了解执行的`LongTask` `PercentDone`输入方式, 然后在每次`Form1`引发事件时短暂重新进入。  
  
 如果在的代码`Form1`中返回执行时, 会发生什么情况, 再次调用该`LongTask`方法呢？ 在最糟糕的情况下, 如果`LongTask`每次引发事件时调用, 则可能会发生堆栈溢出。  
  
 您可以通过将对`mWidget`新`Widget`的`mWidget`引用分配给, `Widget`使变量处理不同对象的事件。 事实上, 每次单击按钮时, 都`Button1_Click`可以使代码执行此操作。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>处理不同小组件的事件  
  
- 将以下代码行添加到`Button1_Click`过程中, 紧靠在读取`mWidget.LongTask(12.2, 0.33)`的行之前:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 每次单击按钮时, `Widget`上面的代码都会创建一个新的。 `LongTask`方法完成后, 将立即释放对的`Widget`引用并`Widget`销毁。  
  
 一个变量一次只能包含一个对象引用, 因此, 如果您`mWidget`向分配不同`Widget`的对象, 则不会`Widget`再处理上一个对象的事件。 `WithEvents` 如果`mWidget`是唯一包含对旧`Widget`对象的引用的对象变量, 则销毁该对象。 如果要处理来自多个`Widget`对象的事件, 请`AddHandler`使用语句分别处理每个对象中的事件。  
  
> [!NOTE]
> 您可以根据需要声明`WithEvents`多个变量, 但不支持变量`WithEvents`的数组。  
  
## <a name="see-also"></a>请参阅

- [演练：声明和引发事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)

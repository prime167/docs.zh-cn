---
title: 终结器 - C# 编程指南
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 9936d56582afd160bf3464d18efd3acf47c7af60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924501"
---
# <a name="finalizers-c-programming-guide"></a>终结器（C# 编程指南）
终结器（也称为  析构函数）用于在垃圾回收器收集类实例时执行任何必要的最终清理操作。  
  
## <a name="remarks"></a>备注  
  
- 无法在结构中定义终结器。 它们仅用于类。  
  
- 一个类只能有一个终结器。  
  
- 不能继承或重载终结器。  
  
- 不能手动调用终结器。 可以自动调用它们。  
  
- 终结器不使用修饰符或参数。  
  
 例如，以下是类 `Car` 的终结器声明。
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

终结器也可以作为表达式主体定义实现，如下面的示例所示。

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 终结器隐式调用对象基类上的 <xref:System.Object.Finalize%2A>。 因此，对终结器的调用会隐式转换为以下代码：  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 这意味着，对继承链（从派生程度最高到派生程度最低）中的所有实例以递归方式调用 `Finalize` 方法。  
  
> [!NOTE]
> 不应使用空终结器。 如果类包含终结器，会在 `Finalize` 队列中创建一个条目。 调用终结器时，会调用垃圾回收器来处理该队列。 空终结器只会导致不必要的性能损失。  
  
 程序员无法控制何时调用终结器，因为这由垃圾回收器决定。 垃圾回收器检查应用程序不再使用的对象。 如果它认为某个对象符合终止条件，则调用终结器（如果有），并回收用来存储此对象的内存。 
 
 在 .NET Framework 应用程序中（但不在 .NET Core 应用程序中），程序退出时也会调用终结器。 
  
 可以通过调用 <xref:System.GC.Collect%2A> 强制进行垃圾回收，但多数情况下应避免此操作，因为它可能会造成性能问题。  
  
## <a name="using-finalizers-to-release-resources"></a>使用终结器释放资源  
 一般来说，C# 所占用的内存管理空间比使用不面向带有垃圾回收机制的运行时的语言进行开发时所使用的内存管理空间要少。 这是因为 .NET Framework 垃圾回收器会隐式管理对象的内存分配和释放。 但是，如果应用程序封装非托管的资源，例如窗口、文件和网络连接，则应使用终结器释放这些资源。 当对象符合终止条件时，垃圾回收器会运行对象的 `Finalize` 方法。  
  
## <a name="explicit-release-of-resources"></a>显式释放资源  
 如果应用程序正在使用昂贵的外部资源，我们还建议在垃圾回收器释放对象前显式释放资源。 若要实现此操作，可从执行必要的对象清除的 <xref:System.IDisposable> 接口实现 `Dispose` 方法。 这样可大大提高应用程序的性能。 如果调用 `Dispose` 方法失败，那么即使拥有对资源的显式控制，终结器也会成为清除资源的一个保障。  
  
 有关清除资源的详细信息，请参阅下列主题：  
  
- [清理未托管资源](../../../standard/garbage-collection/unmanaged.md)（清理未托管资源）  
  
- [实现 Dispose 方法](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [using 语句](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>示例  
 以下示例创建了三个类，并且这三个类构成了一个继承链。 类 `First` 是基类，`Second` 派生自 `First`，`Third` 派生自 `Second`。 这三个类都具有终结器。 在 `Main` 中，已创建派生程度最高的类的一个实例。 程序运行时，请注意，将按顺序（从派生程度最高到派生程度最低）自动调用这三个类的终结器。  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>C# 语言规范  

有关详细信息，请参阅 [C# 语言规范](../../language-reference/language-specification/index.md)中的[析构函数](~/_csharplang/spec/classes.md#destructors)部分。
  
## <a name="see-also"></a>请参阅

- <xref:System.IDisposable>
- [C# 编程指南](../index.md)
- [构造函数](./constructors.md)
- [垃圾回收](../../../standard/garbage-collection/index.md)

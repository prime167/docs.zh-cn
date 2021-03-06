---
title: 数据类型摘要 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Boolean data type [Visual Basic], supported types in Visual Basic
- storage [Visual Basic], order of storage
- data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], supported types in Visual Basic
- notation [Visual Basic], scientific
- memory requirements, data types
- user-defined data types [Visual Basic], Visual Basic
- Date data type [Visual Basic], Visual Basic
- Visual Basic, data types
- storage [Visual Basic], allocation
- Integer data type [Visual Basic], Visual Basic data types
- storage [Visual Basic], space
- Variant data types [Visual Basic], supported types in Visual Basic
- Char data type [Visual Basic], Visual Basic data types
- intrinsic data types [Visual Basic]
- memory consumption [Visual Basic], data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type [Visual Basic], supported types in Visual Basic
- String data type [Visual Basic], Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type [Visual Basic], Visual Basic data types
- Byte data type [Visual Basic], Visual Basic data types
- Object data type [Visual Basic], supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
ms.openlocfilehash: 57f6caa00806f4874cb8070805e8b6784ec82e40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956807"
---
# <a name="data-type-summary-visual-basic"></a>数据类型摘要 (Visual Basic)
下表显示了 Visual Basic 的数据类型、其支持的公共语言运行时类型、其名义存储分配及其值范围。  
  
|Visual Basic 类型|公共语言运行时类型结构|标称存储分配|取值范围|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[布尔值](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|依赖于实现平台|`True` 或 `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 个字节|0到 255 (无符号)|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md)(单个字符)|<xref:System.Char>|2 个字节|0到 65535 (无符号)|  
|[Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 个字节|0:00:00 年1月1日至12月31日下午 11:59:59, (午夜) 9999|  
|[小数](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 个字节|0到 +/-79228162514264337593543950335 (+/-7.9...E + 28) <sup>†</sup> , 无小数点;0到 +/-7.9228162514264337593543950335, 小数点右侧有28个位置;<br /><br /> 最小非零数字为 +/-0.0000000000000000000000000001 (+/-1E-28) <sup>†</sup>|  
|[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)(双精度浮点)|<xref:System.Double>|8 个字节|-1.79769313486231570 e + 308 到-4.94065645841246544 E-324 <sup>†</sup>表示负值;<br /><br /> 4.94065645841246544 e-324 到 1.79769313486231570 E + 308 <sup>†</sup>用于正值|  
|[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 个字节|-2147483648 到 2147483647 (有符号)|  
|[Long](../../../visual-basic/language-reference/data-types/long-data-type.md)(长整型)|<xref:System.Int64>|8 个字节|-9223372036854775808 到 9223372036854775807 (9.2. E + 18 <sup>†</sup>) (有符号)|  
|[对象](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object>班级|32位平台上的4个字节<br /><br /> 64位平台上的8个字节|任何类型都可以存储在类型的变量中`Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 个字节|-128 到 127 (有符号)|  
|[Short](../../../visual-basic/language-reference/data-types/short-data-type.md)(短整型)|<xref:System.Int16>|2 个字节|-32768 到 32767 (有符号)|  
|[单个](../../../visual-basic/language-reference/data-types/single-data-type.md)(单精度浮点)|<xref:System.Single>|4 个字节|-3.4028235 e + 38 到-1.401298 E-45 <sup>†</sup>表示负值;<br /><br /> 1.401298 e-45 到 3.4028235 E + 38 <sup>†</sup>用于正值|  
|[字符串](../../../visual-basic/language-reference/data-types/string-data-type.md)(可变长度)|<xref:System.String>班级|依赖于实现平台|0到约 2000000000 Unicode 字符|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 个字节|0到 4294967295 (无符号)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 个字节|0到 18446744073709551615 (1.8 ... E + 19 <sup>†</sup>) (无符号)|  
|[用户定义](../../../visual-basic/language-reference/data-types/user-defined-data-type.md)构造|(继承自<xref:System.ValueType>)|依赖于实现平台|结构的每个成员都有一个由其数据类型确定的范围, 并与其他成员的范围无关|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 个字节|0到 65535 (无符号)|  
  
 <sup>†</sup>使用*科学记数法*时, "E" 指的是10的幂。 因此, 3.56 E + 2 表示 3.56 x 10<sup>2</sup>或 356, 3.56 e-2 表示 3.56/10<sup>2</sup>或0.0356。  
  
> [!NOTE]
> 对于包含文本的字符串, 请<xref:Microsoft.VisualBasic.Strings.StrConv%2A>使用函数从一种文本格式转换为另一种文本格式。  
  
 除了在声明语句中指定数据类型之外, 还可以使用类型字符强制某些编程元素的数据类型。 请参阅[类型字符](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。  
  
## <a name="memory-consumption"></a>内存消耗  
 在声明基本数据类型时, 不安全地假定其内存消耗与其名义存储分配相同。 这是由于下列注意事项:  
  
- **存储分配。** 公共语言运行时可以基于执行应用程序的平台的当前特性来分配存储空间。 如果内存几乎已满, 则可能会将声明的元素尽可能紧密地打包在一起。 在其他情况下, 它可能会将内存地址与自然硬件边界对齐, 以优化性能。  
  
- **平台宽度。** 64位平台上的存储分配不同于32位平台上的分配。  
  
### <a name="composite-data-types"></a>复合数据类型  
 相同的注意事项也适用于复合数据类型的每个成员, 如结构或数组。 你不能只是将类型成员的标称存储分配组合在一起。 此外, 还有其他注意事项, 如以下内容:  
  
- **费用.** 某些复合类型具有额外的内存需求。 例如, 数组对数组本身和每个维度使用额外的内存。 在32位平台上, 此开销目前为每个维度12个字节加上8个字节。 在64位平台上, 此要求翻倍。  
  
- **存储布局。** 不能安全地假设内存中存储的顺序与声明顺序相同。 甚至不能对字节对齐进行假设, 如2字节或4字节边界。 如果要定义类或结构, 并且需要控制其成员的存储布局, 则可以将<xref:System.Runtime.InteropServices.StructLayoutAttribute>属性应用于类或结构。  
  
### <a name="object-overhead"></a>对象开销  
 除数据类型中包含的数据外,引用任何基本数据类型或复合数据类型的也使用4个字节。`Object`  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [类型字符](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

---
title: <httpWebRequest> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: fa00aed2cd1e96ec788d4bc9c1c63f20561d8d1c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698175"
---
# <a name="httpwebrequest-element-network-settings"></a>\<httpWebRequest > 元素（网络设置）
自定义 Web 请求参数。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t[ **\<system >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<httpWebRequest >**  
  
## <a name="syntax"></a>语法  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|**特性**|**说明**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|指定响应标头的最大长度（以 kb 为单位）。 默认值为 64。 如果值为-1，则指示不会对响应标头施加大小限制。|  
|`maximumErrorResponseLength`|指定错误响应的最大长度（以 kb 为单位）。 默认值为 64。 如果值为-1，则表示不对错误响应施加大小限制。|  
|`maximumUnauthorizedUploadLength`|指定用于响应未经授权的错误代码的上载的最大长度（以字节为单位）。 默认值为 -1。 如果值为-1，则表示上传不会施加大小限制。|  
|`useUnsafeHeaderParsing`|指定是否启用安全标头分析。 默认值为 `false`。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**说明**|  
|-----------------|---------------------|  
|[设置](settings-element-network-settings.md)|配置 <xref:System.Net> 命名空间的基本网络选项。|  
  
## <a name="remarks"></a>备注  
 默认情况下，.NET Framework 严格地强制执行 RFC 2616，以便进行 URI 分析。 某些服务器响应可能在禁止字段中包含控制字符，这将导致 @no__t 0 方法引发 @no__t。 如果**useUnsafeHeaderParsing**设置为**true**，则在这种情况下不会引发 <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>;但是，您的应用程序容易受到多种形式的 URI 分析攻击。 最佳解决方案是更改服务器，使响应不包含控制字符。  
  
## <a name="configuration-files"></a>配置文件  
 此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。  
  
## <a name="example"></a>示例  
 下面的示例演示如何指定大于标准最大标头长度。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [网络设置架构](index.md)

---
description: '詳細情報: <sslStreamSecurity>'
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 77e08deb5263e330ead5df21ed1ef2dddbba28ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682697"
---
# \<sslStreamSecurity>

<span data-ttu-id="cc7c9-102">SSL ストリームを使用するチャネル セキュリティをサポートするカスタム バインディング要素を表します。</span><span class="sxs-lookup"><span data-stu-id="cc7c9-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="cc7c9-103">構文</span><span class="sxs-lookup"><span data-stu-id="cc7c9-103">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc7c9-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cc7c9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="cc7c9-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc7c9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc7c9-106">属性</span><span class="sxs-lookup"><span data-stu-id="cc7c9-106">Attributes</span></span>  
  
|<span data-ttu-id="cc7c9-107">属性</span><span class="sxs-lookup"><span data-stu-id="cc7c9-107">Attribute</span></span>|<span data-ttu-id="cc7c9-108">説明</span><span class="sxs-lookup"><span data-stu-id="cc7c9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc7c9-109">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="cc7c9-109">requireClientCertificate</span></span>|<span data-ttu-id="cc7c9-110">クライアント証明書がこのバインディングに必要かどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="cc7c9-110">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="cc7c9-111">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="cc7c9-111">The default is `false`.</span></span>|  
|<span data-ttu-id="cc7c9-112">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="cc7c9-112">sslProtocols</span></span>|<span data-ttu-id="cc7c9-113">どの SslProtocols がサポートされているのかを指定する SslProtocols 列挙型フラグの値。</span><span class="sxs-lookup"><span data-stu-id="cc7c9-113">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="cc7c9-114">既定値は、Ssl3&#124;Tls&#124;Tls11&#124;Tls12 です。</span><span class="sxs-lookup"><span data-stu-id="cc7c9-114">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc7c9-115">子要素</span><span class="sxs-lookup"><span data-stu-id="cc7c9-115">Child Elements</span></span>  

 <span data-ttu-id="cc7c9-116">なし。</span><span class="sxs-lookup"><span data-stu-id="cc7c9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc7c9-117">親要素</span><span class="sxs-lookup"><span data-stu-id="cc7c9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cc7c9-118">要素</span><span class="sxs-lookup"><span data-stu-id="cc7c9-118">Element</span></span>|<span data-ttu-id="cc7c9-119">説明</span><span class="sxs-lookup"><span data-stu-id="cc7c9-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="cc7c9-120">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="cc7c9-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc7c9-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc7c9-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="cc7c9-122">バインド</span><span class="sxs-lookup"><span data-stu-id="cc7c9-122">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cc7c9-123">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="cc7c9-123">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cc7c9-124">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="cc7c9-124">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

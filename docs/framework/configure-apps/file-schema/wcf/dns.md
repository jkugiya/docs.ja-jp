---
description: '詳細情報: <dns>'
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: a5c0601a027c72b4d6307261793bd5725979db92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803894"
---
# \<dns>

<span data-ttu-id="0c743-102">予想されるサーバーの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c743-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="0c743-103">この ID は、同じ値を持つ DNS がサーバーの証明書に含まれていれば、X509 証明書の認証モードで有効です。</span><span class="sxs-lookup"><span data-stu-id="0c743-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="0c743-104">さらに、SPN に同じ値があれば、Windows 認証モードでも有効です。</span><span class="sxs-lookup"><span data-stu-id="0c743-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="0c743-105">要素の値の設定の詳細については、「 [サービス id と認証](../../../wcf/feature-details/service-identity-and-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c743-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="0c743-106">構文</span><span class="sxs-lookup"><span data-stu-id="0c743-106">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c743-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0c743-107">Attributes and Elements</span></span>  

 <span data-ttu-id="0c743-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0c743-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c743-109">属性</span><span class="sxs-lookup"><span data-stu-id="0c743-109">Attributes</span></span>  
  
|<span data-ttu-id="0c743-110">属性</span><span class="sxs-lookup"><span data-stu-id="0c743-110">Attribute</span></span>|<span data-ttu-id="0c743-111">説明</span><span class="sxs-lookup"><span data-stu-id="0c743-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c743-112">value</span><span class="sxs-lookup"><span data-stu-id="0c743-112">value</span></span>|<span data-ttu-id="0c743-113">証明書の DNS です。</span><span class="sxs-lookup"><span data-stu-id="0c743-113">The DNS of the certificate.</span></span> <span data-ttu-id="0c743-114">DNS は、IP ベースのネットワーク上でコンピューターを特定するために使用される業界標準のプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="0c743-114">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="0c743-115">ユーザーは、やなどの表示名を覚えておくことができます。たとえば、207.46.131.137 のように、 `https://go.microsoft.com/fwlink/?prd=10929` `https://go.microsoft.com/fwlink/?LinkID=96165` 数字ベースのアドレスよりも簡単です。</span><span class="sxs-lookup"><span data-stu-id="0c743-115">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c743-116">子要素</span><span class="sxs-lookup"><span data-stu-id="0c743-116">Child Elements</span></span>  

 <span data-ttu-id="0c743-117">なし。</span><span class="sxs-lookup"><span data-stu-id="0c743-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c743-118">親要素</span><span class="sxs-lookup"><span data-stu-id="0c743-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0c743-119">要素</span><span class="sxs-lookup"><span data-stu-id="0c743-119">Element</span></span>|<span data-ttu-id="0c743-120">説明</span><span class="sxs-lookup"><span data-stu-id="0c743-120">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="0c743-121">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c743-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0c743-122">例</span><span class="sxs-lookup"><span data-stu-id="0c743-122">Example</span></span>  

 <span data-ttu-id="0c743-123">次の構成コードは、サーバーの認証に使用される X.509 証明書の DNS を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c743-123">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="0c743-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c743-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="0c743-125">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="0c743-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)

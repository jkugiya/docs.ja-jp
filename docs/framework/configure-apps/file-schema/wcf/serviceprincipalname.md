---
description: '詳細情報: <servicePrincipalName>'
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 494368f1f47f10aac8009e47a9219966c87e5eda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786695"
---
# \<servicePrincipalName>

<span data-ttu-id="df49a-102">サービスの ID をサービス プリンシパル名 (SPN) により指定します。</span><span class="sxs-lookup"><span data-stu-id="df49a-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="df49a-103">SPN の設定の詳細については、「 [サービス id と認証](../../../wcf/feature-details/service-identity-and-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df49a-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="df49a-104">構文</span><span class="sxs-lookup"><span data-stu-id="df49a-104">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df49a-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="df49a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="df49a-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="df49a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df49a-107">属性</span><span class="sxs-lookup"><span data-stu-id="df49a-107">Attributes</span></span>  
  
|<span data-ttu-id="df49a-108">属性</span><span class="sxs-lookup"><span data-stu-id="df49a-108">Attribute</span></span>|<span data-ttu-id="df49a-109">説明</span><span class="sxs-lookup"><span data-stu-id="df49a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df49a-110">value</span><span class="sxs-lookup"><span data-stu-id="df49a-110">value</span></span>|<span data-ttu-id="df49a-111">クライアントがサービスのインスタンスを一意に識別するための名前。</span><span class="sxs-lookup"><span data-stu-id="df49a-111">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="df49a-112">フォレストの複数のコンピューターに 1 つのサービスの複数のインスタンスをインストールする場合、各インスタンスには独自の SPN が必要です。</span><span class="sxs-lookup"><span data-stu-id="df49a-112">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="df49a-113">クライアントが認証に使用できる複数の名前がある場合は、指定したサービス インスタンスに複数の SPN を設定できます。</span><span class="sxs-lookup"><span data-stu-id="df49a-113">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df49a-114">子要素</span><span class="sxs-lookup"><span data-stu-id="df49a-114">Child Elements</span></span>  

 <span data-ttu-id="df49a-115">なし。</span><span class="sxs-lookup"><span data-stu-id="df49a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df49a-116">親要素</span><span class="sxs-lookup"><span data-stu-id="df49a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="df49a-117">要素</span><span class="sxs-lookup"><span data-stu-id="df49a-117">Element</span></span>|<span data-ttu-id="df49a-118">説明</span><span class="sxs-lookup"><span data-stu-id="df49a-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="df49a-119">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="df49a-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df49a-120">解説</span><span class="sxs-lookup"><span data-stu-id="df49a-120">Remarks</span></span>  

 <span data-ttu-id="df49a-121">この id を持つエンドポイントに接続するセキュリティで保護された Windows Communication Foundation (WCF) クライアントは、エンドポイントで SSPI 認証を実行するときに SPN を使用します。</span><span class="sxs-lookup"><span data-stu-id="df49a-121">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df49a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="df49a-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="df49a-123">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="df49a-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)

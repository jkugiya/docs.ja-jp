---
description: '詳細情報: <identity> の <certificate>'
title: <identity> の <certificate>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: b1ccda7e8e84825cc0b2b2be123fe30be449189a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639108"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="ad29e-103">\<identity> の \<certificate></span><span class="sxs-lookup"><span data-stu-id="ad29e-103">\<certificate> for \<identity></span></span>

<span data-ttu-id="ad29e-104">クライアントに対するサービスの検証に使用される X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad29e-104">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="ad29e-105">要素の値の設定について詳しくは、「[サービス ID と認証](../../../wcf/feature-details/service-identity-and-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad29e-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="ad29e-106">構文</span><span class="sxs-lookup"><span data-stu-id="ad29e-106">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad29e-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ad29e-107">Attributes and Elements</span></span>  

 <span data-ttu-id="ad29e-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad29e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad29e-109">属性</span><span class="sxs-lookup"><span data-stu-id="ad29e-109">Attributes</span></span>  
  
|<span data-ttu-id="ad29e-110">属性</span><span class="sxs-lookup"><span data-stu-id="ad29e-110">Attribute</span></span>|<span data-ttu-id="ad29e-111">説明</span><span class="sxs-lookup"><span data-stu-id="ad29e-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad29e-112">encodedValue</span><span class="sxs-lookup"><span data-stu-id="ad29e-112">encodedValue</span></span>|<span data-ttu-id="ad29e-113">証明書の Base64 エンコーディングです。</span><span class="sxs-lookup"><span data-stu-id="ad29e-113">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad29e-114">子要素</span><span class="sxs-lookup"><span data-stu-id="ad29e-114">Child Elements</span></span>  

 <span data-ttu-id="ad29e-115">なし。</span><span class="sxs-lookup"><span data-stu-id="ad29e-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad29e-116">親要素</span><span class="sxs-lookup"><span data-stu-id="ad29e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ad29e-117">要素</span><span class="sxs-lookup"><span data-stu-id="ad29e-117">Element</span></span>|<span data-ttu-id="ad29e-118">説明</span><span class="sxs-lookup"><span data-stu-id="ad29e-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="ad29e-119">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad29e-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ad29e-120">例</span><span class="sxs-lookup"><span data-stu-id="ad29e-120">Example</span></span>  

 <span data-ttu-id="ad29e-121">次のコードは、クライアントに対するサーバーの検証に使用される証明書のエンコードされた表現を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad29e-121">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="ad29e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad29e-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="ad29e-123">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="ad29e-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)

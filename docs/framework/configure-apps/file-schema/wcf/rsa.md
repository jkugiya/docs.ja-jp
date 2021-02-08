---
description: '詳細情報: <rsa>'
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 5e558e608ec1196081166d01415e12fb2c3083b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786877"
---
# \<rsa>

<span data-ttu-id="657d7-102">この ID のエンドポイントに接続するセキュリティで保護された WCF クライアントは、サーバーから提示されたクレームに、この ID を構築するために使用された RSA 公開キーを含むクレームが含まれていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="657d7-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="657d7-103">構文</span><span class="sxs-lookup"><span data-stu-id="657d7-103">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="657d7-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="657d7-104">Attributes and Elements</span></span>  

 <span data-ttu-id="657d7-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="657d7-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="657d7-106">属性</span><span class="sxs-lookup"><span data-stu-id="657d7-106">Attributes</span></span>  
  
|<span data-ttu-id="657d7-107">属性</span><span class="sxs-lookup"><span data-stu-id="657d7-107">Attribute</span></span>|<span data-ttu-id="657d7-108">説明</span><span class="sxs-lookup"><span data-stu-id="657d7-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="657d7-109">value</span><span class="sxs-lookup"><span data-stu-id="657d7-109">value</span></span>|<span data-ttu-id="657d7-110">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="657d7-110">Optional String.</span></span> <span data-ttu-id="657d7-111">クライアントで比較される RSA 公開キー値。</span><span class="sxs-lookup"><span data-stu-id="657d7-111">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="657d7-112">子要素</span><span class="sxs-lookup"><span data-stu-id="657d7-112">Child Elements</span></span>  

 <span data-ttu-id="657d7-113">なし</span><span class="sxs-lookup"><span data-stu-id="657d7-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="657d7-114">親要素</span><span class="sxs-lookup"><span data-stu-id="657d7-114">Parent Elements</span></span>  
  
|<span data-ttu-id="657d7-115">要素</span><span class="sxs-lookup"><span data-stu-id="657d7-115">Element</span></span>|<span data-ttu-id="657d7-116">説明</span><span class="sxs-lookup"><span data-stu-id="657d7-116">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="657d7-117">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="657d7-117">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="657d7-118">解説</span><span class="sxs-lookup"><span data-stu-id="657d7-118">Remarks</span></span>  

 <span data-ttu-id="657d7-119">RSA チェックを行うと、その RSA キーまたは生成された独自の RSA キー値に基づいて、単一の証明書の認証を明確に制限できます。</span><span class="sxs-lookup"><span data-stu-id="657d7-119">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="657d7-120">これにより、RSA キーが変更された場合に既存のクライアントで使用できなくなるサービスを犠牲にして、特定の RSA キーをより厳しく認証できます。</span><span class="sxs-lookup"><span data-stu-id="657d7-120">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="657d7-121">Id を使用してクライアントに対するサービスを検証する方法の詳細については、「 [サービス id と認証](../../../wcf/feature-details/service-identity-and-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="657d7-121">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="657d7-122">例</span><span class="sxs-lookup"><span data-stu-id="657d7-122">Example</span></span>  

 <span data-ttu-id="657d7-123">次の構成コードは、サーバーの認証に使用される X.509 証明書の公開キー値を指定します。</span><span class="sxs-lookup"><span data-stu-id="657d7-123">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="657d7-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="657d7-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="657d7-125">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="657d7-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)

---
description: '詳細情報: <userPrincipalName>'
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 73ace3d6f3d5cb88f2630a4a2ae319decf420021
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664419"
---
# \<userPrincipalName>

<span data-ttu-id="8051f-102">クライアントで認証するサービスのユーザー プリンシパル名 (UPN) を指定します。</span><span class="sxs-lookup"><span data-stu-id="8051f-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="8051f-103">UPN の設定の詳細については、「 [サービス id と認証](../../../wcf/feature-details/service-identity-and-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8051f-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="8051f-104">構文</span><span class="sxs-lookup"><span data-stu-id="8051f-104">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8051f-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8051f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8051f-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8051f-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8051f-107">属性</span><span class="sxs-lookup"><span data-stu-id="8051f-107">Attributes</span></span>  
  
|<span data-ttu-id="8051f-108">属性</span><span class="sxs-lookup"><span data-stu-id="8051f-108">Attribute</span></span>|<span data-ttu-id="8051f-109">説明</span><span class="sxs-lookup"><span data-stu-id="8051f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8051f-110">value</span><span class="sxs-lookup"><span data-stu-id="8051f-110">value</span></span>|<span data-ttu-id="8051f-111">ユーザー アカウント名 (ユーザー ログイン名と呼ばれることもある) と、ユーザー アカウントの検索範囲のドメインを識別するドメイン名です。</span><span class="sxs-lookup"><span data-stu-id="8051f-111">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="8051f-112">これは、Windows ドメインにログオンするための標準的使用方法です。</span><span class="sxs-lookup"><span data-stu-id="8051f-112">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="8051f-113">形式は、 someone@example.com (電子メールアドレスの場合) です。</span><span class="sxs-lookup"><span data-stu-id="8051f-113">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8051f-114">子要素</span><span class="sxs-lookup"><span data-stu-id="8051f-114">Child Elements</span></span>  

 <span data-ttu-id="8051f-115">なし。</span><span class="sxs-lookup"><span data-stu-id="8051f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8051f-116">親要素</span><span class="sxs-lookup"><span data-stu-id="8051f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8051f-117">要素</span><span class="sxs-lookup"><span data-stu-id="8051f-117">Element</span></span>|<span data-ttu-id="8051f-118">説明</span><span class="sxs-lookup"><span data-stu-id="8051f-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="8051f-119">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="8051f-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8051f-120">解説</span><span class="sxs-lookup"><span data-stu-id="8051f-120">Remarks</span></span>  

 <span data-ttu-id="8051f-121">この id を持つエンドポイントに接続するセキュリティで保護された Windows Communication Foundation (WCF) クライアントは、エンドポイントで SSPI 認証を実行するときに UPN を使用します。</span><span class="sxs-lookup"><span data-stu-id="8051f-121">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8051f-122">例</span><span class="sxs-lookup"><span data-stu-id="8051f-122">Example</span></span>  

 <span data-ttu-id="8051f-123">次の構成コードは、クライアントで認証するサービスの UPN を指定します。</span><span class="sxs-lookup"><span data-stu-id="8051f-123">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="8051f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="8051f-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="8051f-125">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="8051f-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)

---
description: '詳細については、次を参照してください: <serviceCertificate> of <clientCredentials> 要素'
title: <serviceCertificate><clientCredentials>要素の
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 5503c1a60b2d37f4f9359a2f49c019c37df71619
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682905"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="a554d-103">\<serviceCertificate>\<clientCredentials>要素の</span><span class="sxs-lookup"><span data-stu-id="a554d-103">\<serviceCertificate> of \<clientCredentials> Element</span></span>

<span data-ttu-id="a554d-104">クライアントに対してサービスを認証する際に使用される証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="a554d-104">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="a554d-105">構文</span><span class="sxs-lookup"><span data-stu-id="a554d-105">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a554d-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a554d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a554d-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a554d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a554d-108">属性</span><span class="sxs-lookup"><span data-stu-id="a554d-108">Attributes</span></span>  

 <span data-ttu-id="a554d-109">なし。</span><span class="sxs-lookup"><span data-stu-id="a554d-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a554d-110">子要素</span><span class="sxs-lookup"><span data-stu-id="a554d-110">Child Elements</span></span>  
  
|<span data-ttu-id="a554d-111">要素</span><span class="sxs-lookup"><span data-stu-id="a554d-111">Element</span></span>|<span data-ttu-id="a554d-112">説明</span><span class="sxs-lookup"><span data-stu-id="a554d-112">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|<span data-ttu-id="a554d-113">ネゴシエーション プロトコル経由でサービスまたは STS が証明書を提供しないときに使用される X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="a554d-113">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="a554d-114">認証用の (範囲指定された) 特定のサービスにより提供される X.509 証明書のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="a554d-114">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="a554d-115">このコレクションは一般に、フェデレーション シナリオでセキュリティ トークン サービスのサービス証明書を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a554d-115">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="a554d-116">クライアントで使用されるサービス証明書の認証動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="a554d-116">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a554d-117">親要素</span><span class="sxs-lookup"><span data-stu-id="a554d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a554d-118">要素</span><span class="sxs-lookup"><span data-stu-id="a554d-118">Element</span></span>|<span data-ttu-id="a554d-119">説明</span><span class="sxs-lookup"><span data-stu-id="a554d-119">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="a554d-120">サービスに対するクライアント自身の認証のためにクライアントによって使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="a554d-120">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a554d-121">解説</span><span class="sxs-lookup"><span data-stu-id="a554d-121">Remarks</span></span>  

 <span data-ttu-id="a554d-122">この構成要素は、SSL 認証を使用してサービスから提示された証明書を検証するためにクライアントが使用する設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="a554d-122">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="a554d-123">また、このクラスには、メッセージ セキュリティを使用してサービスへのメッセージを暗号化するためにクライアントで明示的に構成される、サービスの証明書も含まれます。</span><span class="sxs-lookup"><span data-stu-id="a554d-123">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="a554d-124">要素の属性 `serviceCertificate` は、の属性と同じです [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="a554d-124">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a554d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a554d-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="a554d-126">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="a554d-126">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a554d-127">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="a554d-127">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a554d-128">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="a554d-128">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a554d-129">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="a554d-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)

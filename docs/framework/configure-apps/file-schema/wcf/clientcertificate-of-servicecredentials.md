---
description: '詳細情報: <serviceCredentials> の <clientCertificate>'
title: <clientCertificate> の <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: c3e6378f9646ec30188e2de3d1c832f363904ad0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638822"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="a0af1-103">\<clientCertificate> の \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a0af1-103">\<clientCertificate> of \<serviceCredentials></span></span>

<span data-ttu-id="a0af1-104">双方向通信パターンでサービスからクライアントへのメッセージの署名および暗号化に使用される X.509 証明書を定義します。</span><span class="sxs-lookup"><span data-stu-id="a0af1-104">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="a0af1-105">構文</span><span class="sxs-lookup"><span data-stu-id="a0af1-105">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0af1-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a0af1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a0af1-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0af1-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0af1-108">属性</span><span class="sxs-lookup"><span data-stu-id="a0af1-108">Attributes</span></span>  

 <span data-ttu-id="a0af1-109">なし。</span><span class="sxs-lookup"><span data-stu-id="a0af1-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0af1-110">子要素</span><span class="sxs-lookup"><span data-stu-id="a0af1-110">Child Elements</span></span>  
  
|<span data-ttu-id="a0af1-111">要素</span><span class="sxs-lookup"><span data-stu-id="a0af1-111">Element</span></span>|<span data-ttu-id="a0af1-112">説明</span><span class="sxs-lookup"><span data-stu-id="a0af1-112">Description</span></span>|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="a0af1-113">クライアント証明書の認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0af1-113">Specifies authentication options for the client certificate.</span></span>|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="a0af1-114">使用する証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0af1-114">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0af1-115">親要素</span><span class="sxs-lookup"><span data-stu-id="a0af1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a0af1-116">要素</span><span class="sxs-lookup"><span data-stu-id="a0af1-116">Element</span></span>|<span data-ttu-id="a0af1-117">説明</span><span class="sxs-lookup"><span data-stu-id="a0af1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="a0af1-118">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0af1-118">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0af1-119">解説</span><span class="sxs-lookup"><span data-stu-id="a0af1-119">Remarks</span></span>  

 <span data-ttu-id="a0af1-120">この要素は、サービスがクライアントと安全に通信するために、サービスが前もってクライアントの証明書を持っている必要がある場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="a0af1-120">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="a0af1-121">このような状況は、双方向通信パターンを使用する場合に生じます。</span><span class="sxs-lookup"><span data-stu-id="a0af1-121">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="a0af1-122">より一般的な要求/応答パターンでは、クライアントは自身の証明書を要求に含め、サービスはそれを使用してクライアントへの応答を暗号化し、署名します。</span><span class="sxs-lookup"><span data-stu-id="a0af1-122">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="a0af1-123">一方、双方向通信パターンでは、サービスにはクライアントからの要求が来ないので、クライアントの証明書をあらかじめ取得することで、クライアント宛のメッセージのセキュリティを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0af1-123">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="a0af1-124">このため、クライアントの証明書を帯域外のネゴシエーションで取得し、この要素を使用して証明書を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0af1-124">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="a0af1-125">双方向サービスの詳細については、「[方法: 双方向コントラクトを作成する](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0af1-125">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="a0af1-126">この要素で設定される証明書は、`MutualCertificateDuplex` メッセージ セキュリティ認証モードで構成されているバインディングのみを対象に、クライアントへのメッセージを暗号化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0af1-126">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0af1-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0af1-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="a0af1-128">方法: 双方向コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="a0af1-128">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="a0af1-129">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="a0af1-129">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a0af1-130">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="a0af1-130">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)

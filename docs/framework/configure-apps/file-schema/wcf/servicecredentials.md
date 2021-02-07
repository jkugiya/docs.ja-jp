---
description: '詳細情報: <serviceCredentials>'
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: c6fd39226ca2235d8f8253a7d2f2e363522870e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682866"
---
# \<serviceCredentials>

<span data-ttu-id="c2428-102">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2428-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="c2428-103">構文</span><span class="sxs-lookup"><span data-stu-id="c2428-103">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2428-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c2428-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c2428-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c2428-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2428-106">属性</span><span class="sxs-lookup"><span data-stu-id="c2428-106">Attributes</span></span>  
  
|<span data-ttu-id="c2428-107">属性</span><span class="sxs-lookup"><span data-stu-id="c2428-107">Attribute</span></span>|<span data-ttu-id="c2428-108">説明</span><span class="sxs-lookup"><span data-stu-id="c2428-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c2428-109">この設定要素の種類を指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="c2428-109">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2428-110">子要素</span><span class="sxs-lookup"><span data-stu-id="c2428-110">Child Elements</span></span>  
  
|<span data-ttu-id="c2428-111">要素</span><span class="sxs-lookup"><span data-stu-id="c2428-111">Element</span></span>|<span data-ttu-id="c2428-112">説明</span><span class="sxs-lookup"><span data-stu-id="c2428-112">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="c2428-113">クライアント証明書を帯域外で使用できるときに使用される証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2428-113">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="c2428-114">この要素は、クライアント証明書の検証設定も指定します。</span><span class="sxs-lookup"><span data-stu-id="c2428-114">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="c2428-115">この要素は <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="c2428-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="c2428-116">このサービス用に現在発行されているトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="c2428-116">Specifies the current issued token for this service.</span></span> <span data-ttu-id="c2428-117">この要素は <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="c2428-117">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="c2428-118">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2428-118">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="c2428-119">この要素は <xref:System.ServiceModel.Configuration.PeerCredentialElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="c2428-119">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="c2428-120">セキュリティで保護されたメッセージ交換の現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2428-120">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="c2428-121">この要素は <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="c2428-121">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="c2428-122">サービスが自身を識別するために使用する証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2428-122">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="c2428-123">この要素は <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="c2428-123">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="c2428-124">ユーザー名とパスワードの検証の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2428-124">Specifies the settings for username password validation.</span></span> <span data-ttu-id="c2428-125">この要素は <xref:System.ServiceModel.Configuration.UserNameServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="c2428-125">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="c2428-126">Windows 資格情報の検証の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2428-126">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="c2428-127">この要素は <xref:System.ServiceModel.Configuration.WindowsServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="c2428-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2428-128">親要素</span><span class="sxs-lookup"><span data-stu-id="c2428-128">Parent Elements</span></span>  
  
|<span data-ttu-id="c2428-129">要素</span><span class="sxs-lookup"><span data-stu-id="c2428-129">Element</span></span>|<span data-ttu-id="c2428-130">説明</span><span class="sxs-lookup"><span data-stu-id="c2428-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c2428-131">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2428-131">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2428-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2428-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="c2428-133">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="c2428-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)

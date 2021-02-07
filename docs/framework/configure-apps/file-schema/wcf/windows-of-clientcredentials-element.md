---
description: '詳細については、次を参照してください: <windows> of <clientCredentials> 要素'
title: <windows><clientCredentials>要素の
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: d693ad914dfa02ef12a7c8520ca84be3a9595e73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682424"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="d42fd-103">\<windows>\<clientCredentials>要素の</span><span class="sxs-lookup"><span data-stu-id="d42fd-103">\<windows> of \<clientCredentials> Element</span></span>

<span data-ttu-id="d42fd-104">クライアントを表すために使用される Windows 資格情報の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="d42fd-104">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="d42fd-105">構文</span><span class="sxs-lookup"><span data-stu-id="d42fd-105">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d42fd-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d42fd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d42fd-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d42fd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d42fd-108">属性</span><span class="sxs-lookup"><span data-stu-id="d42fd-108">Attributes</span></span>  
  
|<span data-ttu-id="d42fd-109">属性</span><span class="sxs-lookup"><span data-stu-id="d42fd-109">Attribute</span></span>|<span data-ttu-id="d42fd-110">説明</span><span class="sxs-lookup"><span data-stu-id="d42fd-110">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="d42fd-111">クライアントがサーバーと通信する偽装設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="d42fd-111">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="d42fd-112">クライアントが選択する偽装モードは、サーバーでは適用されません。</span><span class="sxs-lookup"><span data-stu-id="d42fd-112">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="d42fd-113">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d42fd-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d42fd-114">-識別: サーバーはクライアントの id と特権を取得できますが、クライアントの権限を借用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d42fd-114">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="d42fd-115">-権限借用: サーバーは、ローカルシステム上のクライアントのセキュリティコンテキストを偽装できます。</span><span class="sxs-lookup"><span data-stu-id="d42fd-115">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="d42fd-116">-委任: サーバーは、リモートシステム上のクライアントのセキュリティコンテキストを偽装できます。</span><span class="sxs-lookup"><span data-stu-id="d42fd-116">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="d42fd-117">-Anonymous: サーバーはクライアントの権限を借用または識別できません。</span><span class="sxs-lookup"><span data-stu-id="d42fd-117">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="d42fd-118">-None: 偽装レベルが割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="d42fd-118">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="d42fd-119">既定値は Identification です。</span><span class="sxs-lookup"><span data-stu-id="d42fd-119">The default is Identification.</span></span> <span data-ttu-id="d42fd-120">この属性は <xref:System.Security.Principal.TokenImpersonationLevel> 型です。</span><span class="sxs-lookup"><span data-stu-id="d42fd-120">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="d42fd-121">このプロパティを `true` に設定すると、Kerberos 認証を利用できない場合、NTLM 認証にダウングレードできます。</span><span class="sxs-lookup"><span data-stu-id="d42fd-121">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="d42fd-122">このプロパティをに設定する `false` と、NTLM が使用されている場合に Windows Communication Foundation (WCF) がベストエフォートで例外をスローするようになります。</span><span class="sxs-lookup"><span data-stu-id="d42fd-122">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="d42fd-123">ただし、このプロパティを `false` に設定しても、ネットワーク経由で NTLM 資格情報が送信されなくなるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="d42fd-123">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d42fd-124">子要素</span><span class="sxs-lookup"><span data-stu-id="d42fd-124">Child Elements</span></span>  

 <span data-ttu-id="d42fd-125">なし。</span><span class="sxs-lookup"><span data-stu-id="d42fd-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d42fd-126">親要素</span><span class="sxs-lookup"><span data-stu-id="d42fd-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d42fd-127">要素</span><span class="sxs-lookup"><span data-stu-id="d42fd-127">Element</span></span>|<span data-ttu-id="d42fd-128">説明</span><span class="sxs-lookup"><span data-stu-id="d42fd-128">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="d42fd-129">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="d42fd-129">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d42fd-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="d42fd-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="d42fd-131">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d42fd-131">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="d42fd-132">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="d42fd-132">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d42fd-133">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d42fd-133">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)

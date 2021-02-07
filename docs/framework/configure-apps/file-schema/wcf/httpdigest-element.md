---
description: '詳細情報: <httpDigest> 要素'
title: <httpDigest> 要素
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2b11edcaab88ff3a2b437b1e886997e08b8c9fee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749663"
---
# <a name="httpdigest-element"></a><span data-ttu-id="ceebf-103">\<httpDigest> 要素</span><span class="sxs-lookup"><span data-stu-id="ceebf-103">\<httpDigest> Element</span></span>

<span data-ttu-id="ceebf-104">サービスに対するクライアントの認証時に使用されるダイジェスト型の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="ceebf-104">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**  
  
## <a name="syntax"></a><span data-ttu-id="ceebf-105">構文</span><span class="sxs-lookup"><span data-stu-id="ceebf-105">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceebf-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ceebf-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ceebf-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ceebf-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceebf-108">属性</span><span class="sxs-lookup"><span data-stu-id="ceebf-108">Attributes</span></span>  
  
|<span data-ttu-id="ceebf-109">属性</span><span class="sxs-lookup"><span data-stu-id="ceebf-109">Attribute</span></span>|<span data-ttu-id="ceebf-110">説明</span><span class="sxs-lookup"><span data-stu-id="ceebf-110">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="ceebf-111">クライアントがサーバーと通信する偽装設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="ceebf-111">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="ceebf-112">クライアントが選択する偽装モードは、サーバーでは適用されません。</span><span class="sxs-lookup"><span data-stu-id="ceebf-112">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="ceebf-113">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ceebf-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ceebf-114">-識別: サーバーはクライアントの id と特権を取得できますが、クライアントの権限を借用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ceebf-114">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="ceebf-115">-権限借用: サーバーは、ローカルシステム上のクライアントのセキュリティコンテキストを偽装できます。</span><span class="sxs-lookup"><span data-stu-id="ceebf-115">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="ceebf-116">-委任: サーバーは、リモートシステム上のクライアントのセキュリティコンテキストを偽装できます。</span><span class="sxs-lookup"><span data-stu-id="ceebf-116">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="ceebf-117">-Anonymous: サーバーはクライアントの権限を借用または識別できません。</span><span class="sxs-lookup"><span data-stu-id="ceebf-117">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="ceebf-118">-None: 偽装レベルが割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="ceebf-118">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="ceebf-119">既定値は Identification です。</span><span class="sxs-lookup"><span data-stu-id="ceebf-119">The default is Identification.</span></span> <span data-ttu-id="ceebf-120">この属性は <xref:System.Security.Principal.TokenImpersonationLevel> 型です。</span><span class="sxs-lookup"><span data-stu-id="ceebf-120">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ceebf-121">子要素</span><span class="sxs-lookup"><span data-stu-id="ceebf-121">Child Elements</span></span>  

 <span data-ttu-id="ceebf-122">なし</span><span class="sxs-lookup"><span data-stu-id="ceebf-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ceebf-123">親要素</span><span class="sxs-lookup"><span data-stu-id="ceebf-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ceebf-124">要素</span><span class="sxs-lookup"><span data-stu-id="ceebf-124">Element</span></span>|<span data-ttu-id="ceebf-125">説明</span><span class="sxs-lookup"><span data-stu-id="ceebf-125">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="ceebf-126">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="ceebf-126">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceebf-127">解説</span><span class="sxs-lookup"><span data-stu-id="ceebf-127">Remarks</span></span>  

 <span data-ttu-id="ceebf-128">ダイジェストは、アルゴリズムと入力セットを使用して決定されるハッシュです。</span><span class="sxs-lookup"><span data-stu-id="ceebf-128">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="ceebf-129">認証する側と認証される側はアルゴリズムに同意し、入力として使用されるデータを交換します。</span><span class="sxs-lookup"><span data-stu-id="ceebf-129">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="ceebf-130">クライアントはハッシュを計算して、サービスに送信できます。</span><span class="sxs-lookup"><span data-stu-id="ceebf-130">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="ceebf-131">また、サービスもハッシュを計算して、値を比較します。</span><span class="sxs-lookup"><span data-stu-id="ceebf-131">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="ceebf-132">一致すると、クライアントが検証されます。</span><span class="sxs-lookup"><span data-stu-id="ceebf-132">A match validates the client.</span></span>  
  
 <span data-ttu-id="ceebf-133">この機能は、Windows の Active Directory およびインターネット インフォメーション サービス (IIS) と共に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ceebf-133">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="ceebf-134">詳細については、「 [IIS 6.0 でのダイジェスト認証](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ceebf-134">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceebf-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="ceebf-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="ceebf-136">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="ceebf-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ceebf-137">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="ceebf-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ceebf-138">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="ceebf-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ceebf-139">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="ceebf-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)

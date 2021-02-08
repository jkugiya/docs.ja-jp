---
description: 詳細については <transport> 、 <webHttpBinding>
title: <transport> の <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: a845786f4e60a44dcb157201235d28d49ab8d40b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773447"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="95478-103">\<transport> の \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="95478-103">\<transport> of \<webHttpBinding></span></span>

<span data-ttu-id="95478-104">HTTP 要求を受信するように構成されたサービス エンドポイントのトランスポート レベルのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="95478-104">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="95478-105">構文</span><span class="sxs-lookup"><span data-stu-id="95478-105">Syntax</span></span>  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="95478-106">Type</span><span class="sxs-lookup"><span data-stu-id="95478-106">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95478-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="95478-107">Attributes and Elements</span></span>  

 <span data-ttu-id="95478-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="95478-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95478-109">属性</span><span class="sxs-lookup"><span data-stu-id="95478-109">Attributes</span></span>  
  
|<span data-ttu-id="95478-110">属性</span><span class="sxs-lookup"><span data-stu-id="95478-110">Attribute</span></span>|<span data-ttu-id="95478-111">説明</span><span class="sxs-lookup"><span data-stu-id="95478-111">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="95478-112">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="95478-112">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="95478-113">この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="95478-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="95478-114">ドメイン プロキシに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="95478-114">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="95478-115">この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="95478-115">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="95478-116">ダイジェストまたは基本認証の認証レルムを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="95478-116">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="95478-117">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="95478-117">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="95478-118">認証レルムでは、少なくとも、認証を実行するホストの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="95478-118">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="95478-119">アクセス権のあるユーザーのコレクションも指定できます。</span><span class="sxs-lookup"><span data-stu-id="95478-119">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="95478-120">ユーザーは、認証レルムを照会して、複数のユーザー名およびパスワードの候補のうち、どれを使用できるかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="95478-120">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="95478-121">この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="95478-121">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="95478-122">1. never –ポリシーは適用されません (拡張保護は無効になります)。</span><span class="sxs-lookup"><span data-stu-id="95478-122">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="95478-123">2. WhenSupported –ポリシーは、クライアントが拡張保護をサポートしている場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="95478-123">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="95478-124">3. always –ポリシーは常に適用されます。</span><span class="sxs-lookup"><span data-stu-id="95478-124">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="95478-125">拡張保護をサポートしていないクライアントは認証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="95478-125">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="95478-126">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="95478-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="95478-127">値</span><span class="sxs-lookup"><span data-stu-id="95478-127">Value</span></span>|<span data-ttu-id="95478-128">説明</span><span class="sxs-lookup"><span data-stu-id="95478-128">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="95478-129">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="95478-129">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="95478-130">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="95478-130">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="95478-131">X.509 証明書を使用して、クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="95478-131">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="95478-132">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="95478-132">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="95478-133">Windows ドメインのフォールバックとして NTLM 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="95478-133">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="95478-134">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="95478-134">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="95478-135">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="95478-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="95478-136">値</span><span class="sxs-lookup"><span data-stu-id="95478-136">Value</span></span>|<span data-ttu-id="95478-137">説明</span><span class="sxs-lookup"><span data-stu-id="95478-137">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="95478-138">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="95478-138">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="95478-139">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="95478-139">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="95478-140">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="95478-140">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="95478-141">Windows ドメインのフォールバックとして NTLM を使用します。</span><span class="sxs-lookup"><span data-stu-id="95478-141">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="95478-142">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="95478-142">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95478-143">子要素</span><span class="sxs-lookup"><span data-stu-id="95478-143">Child Elements</span></span>  

 <span data-ttu-id="95478-144">なし。</span><span class="sxs-lookup"><span data-stu-id="95478-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95478-145">親要素</span><span class="sxs-lookup"><span data-stu-id="95478-145">Parent Elements</span></span>  
  
|<span data-ttu-id="95478-146">要素</span><span class="sxs-lookup"><span data-stu-id="95478-146">Element</span></span>|<span data-ttu-id="95478-147">説明</span><span class="sxs-lookup"><span data-stu-id="95478-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="95478-148">要素のセキュリティ機能を表し [\<wsHttpBinding>](wshttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="95478-148">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95478-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="95478-149">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="95478-150">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="95478-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="95478-151">バインド</span><span class="sxs-lookup"><span data-stu-id="95478-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="95478-152">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="95478-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="95478-153">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="95478-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="95478-154">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="95478-154">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)

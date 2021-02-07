---
description: 詳細については <transport> 、 <wsHttpBinding>
title: <transport> の <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 7801148d76aaa9c074eeb7a83c1dd2fa152d871c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749299"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="04bd9-103">\<transport> の \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="04bd9-103">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="04bd9-104">HTTP トランスポートの認証設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-104">Defines authentication settings for the HTTP transport.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a><span data-ttu-id="04bd9-105">構文</span><span class="sxs-lookup"><span data-stu-id="04bd9-105">Syntax</span></span>

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a><span data-ttu-id="04bd9-106">Type</span><span class="sxs-lookup"><span data-stu-id="04bd9-106">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="04bd9-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="04bd9-107">Attributes and Elements</span></span>

<span data-ttu-id="04bd9-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="04bd9-109">属性</span><span class="sxs-lookup"><span data-stu-id="04bd9-109">Attributes</span></span>

|<span data-ttu-id="04bd9-110">属性</span><span class="sxs-lookup"><span data-stu-id="04bd9-110">Attribute</span></span>|<span data-ttu-id="04bd9-111">説明</span><span class="sxs-lookup"><span data-stu-id="04bd9-111">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="04bd9-112">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-112">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="04bd9-113">この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="04bd9-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="04bd9-114">ドメイン プロキシに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-114">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="04bd9-115">この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="04bd9-115">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="04bd9-116">ダイジェストまたは基本認証の認証レルムを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="04bd9-116">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="04bd9-117">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="04bd9-117">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="04bd9-118">認証レルムでは、少なくとも、認証を実行するホストの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-118">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="04bd9-119">アクセス権のあるユーザーのコレクションも指定できます。</span><span class="sxs-lookup"><span data-stu-id="04bd9-119">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="04bd9-120">ユーザーは、認証レルムを照会して、複数のユーザー名およびパスワードの候補のうち、どれを使用できるかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="04bd9-120">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="04bd9-121">この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-121">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="04bd9-122">1. never –ポリシーは適用されません (拡張保護は無効になります)。</span><span class="sxs-lookup"><span data-stu-id="04bd9-122">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="04bd9-123">2. WhenSupported –ポリシーは、クライアントが拡張保護をサポートしている場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="04bd9-123">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="04bd9-124">3. always –ポリシーは常に適用されます。</span><span class="sxs-lookup"><span data-stu-id="04bd9-124">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="04bd9-125">拡張保護をサポートしていないクライアントは認証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-125">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="04bd9-126">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="04bd9-126">clientCredentialType Attribute</span></span>

|<span data-ttu-id="04bd9-127">値</span><span class="sxs-lookup"><span data-stu-id="04bd9-127">Value</span></span>|<span data-ttu-id="04bd9-128">説明</span><span class="sxs-lookup"><span data-stu-id="04bd9-128">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="04bd9-129">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="04bd9-129">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="04bd9-130">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-130">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="04bd9-131">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-131">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="04bd9-132">Windows ドメインのフォールバックとして NTLM 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="04bd9-133">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-133">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="04bd9-134">X.509 証明書を使用して、クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-134">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="04bd9-135">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="04bd9-135">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="04bd9-136">値</span><span class="sxs-lookup"><span data-stu-id="04bd9-136">Value</span></span>|<span data-ttu-id="04bd9-137">説明</span><span class="sxs-lookup"><span data-stu-id="04bd9-137">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="04bd9-138">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="04bd9-138">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="04bd9-139">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-139">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="04bd9-140">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-140">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="04bd9-141">Windows ドメインのフォールバックとして NTLM を使用します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-141">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="04bd9-142">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-142">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="04bd9-143">X.509 証明書を使用して、クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="04bd9-143">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="04bd9-144">子要素</span><span class="sxs-lookup"><span data-stu-id="04bd9-144">Child Elements</span></span>

<span data-ttu-id="04bd9-145">なし。</span><span class="sxs-lookup"><span data-stu-id="04bd9-145">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="04bd9-146">親要素</span><span class="sxs-lookup"><span data-stu-id="04bd9-146">Parent Elements</span></span>

|<span data-ttu-id="04bd9-147">要素</span><span class="sxs-lookup"><span data-stu-id="04bd9-147">Element</span></span>|<span data-ttu-id="04bd9-148">説明</span><span class="sxs-lookup"><span data-stu-id="04bd9-148">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="04bd9-149">のセキュリティ機能を表し [\<wsHttpBinding>](wshttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="04bd9-149">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="04bd9-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="04bd9-150">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="04bd9-151">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="04bd9-151">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="04bd9-152">バインド</span><span class="sxs-lookup"><span data-stu-id="04bd9-152">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="04bd9-153">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="04bd9-153">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="04bd9-154">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="04bd9-154">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

---
description: 詳細については <transport> 、 <netHttpBinding>
title: <transport> の <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 1c2029fcbc57632b828fa180ba0ffbbf6b974775
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773512"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="cc73e-103">\<transport> の \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="cc73e-103">\<transport> of \<netHttpBinding></span></span>

<span data-ttu-id="cc73e-104">HTTP トランスポートの認証パラメーターを制御するプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-104">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="cc73e-105">構文</span><span class="sxs-lookup"><span data-stu-id="cc73e-105">Syntax</span></span>  
  
```xml  
<netHttpBinding>
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
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc73e-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cc73e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cc73e-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc73e-108">属性</span><span class="sxs-lookup"><span data-stu-id="cc73e-108">Attributes</span></span>  
  
|<span data-ttu-id="cc73e-109">属性</span><span class="sxs-lookup"><span data-stu-id="cc73e-109">Attribute</span></span>|<span data-ttu-id="cc73e-110">説明</span><span class="sxs-lookup"><span data-stu-id="cc73e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc73e-111">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="cc73e-111">clientCredentialType</span></span>|<span data-ttu-id="cc73e-112">-HTTP 認証を使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-112">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="cc73e-113">既定値は、`None` です。</span><span class="sxs-lookup"><span data-stu-id="cc73e-113">The default is `None`.</span></span> <span data-ttu-id="cc73e-114">この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="cc73e-114">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="cc73e-115">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="cc73e-115">proxyCredentialType</span></span>|<span data-ttu-id="cc73e-116">-HTTP 経由のプロキシを使用してドメイン内からクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-116">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="cc73e-117">この属性は、親 `mode` 要素の `security` 属性が `Transport` または `TransportCredentialsOnly` の場合にだけ適用されます。</span><span class="sxs-lookup"><span data-stu-id="cc73e-117">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="cc73e-118">この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="cc73e-118">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="cc73e-119">realm</span><span class="sxs-lookup"><span data-stu-id="cc73e-119">realm</span></span>|<span data-ttu-id="cc73e-120">ダイジェストまたは基本認証の HTTP 認証方式によって使用されるレルムを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="cc73e-120">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="cc73e-121">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="cc73e-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="cc73e-122">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="cc73e-122">policyEnforcement</span></span>|<span data-ttu-id="cc73e-123">この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-123">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="cc73e-124">1. never –ポリシーは適用されません (拡張保護は無効になります)。</span><span class="sxs-lookup"><span data-stu-id="cc73e-124">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="cc73e-125">2. WhenSupported –ポリシーは、クライアントが拡張保護をサポートしている場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="cc73e-125">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="cc73e-126">3. always –ポリシーは常に適用されます。</span><span class="sxs-lookup"><span data-stu-id="cc73e-126">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="cc73e-127">拡張保護をサポートしていないクライアントは認証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-127">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="cc73e-128">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="cc73e-128">protectionScenario</span></span>|<span data-ttu-id="cc73e-129">この列挙体は、ポリシーによって適用される保護シナリオを指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-129">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="cc73e-130">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="cc73e-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="cc73e-131">値</span><span class="sxs-lookup"><span data-stu-id="cc73e-131">Value</span></span>|<span data-ttu-id="cc73e-132">説明</span><span class="sxs-lookup"><span data-stu-id="cc73e-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cc73e-133">なし</span><span class="sxs-lookup"><span data-stu-id="cc73e-133">None</span></span>|<span data-ttu-id="cc73e-134">メッセージは、転送中はセキュリティで保護されません。</span><span class="sxs-lookup"><span data-stu-id="cc73e-134">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="cc73e-135">Basic</span><span class="sxs-lookup"><span data-stu-id="cc73e-135">Basic</span></span>|<span data-ttu-id="cc73e-136">基本認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-136">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="cc73e-137">ダイジェスト</span><span class="sxs-lookup"><span data-stu-id="cc73e-137">Digest</span></span>|<span data-ttu-id="cc73e-138">ダイジェスト認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-138">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="cc73e-139">Ntlm</span><span class="sxs-lookup"><span data-stu-id="cc73e-139">Ntlm</span></span>|<span data-ttu-id="cc73e-140">Windows 認証に失敗した場合で可能な場合は、NTLM 認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-140">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="cc73e-141">Windows</span><span class="sxs-lookup"><span data-stu-id="cc73e-141">Windows</span></span>|<span data-ttu-id="cc73e-142">Windows 統合認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-142">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="cc73e-143">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="cc73e-143">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="cc73e-144">値</span><span class="sxs-lookup"><span data-stu-id="cc73e-144">Value</span></span>|<span data-ttu-id="cc73e-145">説明</span><span class="sxs-lookup"><span data-stu-id="cc73e-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cc73e-146">なし</span><span class="sxs-lookup"><span data-stu-id="cc73e-146">None</span></span>|<span data-ttu-id="cc73e-147">-メッセージは、転送中にセキュリティ保護されません。</span><span class="sxs-lookup"><span data-stu-id="cc73e-147">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="cc73e-148">Basic</span><span class="sxs-lookup"><span data-stu-id="cc73e-148">Basic</span></span>|<span data-ttu-id="cc73e-149">RFC 2617 『HTTP Authentication: Basic and Digest Authentication』で定義されているとおりに基本認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-149">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="cc73e-150">ダイジェスト</span><span class="sxs-lookup"><span data-stu-id="cc73e-150">Digest</span></span>|<span data-ttu-id="cc73e-151">RFC 2617 『HTTP Authentication: Basic and Digest Authentication』で定義されているとおりにダイジェスト認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-151">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="cc73e-152">Ntlm</span><span class="sxs-lookup"><span data-stu-id="cc73e-152">Ntlm</span></span>|<span data-ttu-id="cc73e-153">Windows 認証に失敗した場合で可能な場合は、NTLM 認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-153">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="cc73e-154">Windows</span><span class="sxs-lookup"><span data-stu-id="cc73e-154">Windows</span></span>|<span data-ttu-id="cc73e-155">Windows 統合認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-155">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="cc73e-156">Certificate</span><span class="sxs-lookup"><span data-stu-id="cc73e-156">Certificate</span></span>|<span data-ttu-id="cc73e-157">証明書を使用したクライアント認証を実行します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-157">Performs client authentication using a certificate.</span></span> <span data-ttu-id="cc73e-158">このオプションは、親要素の `Mode` の `security` 属性が Transport に設定されている場合のみ機能し、TransportCredentialOnly に設定されている場合は機能しません。</span><span class="sxs-lookup"><span data-stu-id="cc73e-158">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc73e-159">子要素</span><span class="sxs-lookup"><span data-stu-id="cc73e-159">Child Elements</span></span>  

 <span data-ttu-id="cc73e-160">なし</span><span class="sxs-lookup"><span data-stu-id="cc73e-160">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc73e-161">親要素</span><span class="sxs-lookup"><span data-stu-id="cc73e-161">Parent Elements</span></span>  
  
|<span data-ttu-id="cc73e-162">要素</span><span class="sxs-lookup"><span data-stu-id="cc73e-162">Element</span></span>|<span data-ttu-id="cc73e-163">説明</span><span class="sxs-lookup"><span data-stu-id="cc73e-163">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|<span data-ttu-id="cc73e-164">のセキュリティ機能を定義 [\<netHttpBinding>](nethttpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-164">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cc73e-165">例</span><span class="sxs-lookup"><span data-stu-id="cc73e-165">Example</span></span>  

 <span data-ttu-id="cc73e-166">基本的なバインディングを使用した SSL トランスポート セキュリティの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cc73e-166">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="cc73e-167">既定で、基本的なバインディングは HTTP 通信をサポートします。</span><span class="sxs-lookup"><span data-stu-id="cc73e-167">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="cc73e-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc73e-168">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="cc73e-169">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="cc73e-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cc73e-170">バインド</span><span class="sxs-lookup"><span data-stu-id="cc73e-170">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cc73e-171">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="cc73e-171">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cc73e-172">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="cc73e-172">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

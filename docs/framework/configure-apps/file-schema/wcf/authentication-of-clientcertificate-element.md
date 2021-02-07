---
description: '詳細については、次を参照してください: <authentication> of <clientCertificate> 要素'
title: <authentication><clientCertificate>要素の
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 346e1012fd9d799b093be15381aebbc026ea2591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749897"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="eb61f-103">\<authentication>\<clientCertificate>要素の</span><span class="sxs-lookup"><span data-stu-id="eb61f-103">\<authentication> of \<clientCertificate> Element</span></span>

<span data-ttu-id="eb61f-104">サービスによって使用されるクライアント証明書の認証動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-104">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="eb61f-105">構文</span><span class="sxs-lookup"><span data-stu-id="eb61f-105">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb61f-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="eb61f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="eb61f-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb61f-108">属性</span><span class="sxs-lookup"><span data-stu-id="eb61f-108">Attributes</span></span>  
  
|<span data-ttu-id="eb61f-109">属性</span><span class="sxs-lookup"><span data-stu-id="eb61f-109">Attribute</span></span>|<span data-ttu-id="eb61f-110">説明</span><span class="sxs-lookup"><span data-stu-id="eb61f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb61f-111">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="eb61f-111">customCertificateValidatorType</span></span>|<span data-ttu-id="eb61f-112">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="eb61f-112">Optional string.</span></span> <span data-ttu-id="eb61f-113">カスタム型の検証に使用される型およびアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="eb61f-113">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="eb61f-114">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb61f-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="eb61f-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="eb61f-115">certificateValidationMode</span></span>|<span data-ttu-id="eb61f-116">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="eb61f-116">Optional enumeration.</span></span> <span data-ttu-id="eb61f-117">資格情報の検証に使用されるモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-117">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="eb61f-118">この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="eb61f-118">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="eb61f-119"><xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType> に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb61f-119">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="eb61f-120">既定値は、<xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="eb61f-120">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="eb61f-121">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="eb61f-121">includeWindowsGroups</span></span>|<span data-ttu-id="eb61f-122">省略可能なブール。</span><span class="sxs-lookup"><span data-stu-id="eb61f-122">Optional Boolean.</span></span> <span data-ttu-id="eb61f-123">セキュリティ コンテキストに Windows グループが含まれているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-123">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="eb61f-124">この属性を `true` に設定すると、グループ全体が拡張されるため、パフォーマンスに影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="eb61f-124">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="eb61f-125">ユーザーが属するグループの一覧を生成する必要がない場合は、この属性を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-125">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="eb61f-126">mapClientCertificateToWindowsAccount</span><span class="sxs-lookup"><span data-stu-id="eb61f-126">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="eb61f-127">ブール型。</span><span class="sxs-lookup"><span data-stu-id="eb61f-127">Boolean.</span></span> <span data-ttu-id="eb61f-128">証明書を使用してクライアントを Windows ID にマップできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-128">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="eb61f-129">これを行うには、Active Directory が有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb61f-129">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="eb61f-130">revocationMode</span><span class="sxs-lookup"><span data-stu-id="eb61f-130">revocationMode</span></span>|<span data-ttu-id="eb61f-131">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="eb61f-131">Optional enumeration.</span></span> <span data-ttu-id="eb61f-132">証明書失効リスト (RCL) のチェックに使用されるモードのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="eb61f-132">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="eb61f-133">既定値は、`Online` です。</span><span class="sxs-lookup"><span data-stu-id="eb61f-133">The default is `Online`.</span></span> <span data-ttu-id="eb61f-134">この値は、HTTP トランスポート セキュリティを使用する場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="eb61f-134">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="eb61f-135">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="eb61f-135">trustedStoreLocation</span></span>|<span data-ttu-id="eb61f-136">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="eb61f-136">Optional enumeration.</span></span> <span data-ttu-id="eb61f-137">2 つのシステム格納場所 (`LocalMachine` または `CurrentUser`) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="eb61f-137">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="eb61f-138">この値は、サービス証明書がクライアントにネゴシエートされるときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="eb61f-138">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="eb61f-139">指定されたストアの場所にある **信頼さ** れた People ストアに対して検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="eb61f-139">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="eb61f-140">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="eb61f-140">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="eb61f-141">customCertificateValidatorType 属性</span><span class="sxs-lookup"><span data-stu-id="eb61f-141">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="eb61f-142">値</span><span class="sxs-lookup"><span data-stu-id="eb61f-142">Value</span></span>|<span data-ttu-id="eb61f-143">説明</span><span class="sxs-lookup"><span data-stu-id="eb61f-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eb61f-144">String</span><span class="sxs-lookup"><span data-stu-id="eb61f-144">String</span></span>|<span data-ttu-id="eb61f-145">タイプ名およびアセンブリと、タイプの検索に使用される他のデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-145">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="eb61f-146">certificateValidationMode 属性</span><span class="sxs-lookup"><span data-stu-id="eb61f-146">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="eb61f-147">値</span><span class="sxs-lookup"><span data-stu-id="eb61f-147">Value</span></span>|<span data-ttu-id="eb61f-148">説明</span><span class="sxs-lookup"><span data-stu-id="eb61f-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eb61f-149">列挙</span><span class="sxs-lookup"><span data-stu-id="eb61f-149">Enumeration</span></span>|<span data-ttu-id="eb61f-150">None、PeerTrust、ChainTrust、PeerOrChainTrust、Custom のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="eb61f-150">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="eb61f-151">詳細については、「 [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb61f-151">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="eb61f-152">revocationMode 属性</span><span class="sxs-lookup"><span data-stu-id="eb61f-152">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="eb61f-153">値</span><span class="sxs-lookup"><span data-stu-id="eb61f-153">Value</span></span>|<span data-ttu-id="eb61f-154">説明</span><span class="sxs-lookup"><span data-stu-id="eb61f-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eb61f-155">列挙</span><span class="sxs-lookup"><span data-stu-id="eb61f-155">Enumeration</span></span>|<span data-ttu-id="eb61f-156">NoCheck、Online、Offline のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="eb61f-156">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="eb61f-157">詳細については、「 [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb61f-157">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="eb61f-158">trustedStoreLocation 属性</span><span class="sxs-lookup"><span data-stu-id="eb61f-158">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="eb61f-159">値</span><span class="sxs-lookup"><span data-stu-id="eb61f-159">Value</span></span>|<span data-ttu-id="eb61f-160">説明</span><span class="sxs-lookup"><span data-stu-id="eb61f-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eb61f-161">列挙</span><span class="sxs-lookup"><span data-stu-id="eb61f-161">Enumeration</span></span>|<span data-ttu-id="eb61f-162">次のいずれかの値を指定できます。`LocalMachine` または `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="eb61f-162">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="eb61f-163">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="eb61f-163">The default is `CurrentUser`.</span></span> <span data-ttu-id="eb61f-164">クライアント アプリケーションがシステム アカウントで実行されている場合、証明書は通常 `LocalMachine` の下にあります。</span><span class="sxs-lookup"><span data-stu-id="eb61f-164">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="eb61f-165">クライアント アプリケーションがユーザー アカウントで実行されている場合、証明書は通常 `CurrentUser` の下にあります。</span><span class="sxs-lookup"><span data-stu-id="eb61f-165">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb61f-166">子要素</span><span class="sxs-lookup"><span data-stu-id="eb61f-166">Child Elements</span></span>  

 <span data-ttu-id="eb61f-167">なし。</span><span class="sxs-lookup"><span data-stu-id="eb61f-167">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb61f-168">親要素</span><span class="sxs-lookup"><span data-stu-id="eb61f-168">Parent Elements</span></span>  
  
|<span data-ttu-id="eb61f-169">要素</span><span class="sxs-lookup"><span data-stu-id="eb61f-169">Element</span></span>|<span data-ttu-id="eb61f-170">説明</span><span class="sxs-lookup"><span data-stu-id="eb61f-170">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="eb61f-171">サービスに対するクライアントの認証に使用する X.509 証明書を定義します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-171">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb61f-172">解説</span><span class="sxs-lookup"><span data-stu-id="eb61f-172">Remarks</span></span>  

 <span data-ttu-id="eb61f-173">`<authentication>` 要素は、<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> クラスに対応します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-173">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="eb61f-174">この要素を使用すると、クライアントを認証する方法をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="eb61f-174">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="eb61f-175">`certificateValidationMode` 属性は、`None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust`、または `Custom` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="eb61f-175">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="eb61f-176">既定では、レベルはに設定されています `ChainTrust` 。これは、チェーンの最上位にあるルート証明 *機関* で終了する証明書の階層構造で各証明書を検索する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-176">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="eb61f-177">これは最もセキュリティで保護されているモードです。</span><span class="sxs-lookup"><span data-stu-id="eb61f-177">This is the most secure mode.</span></span> <span data-ttu-id="eb61f-178">また、値を `PeerOrChainTrust` に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 (ピア信頼) も受け入れるよう指定します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-178">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="eb61f-179">自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。</span><span class="sxs-lookup"><span data-stu-id="eb61f-179">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="eb61f-180">クライアントを展開するときは、代わりに `ChainTrust` 値を使用します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-180">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="eb61f-181">また、値を `Custom` に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="eb61f-181">You can also set the value to `Custom`.</span></span> <span data-ttu-id="eb61f-182">`Custom` 値に設定する場合は、`customCertificateValidatorType` 属性を、証明書の検証に使用するアセンブリと型に設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="eb61f-182">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="eb61f-183">独自のカスタム検証を作成するには、抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスを継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb61f-183">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="eb61f-184">詳細については、「 [方法: カスタム証明書検証を使用するサービスを作成](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb61f-184">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb61f-185">例</span><span class="sxs-lookup"><span data-stu-id="eb61f-185">Example</span></span>  

 <span data-ttu-id="eb61f-186">次のコードは、`<authentication>` 要素の X.509 証明書とカスタム検証タイプを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb61f-186">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="eb61f-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb61f-187">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="eb61f-188">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="eb61f-188">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="eb61f-189">方法: カスタム証明書検証を使用するサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="eb61f-189">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="eb61f-190">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="eb61f-190">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)

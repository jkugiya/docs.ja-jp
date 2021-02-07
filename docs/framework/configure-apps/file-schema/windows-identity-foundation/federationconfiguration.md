---
description: '詳細情報: <federationConfiguration>'
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: f8793a8fbd6fc6d5e6994c8e368f587b740e5973
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748987"
---
# \<federationConfiguration>

<span data-ttu-id="517d3-102"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule> <xref:System.IdentityModel.Services.SessionAuthenticationModule> WS-Federation プロトコルを介してフェデレーション認証を使用する場合、(wsfam) と (SAM) を構成します。</span><span class="sxs-lookup"><span data-stu-id="517d3-102">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="517d3-103"><xref:System.Security.Claims.ClaimsAuthorizationManager> <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> またはクラスを使用して <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> クレームベースのアクセス制御を提供するときに、を構成します。</span><span class="sxs-lookup"><span data-stu-id="517d3-103">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="517d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="517d3-104">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="517d3-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="517d3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="517d3-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="517d3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="517d3-107">属性</span><span class="sxs-lookup"><span data-stu-id="517d3-107">Attributes</span></span>  
  
|<span data-ttu-id="517d3-108">属性</span><span class="sxs-lookup"><span data-stu-id="517d3-108">Attribute</span></span>|<span data-ttu-id="517d3-109">説明</span><span class="sxs-lookup"><span data-stu-id="517d3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="517d3-110">name</span><span class="sxs-lookup"><span data-stu-id="517d3-110">name</span></span>|<span data-ttu-id="517d3-111">フェデレーション構成要素の名前。</span><span class="sxs-lookup"><span data-stu-id="517d3-111">The name of this federation configuration element.</span></span> <span data-ttu-id="517d3-112">この属性は、主に将来のプロトコルの機能拡張ポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="517d3-112">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="517d3-113">任意。</span><span class="sxs-lookup"><span data-stu-id="517d3-113">Optional.</span></span>|  
|<span data-ttu-id="517d3-114">identity Configurationname</span><span class="sxs-lookup"><span data-stu-id="517d3-114">identityConfigurationName</span></span>|<span data-ttu-id="517d3-115">使用する要素で指定されている id 構成セクションの名前 [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="517d3-115">The name of the identity configuration section as specified in an [\<identityConfiguration>](identityconfiguration.md) element to use.</span></span> <span data-ttu-id="517d3-116">この属性が指定されていない場合は、既定の id 構成セクションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="517d3-116">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="517d3-117">任意。</span><span class="sxs-lookup"><span data-stu-id="517d3-117">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="517d3-118">子要素</span><span class="sxs-lookup"><span data-stu-id="517d3-118">Child Elements</span></span>  
  
|<span data-ttu-id="517d3-119">要素</span><span class="sxs-lookup"><span data-stu-id="517d3-119">Element</span></span>|<span data-ttu-id="517d3-120">説明</span><span class="sxs-lookup"><span data-stu-id="517d3-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="517d3-121">SAM によって使用されるクッキーハンドラーを構成します。</span><span class="sxs-lookup"><span data-stu-id="517d3-121">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="517d3-122">任意。</span><span class="sxs-lookup"><span data-stu-id="517d3-122">Optional.</span></span>|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="517d3-123">トークンの暗号化と復号化に使用される証明書を構成します。</span><span class="sxs-lookup"><span data-stu-id="517d3-123">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="517d3-124">任意。</span><span class="sxs-lookup"><span data-stu-id="517d3-124">Optional.</span></span>|  
|[\<wsFederation>](wsfederation.md)|<span data-ttu-id="517d3-125">WS-Federation 認証モジュール (WSFAM) を構成します。</span><span class="sxs-lookup"><span data-stu-id="517d3-125">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="517d3-126">任意。</span><span class="sxs-lookup"><span data-stu-id="517d3-126">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="517d3-127">親要素</span><span class="sxs-lookup"><span data-stu-id="517d3-127">Parent Elements</span></span>  
  
|<span data-ttu-id="517d3-128">要素</span><span class="sxs-lookup"><span data-stu-id="517d3-128">Element</span></span>|<span data-ttu-id="517d3-129">説明</span><span class="sxs-lookup"><span data-stu-id="517d3-129">Description</span></span>|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|<span data-ttu-id="517d3-130">WS-Federation プロトコルを使用した認証の構成セクション。</span><span class="sxs-lookup"><span data-stu-id="517d3-130">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="517d3-131">解説</span><span class="sxs-lookup"><span data-stu-id="517d3-131">Remarks</span></span>  

 <span data-ttu-id="517d3-132">要素は、 \<federationConfiguration> 2 つの異なるシナリオで設定を提供します。</span><span class="sxs-lookup"><span data-stu-id="517d3-132">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
- <span data-ttu-id="517d3-133">パッシブ Web アプリケーションで WS-Federation を使用する場合、要素には、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (wsfam) と (SAM) を構成する設定が含まれ <xref:System.IdentityModel.Services.SessionAuthenticationModule> ます。</span><span class="sxs-lookup"><span data-stu-id="517d3-133">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="517d3-134">また、セキュリティトークンハンドラーと証明書の構成に使用される id 構成と、要求承認マネージャーや要求認証マネージャーなどのコンポーネントも参照しています。</span><span class="sxs-lookup"><span data-stu-id="517d3-134">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
- <span data-ttu-id="517d3-135">クラスまたはクラスを使用して、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> コード内にクレームベースのアクセス制御を提供する場合、要素は、承認の決定に使用されるクレーム承認マネージャーとポリシーを構成する id 構成を参照します。</span><span class="sxs-lookup"><span data-stu-id="517d3-135">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="517d3-136">これは、パッシブな Web シナリオではないシナリオでも当てはまります。たとえば、Windows Communication Foundation (WCF) アプリケーションや、Web ベースではないアプリケーションなどです。</span><span class="sxs-lookup"><span data-stu-id="517d3-136">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="517d3-137">アプリケーションがパッシブな Web アプリケーションでない場合は、要素 [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) (およびその子ポリシー要素が存在する場合) は、要素によって参照される id 構成に適用される `<federationConfiguration>` 唯一の設定です。</span><span class="sxs-lookup"><span data-stu-id="517d3-137">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="517d3-138">他の属性はすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="517d3-138">All others are ignored.</span></span>  
  
 <span data-ttu-id="517d3-139">シナリオに関係なく、ランタイムは既定のフェデレーション構成を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="517d3-139">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="517d3-140">動作は次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="517d3-140">The behavior is defined as follows:</span></span>  
  
1. <span data-ttu-id="517d3-141">要素が存在しない場合 `<federationConfiguration>` 、ランタイムはフェデレーション構成を作成し、既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="517d3-141">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="517d3-142">この既定のフェデレーション構成では、既定の id 構成が参照されます。</span><span class="sxs-lookup"><span data-stu-id="517d3-142">This default federation configuration will reference the default identity configuration.</span></span>  
  
2. <span data-ttu-id="517d3-143">1つの `<federationConfiguration>` 要素が存在する場合は、名前が付けられているか名前が付いていないかに関係なく、既定のフェデレーション構成になります。</span><span class="sxs-lookup"><span data-stu-id="517d3-143">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="517d3-144">`identityConfiguration`属性が指定されている場合は、名前付き id 構成が参照されます。それ以外の場合は、既定の id 構成が参照されます。</span><span class="sxs-lookup"><span data-stu-id="517d3-144">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3. <span data-ttu-id="517d3-145">名前のない `<federationConfiguration>` 要素が存在する場合は、既定のフェデレーション構成になります。</span><span class="sxs-lookup"><span data-stu-id="517d3-145">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="517d3-146">`identityConfiguration`属性が指定されている場合は、名前付き id 構成が参照されます。それ以外の場合は、既定の id 構成が参照されます。</span><span class="sxs-lookup"><span data-stu-id="517d3-146">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4. <span data-ttu-id="517d3-147">複数の名前付き `<federationConfiguration>` 要素が存在し、名前のない要素が存在しない場合は `<federationConfiguration>` 、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="517d3-147">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="517d3-148">通常、1つの `<federationConfiguration>` セクションのみが定義されます。</span><span class="sxs-lookup"><span data-stu-id="517d3-148">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="517d3-149">このセクションは、既定のフェデレーション構成です。</span><span class="sxs-lookup"><span data-stu-id="517d3-149">This section is the default federation configuration.</span></span> <span data-ttu-id="517d3-150">一意の名前を持つ複数の要素を指定することもできます `<federationConfiguration>` 。ただし、この場合は、名前のないフェデレーション構成を読み込む場合は、のハンドラーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="517d3-150">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="517d3-151"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> イベントを発生さ <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> せると共に、ハンドラー内のプロパティを、 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 構成ファイル内の適切な要素の値で初期化されたオブジェクトに設定し `<federationConfiguration>` ます。</span><span class="sxs-lookup"><span data-stu-id="517d3-151"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="517d3-152">`<federationConfiguration>`要素は、クラスによって表され <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> ます。</span><span class="sxs-lookup"><span data-stu-id="517d3-152">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="517d3-153">構成オブジェクト自体は、クラスによって表され <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> ます。</span><span class="sxs-lookup"><span data-stu-id="517d3-153">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="517d3-154">1つの <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> インスタンスがプロパティに設定され、 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> アプリケーションのフェデレーション構成が提供されます。</span><span class="sxs-lookup"><span data-stu-id="517d3-154">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="517d3-155">例</span><span class="sxs-lookup"><span data-stu-id="517d3-155">Example</span></span>  

 <span data-ttu-id="517d3-156">次の XML は、 `<federationConfiguration>` WSFAM の設定を指定する要素を示し、既定の cookie ハンドラー (クラスのインスタンス <xref:System.IdentityModel.Services.ChunkedCookieHandler> ) が SAM によって使用されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="517d3-156">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="517d3-157">この例では、cookie ハンドラーも WSFAM も HTTPS を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="517d3-157">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="517d3-158">これは、 `requireHttps` 要素の属性 `<wsFederation>` と `requireSsl` の属性 `<cookieHandlerElement>` が `false` であるためです。</span><span class="sxs-lookup"><span data-stu-id="517d3-158">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="517d3-159">ほとんどの運用環境では、セキュリティ上のリスクが生じる可能性があるため、これらの設定は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="517d3-159">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"
      issuer="http://localhost:15839/wsFederationSTS/Issue"
      realm="http://localhost:50969/" reply="http://localhost:50969/"
      requireHttps="false"
      signOutReply="http://localhost:50969/SignedOutPage.html"
      signOutQueryString="Param1=value2&Param2=value2"
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="see-also"></a><span data-ttu-id="517d3-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="517d3-160">See also</span></span>

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)

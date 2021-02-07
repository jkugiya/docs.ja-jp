---
description: '詳細情報: <securityTokenHandlerConfiguration>'
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 8c014d971d3e8cc640a3b7042e3a0266d902de7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698311"
---
# \<securityTokenHandlerConfiguration>

<span data-ttu-id="a2594-102">トークンハンドラーのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="a2594-102">Provides configuration for the collection of token handlers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="a2594-103">構文</span><span class="sxs-lookup"><span data-stu-id="a2594-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2594-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a2594-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a2594-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2594-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2594-106">属性</span><span class="sxs-lookup"><span data-stu-id="a2594-106">Attributes</span></span>  
  
|<span data-ttu-id="a2594-107">属性</span><span class="sxs-lookup"><span data-stu-id="a2594-107">Attribute</span></span>|<span data-ttu-id="a2594-108">説明</span><span class="sxs-lookup"><span data-stu-id="a2594-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2594-109">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="a2594-109">saveBootstrapContext</span></span>|<span data-ttu-id="a2594-110">ブートストラップトークンをセッショントークンに含める必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2594-110">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="a2594-111">また、要素の属性を設定することによって、トークンハンドラーコレクションに値を設定することもでき `saveBootstrapContext` [\<identityConfiguration>](identityconfiguration.md) ます。</span><span class="sxs-lookup"><span data-stu-id="a2594-111">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="a2594-112">トークンハンドラーコレクションに設定された値は、サービスで設定された値よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="a2594-112">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="a2594-113">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="a2594-113">maximumClockSkew</span></span>|<span data-ttu-id="a2594-114"><xref:System.TimeSpan>許容される最大のクロックスキューを指定する。</span><span class="sxs-lookup"><span data-stu-id="a2594-114">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="a2594-115">サインインセッションの有効期限の検証など、時間を区別する操作を実行するときに許容される最大のクロックスキューを制御します。</span><span class="sxs-lookup"><span data-stu-id="a2594-115">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="a2594-116">既定値は5分 "00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="a2594-116">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="a2594-117">値を指定する方法の詳細について <xref:System.TimeSpan> は、「 [Timespan values](../windows-workflow-foundation/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2594-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="a2594-118">また、要素の属性を設定することによって、サービスレベルで時刻のずれの最大値を設定することもでき `maximumClockSkew` [\<identityConfiguration>](identityconfiguration.md) ます。</span><span class="sxs-lookup"><span data-stu-id="a2594-118">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="a2594-119">トークンハンドラーコレクションに設定された値は、サービスで設定された値よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="a2594-119">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2594-120">子要素</span><span class="sxs-lookup"><span data-stu-id="a2594-120">Child Elements</span></span>  
  
|<span data-ttu-id="a2594-121">要素</span><span class="sxs-lookup"><span data-stu-id="a2594-121">Element</span></span>|<span data-ttu-id="a2594-122">説明</span><span class="sxs-lookup"><span data-stu-id="a2594-122">Description</span></span>|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|<span data-ttu-id="a2594-123">この証明書利用者の許容される識別子である Uri のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2594-123">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="a2594-124">任意。</span><span class="sxs-lookup"><span data-stu-id="a2594-124">Optional.</span></span>|  
|[\<caches>](caches.md)|<span data-ttu-id="a2594-125">セッショントークンとトークンリプレイ検出に使用されるキャッシュを登録します。</span><span class="sxs-lookup"><span data-stu-id="a2594-125">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="a2594-126">は、サービスレベルまたはセキュリティトークンハンドラーコレクションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="a2594-126">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="a2594-127">任意。</span><span class="sxs-lookup"><span data-stu-id="a2594-127">Optional.</span></span>|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="a2594-128">トークンハンドラーが証明書を検証するために使用する設定を制御します。</span><span class="sxs-lookup"><span data-stu-id="a2594-128">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="a2594-129">は、サービスレベルまたはセキュリティトークンハンドラーコレクションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="a2594-129">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="a2594-130">特定のハンドラーが独自の検証コントロールを使用して構成されている場合、これらの設定はオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="a2594-130">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="a2594-131">任意。</span><span class="sxs-lookup"><span data-stu-id="a2594-131">Optional.</span></span>|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="a2594-132">トークンハンドラーコレクションのハンドラーによって使用される発行者名レジストリを構成します。</span><span class="sxs-lookup"><span data-stu-id="a2594-132">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a2594-133">任意。</span><span class="sxs-lookup"><span data-stu-id="a2594-133">Optional.</span></span>|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|<span data-ttu-id="a2594-134">トークンハンドラーコレクションのハンドラーによって使用される発行者トークンリゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="a2594-134">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a2594-135">発行者トークンリゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a2594-135">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="a2594-136">任意。</span><span class="sxs-lookup"><span data-stu-id="a2594-136">Optional.</span></span>|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|<span data-ttu-id="a2594-137">トークンハンドラーコレクションのハンドラーによって使用されるサービストークンリゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="a2594-137">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a2594-138">サービストークンリゾルバーは、受信トークンとメッセージの暗号化トークンを解決するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a2594-138">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="a2594-139">任意。</span><span class="sxs-lookup"><span data-stu-id="a2594-139">Optional.</span></span>|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="a2594-140">トークンリプレイ検出を有効にし、トークンの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="a2594-140">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="a2594-141">は、サービスレベルまたはセキュリティトークンハンドラーコレクションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="a2594-141">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="a2594-142">任意。</span><span class="sxs-lookup"><span data-stu-id="a2594-142">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2594-143">親要素</span><span class="sxs-lookup"><span data-stu-id="a2594-143">Parent Elements</span></span>  
  
|<span data-ttu-id="a2594-144">要素</span><span class="sxs-lookup"><span data-stu-id="a2594-144">Element</span></span>|<span data-ttu-id="a2594-145">説明</span><span class="sxs-lookup"><span data-stu-id="a2594-145">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="a2594-146">エンドポイントに登録されているセキュリティトークンハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2594-146">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2594-147">解説</span><span class="sxs-lookup"><span data-stu-id="a2594-147">Remarks</span></span>  

 <span data-ttu-id="a2594-148">このセクションでは、オブジェクトのプロパティ値を提供 <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> します。</span><span class="sxs-lookup"><span data-stu-id="a2594-148">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="a2594-149">このセクションで構成した設定は、サービスで構成されている設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="a2594-149">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="a2594-150">これらの設定の一部は、ハンドラーがセキュリティトークンハンドラーコレクションに追加されたときに指定される設定によってオーバーライドされることがあります。</span><span class="sxs-lookup"><span data-stu-id="a2594-150">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2594-151">例</span><span class="sxs-lookup"><span data-stu-id="a2594-151">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```

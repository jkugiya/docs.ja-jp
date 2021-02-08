---
description: '詳細情報: <cookieHandler>'
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 036646ca5c8aaedebba9466ecb8c9232e87a773d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786578"
---
# \<cookieHandler>

<span data-ttu-id="2bb23-102"><xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) が cookie の読み取りと書き込みに使用するを構成します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-102">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="2bb23-103">構文</span><span class="sxs-lookup"><span data-stu-id="2bb23-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bb23-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2bb23-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2bb23-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bb23-106">属性</span><span class="sxs-lookup"><span data-stu-id="2bb23-106">Attributes</span></span>  
  
|<span data-ttu-id="2bb23-107">属性</span><span class="sxs-lookup"><span data-stu-id="2bb23-107">Attribute</span></span>|<span data-ttu-id="2bb23-108">説明</span><span class="sxs-lookup"><span data-stu-id="2bb23-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2bb23-109">name</span><span class="sxs-lookup"><span data-stu-id="2bb23-109">name</span></span>|<span data-ttu-id="2bb23-110">書き込まれたすべてのクッキーの基本名を指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-110">Specifies the base name for any cookies written.</span></span> <span data-ttu-id="2bb23-111">既定値は "FedAuth" です。</span><span class="sxs-lookup"><span data-stu-id="2bb23-111">The default is "FedAuth".</span></span>|  
|<span data-ttu-id="2bb23-112">path</span><span class="sxs-lookup"><span data-stu-id="2bb23-112">path</span></span>|<span data-ttu-id="2bb23-113">書き込まれたすべてのクッキーのパス値を指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-113">Specifies the path value for any cookies written.</span></span> <span data-ttu-id="2bb23-114">既定値は "HttpRuntime. AppDomainAppVirtualPath" です。</span><span class="sxs-lookup"><span data-stu-id="2bb23-114">The default is "HttpRuntime.AppDomainAppVirtualPath".</span></span>|  
|<span data-ttu-id="2bb23-115">mode</span><span class="sxs-lookup"><span data-stu-id="2bb23-115">mode</span></span>|<span data-ttu-id="2bb23-116"><xref:System.IdentityModel.Services.CookieHandlerMode>SAM によって使用されるクッキーハンドラーの種類を指定する値の1つ。</span><span class="sxs-lookup"><span data-stu-id="2bb23-116">One of the <xref:System.IdentityModel.Services.CookieHandlerMode> values that specifies the kind of cookie handler used by the SAM.</span></span> <span data-ttu-id="2bb23-117">次の値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-117">The following values may be used:</span></span><br /><br /> <span data-ttu-id="2bb23-118">-"Default"-"Chunked" と同じです。</span><span class="sxs-lookup"><span data-stu-id="2bb23-118">-   "Default" — The same as "Chunked".</span></span><br /><span data-ttu-id="2bb23-119">-"Chunked" —クラスのインスタンスを使用 <xref:System.IdentityModel.Services.ChunkedCookieHandler> します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-119">-   "Chunked" — Uses an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class.</span></span> <span data-ttu-id="2bb23-120">この cookie ハンドラーによって、個々の cookie が設定された最大サイズを超えないようにします。</span><span class="sxs-lookup"><span data-stu-id="2bb23-120">This cookie handler ensures that individual cookies do not exceed a set maximum size.</span></span> <span data-ttu-id="2bb23-121">これを実現するには、1つの論理クッキーをネットワーク上の多数の cookie に "チャンキング" します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-121">It accomplishes this by potentially "chunking" one logical cookie into a number of cookies on-the-wire.</span></span><br /><span data-ttu-id="2bb23-122">-"Custom" —は、から派生したカスタムクラスのインスタンスを使用 <xref:System.IdentityModel.Services.CookieHandler> します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-122">-   "Custom" — Uses an instance of a custom class derived from <xref:System.IdentityModel.Services.CookieHandler>.</span></span> <span data-ttu-id="2bb23-123">派生クラスは、子要素によって参照され `<customCookieHandler>` ます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-123">The derived class is referenced by the `<customCookieHandler>` child element.</span></span><br /><br /> <span data-ttu-id="2bb23-124">既定値は "Default" です。</span><span class="sxs-lookup"><span data-stu-id="2bb23-124">The default is "Default".</span></span>|  
|<span data-ttu-id="2bb23-125">persistentSessionLifetime</span><span class="sxs-lookup"><span data-stu-id="2bb23-125">persistentSessionLifetime</span></span>|<span data-ttu-id="2bb23-126">永続的なセッションの有効期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-126">Specifies the lifetime of persistent sessions.</span></span> <span data-ttu-id="2bb23-127">ゼロの場合は、一時的なセッションが常に使用されます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-127">If zero, transient sessions are always used.</span></span> <span data-ttu-id="2bb23-128">既定値は "0:0:0" で、一時的なセッションを指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-128">The default value is "0:0:0", which specifies a transient session.</span></span> <span data-ttu-id="2bb23-129">最大値は "365:0:0" で、これは365日のセッションを指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-129">The maximum value is "365:0:0", which specifies a session of 365 days.</span></span> <span data-ttu-id="2bb23-130">値は、次の制限に従って指定する必要があります。つまり、左端の値には日を指定し、中央の値 `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />` (存在する場合) は時間を指定し、右端の値 (存在する場合) は分を指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-130">The value should be specified according to the following restriction: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, where the leftmost value specifies days, the middle value (if present) specifies hours, and the rightmost value (if present) specifies minutes.</span></span>|  
|<span data-ttu-id="2bb23-131">requireSsl</span><span class="sxs-lookup"><span data-stu-id="2bb23-131">requireSsl</span></span>|<span data-ttu-id="2bb23-132">書き込まれたすべてのクッキーに対して "Secure" フラグを出力するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-132">Specifies whether the "Secure" flag is emitted for any cookies written.</span></span> <span data-ttu-id="2bb23-133">この値が設定されている場合、サインインセッションの cookie は HTTPS 経由でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-133">If this value is set, the sign-in session cookies will only be available over HTTPS.</span></span> <span data-ttu-id="2bb23-134">既定値は "true" です。</span><span class="sxs-lookup"><span data-stu-id="2bb23-134">The default is "true".</span></span>|  
|<span data-ttu-id="2bb23-135">hideFromScript</span><span class="sxs-lookup"><span data-stu-id="2bb23-135">hideFromScript</span></span>|<span data-ttu-id="2bb23-136">書き込まれたクッキーに対して "HttpOnly" フラグを出力するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-136">Controls whether the "HttpOnly" flag is emitted for any cookies written.</span></span> <span data-ttu-id="2bb23-137">一部の web ブラウザーでは、クライアント側のスクリプトに cookie 値へのアクセスを保持することで、このフラグが適用されます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-137">Certain web browsers honor this flag by keeping client-side script from accessing the cookie value.</span></span> <span data-ttu-id="2bb23-138">既定値は "true" です。</span><span class="sxs-lookup"><span data-stu-id="2bb23-138">The default is "true".</span></span>|  
|<span data-ttu-id="2bb23-139">domain</span><span class="sxs-lookup"><span data-stu-id="2bb23-139">domain</span></span>|<span data-ttu-id="2bb23-140">書き込まれたすべてのクッキーのドメイン値。</span><span class="sxs-lookup"><span data-stu-id="2bb23-140">The domain value for any cookies written.</span></span> <span data-ttu-id="2bb23-141">既定値は "" です。</span><span class="sxs-lookup"><span data-stu-id="2bb23-141">The default is "".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bb23-142">子要素</span><span class="sxs-lookup"><span data-stu-id="2bb23-142">Child Elements</span></span>  
  
|<span data-ttu-id="2bb23-143">要素</span><span class="sxs-lookup"><span data-stu-id="2bb23-143">Element</span></span>|<span data-ttu-id="2bb23-144">説明</span><span class="sxs-lookup"><span data-stu-id="2bb23-144">Description</span></span>|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|<span data-ttu-id="2bb23-145">を構成 <xref:System.IdentityModel.Services.ChunkedCookieHandler> します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-145">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="2bb23-146">この要素は `mode` 、要素の属性 `<cookieHandler>` が "Default" または "Chunked" の場合にのみ存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2bb23-146">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>|  
|[\<customCookieHandler>](customcookiehandler.md)|<span data-ttu-id="2bb23-147">カスタムクッキーハンドラーの種類を設定します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-147">Sets the custom cookie handler type.</span></span> <span data-ttu-id="2bb23-148">`mode`要素の属性 `<cookieHandler>` が "Custom" の場合、この要素は存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bb23-148">This element must be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="2bb23-149">属性の他の値には存在できません `mode` 。</span><span class="sxs-lookup"><span data-stu-id="2bb23-149">It cannot be present for any other values of the `mode` attribute.</span></span> <span data-ttu-id="2bb23-150">カスタム型は、クラスから派生する必要があり <xref:System.IdentityModel.Services.CookieHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-150">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2bb23-151">親要素</span><span class="sxs-lookup"><span data-stu-id="2bb23-151">Parent Elements</span></span>  
  
|<span data-ttu-id="2bb23-152">要素</span><span class="sxs-lookup"><span data-stu-id="2bb23-152">Element</span></span>|<span data-ttu-id="2bb23-153">説明</span><span class="sxs-lookup"><span data-stu-id="2bb23-153">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="2bb23-154"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfam) と (SAM) を構成する設定が含まれてい <xref:System.IdentityModel.Services.SessionAuthenticationModule> ます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-154">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bb23-155">解説</span><span class="sxs-lookup"><span data-stu-id="2bb23-155">Remarks</span></span>  

 <span data-ttu-id="2bb23-156"><xref:System.IdentityModel.Services.CookieHandler>は、HTTP プロトコルレベルでの未加工の cookie の読み取りと書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="2bb23-156">The <xref:System.IdentityModel.Services.CookieHandler> is responsible for reading and writing raw cookies at the HTTP protocol level.</span></span> <span data-ttu-id="2bb23-157"><xref:System.IdentityModel.Services.ChunkedCookieHandler>またはクラスから派生したカスタム cookie ハンドラーを構成でき <xref:System.IdentityModel.Services.CookieHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-157">You can configure either a <xref:System.IdentityModel.Services.ChunkedCookieHandler> or a custom cookie handler derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="2bb23-158">チャンク cookie ハンドラーを構成するには、mode 属性を "Chunked" または "Default" に設定します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-158">To configure a chunked cookie handler, set the mode attribute to "Chunked" or "Default".</span></span> <span data-ttu-id="2bb23-159">既定のチャンクサイズは2000バイトですが、必要に応じて、子要素を含めることによって別のチャンクサイズを指定することもでき `<chunkedCookieHandler>` ます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-159">The default chunk size is 2000 bytes, but you may optionally specify a different chunk size by including a `<chunkedCookieHandler>` child element.</span></span>  
  
 <span data-ttu-id="2bb23-160">カスタム cookie ハンドラーを構成するには、mode 属性を "Custom" に設定します。</span><span class="sxs-lookup"><span data-stu-id="2bb23-160">To configure a custom cookie handler, set the mode attribute to "Custom".</span></span> <span data-ttu-id="2bb23-161">また、 `<customCookieHandler>` カスタムハンドラーの型を参照する子要素も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bb23-161">You must also specify a `<customCookieHandler>` child element that references the type of your custom handler.</span></span>  
  
 <span data-ttu-id="2bb23-162">`<cookieHandler>`要素は、クラスによって表され <xref:System.IdentityModel.Services.CookieHandlerElement> ます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-162">The `<cookieHandler>` element is represented by the <xref:System.IdentityModel.Services.CookieHandlerElement> class.</span></span> <span data-ttu-id="2bb23-163">構成で指定されたクッキーハンドラーは、プロパティに設定されている <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> オブジェクトのプロパティから取得でき <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-163">The cookie handler that was specified in configuration is available from the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> property of the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bb23-164">例</span><span class="sxs-lookup"><span data-stu-id="2bb23-164">Example</span></span>  

 <span data-ttu-id="2bb23-165">次の XML は、要素を示して `<cookieHandler>` います。</span><span class="sxs-lookup"><span data-stu-id="2bb23-165">The following XML shows a `<cookieHandler>` element.</span></span> <span data-ttu-id="2bb23-166">この例では、 `mode` 属性が指定されていないため、既定の cookie ハンドラーが SAM によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-166">In this example, because the `mode` attribute is not specified, the default cookie handler will be used by the SAM.</span></span> <span data-ttu-id="2bb23-167">これはクラスのインスタンスです <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="2bb23-167">This is an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class.</span></span> <span data-ttu-id="2bb23-168">`<chunkedCookieHandler>`子要素が指定されていないため、既定のチャンクサイズが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2bb23-168">Because the `<chunkedCookieHandler>` child element is not specified, the default chunk size will be used.</span></span> <span data-ttu-id="2bb23-169">属性が設定されているため、HTTPS は必要ありません `requireSsl` `false` 。</span><span class="sxs-lookup"><span data-stu-id="2bb23-169">HTTPS will not be required because the `requireSsl` attribute is set `false`.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2bb23-170">この例では、セッション cookie を書き込むために HTTPS は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2bb23-170">In this example, HTTPS is not required to write session cookies.</span></span> <span data-ttu-id="2bb23-171">これは、 `requireSsl` 要素の属性 `<cookieHandler>` がに設定されているためです `false` 。</span><span class="sxs-lookup"><span data-stu-id="2bb23-171">This is because the `requireSsl` attribute on the `<cookieHandler>` element is set to `false`.</span></span> <span data-ttu-id="2bb23-172">ほとんどの運用環境では、セキュリティ上のリスクが生じる可能性があるため、この設定は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="2bb23-172">This setting is not recommended for most production environments as it may present a security risk.</span></span>  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bb23-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bb23-173">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>

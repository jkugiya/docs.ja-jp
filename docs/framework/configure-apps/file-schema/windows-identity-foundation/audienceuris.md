---
description: '詳細情報: <audienceUris>'
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 98b411e73d4b9941e65daaf5d1d63285cdc90fd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681852"
---
# \<audienceUris>

<span data-ttu-id="0acdb-102">証明書利用者 (RP) の許容される識別子である Uri のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="0acdb-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="0acdb-103">トークンは、許可されている対象 URI の 1 つに範囲が設定されていない限り、受け入れられません。</span><span class="sxs-lookup"><span data-stu-id="0acdb-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="0acdb-104">構文</span><span class="sxs-lookup"><span data-stu-id="0acdb-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0acdb-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0acdb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0acdb-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0acdb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0acdb-107">属性</span><span class="sxs-lookup"><span data-stu-id="0acdb-107">Attributes</span></span>  
  
|<span data-ttu-id="0acdb-108">属性</span><span class="sxs-lookup"><span data-stu-id="0acdb-108">Attribute</span></span>|<span data-ttu-id="0acdb-109">説明</span><span class="sxs-lookup"><span data-stu-id="0acdb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0acdb-110">mode</span><span class="sxs-lookup"><span data-stu-id="0acdb-110">mode</span></span>|<span data-ttu-id="0acdb-111"><xref:System.IdentityModel.Selectors.AudienceUriMode>対象ユーザーの制限を受信トークンに適用する必要があるかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="0acdb-111">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="0acdb-112">指定できる値は、"Always"、"Never"、および "BearerKeyOnly" です。</span><span class="sxs-lookup"><span data-stu-id="0acdb-112">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="0acdb-113">既定値は "Always" です。</span><span class="sxs-lookup"><span data-stu-id="0acdb-113">The default is "Always".</span></span> <span data-ttu-id="0acdb-114">任意。</span><span class="sxs-lookup"><span data-stu-id="0acdb-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0acdb-115">子要素</span><span class="sxs-lookup"><span data-stu-id="0acdb-115">Child Elements</span></span>  
  
|<span data-ttu-id="0acdb-116">要素</span><span class="sxs-lookup"><span data-stu-id="0acdb-116">Element</span></span>|<span data-ttu-id="0acdb-117">説明</span><span class="sxs-lookup"><span data-stu-id="0acdb-117">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="0acdb-118">属性によって指定された URI を `value` audienceUris コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="0acdb-118">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="0acdb-119">`value` 属性は必須です。</span><span class="sxs-lookup"><span data-stu-id="0acdb-119">The `value` attribute is required.</span></span> <span data-ttu-id="0acdb-120">URI では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="0acdb-120">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="0acdb-121">AudienceUris コレクションをクリアします。</span><span class="sxs-lookup"><span data-stu-id="0acdb-121">Clears the audienceUris collection.</span></span> <span data-ttu-id="0acdb-122">すべての識別子はコレクションから削除されます。</span><span class="sxs-lookup"><span data-stu-id="0acdb-122">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="0acdb-123">属性によって指定された URI を `value` audienceUris コレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="0acdb-123">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="0acdb-124">`value` 属性は必須です。</span><span class="sxs-lookup"><span data-stu-id="0acdb-124">The `value` attribute is required.</span></span> <span data-ttu-id="0acdb-125">URI では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="0acdb-125">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0acdb-126">親要素</span><span class="sxs-lookup"><span data-stu-id="0acdb-126">Parent Elements</span></span>  
  
|<span data-ttu-id="0acdb-127">要素</span><span class="sxs-lookup"><span data-stu-id="0acdb-127">Element</span></span>|<span data-ttu-id="0acdb-128">説明</span><span class="sxs-lookup"><span data-stu-id="0acdb-128">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="0acdb-129">セキュリティトークンハンドラーのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="0acdb-129">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0acdb-130">解説</span><span class="sxs-lookup"><span data-stu-id="0acdb-130">Remarks</span></span>  

 <span data-ttu-id="0acdb-131">既定では、コレクションは空です。 `<add>`コレクションを `<clear>` 変更するには、、、およびの各要素を使用し `<remove>` ます。</span><span class="sxs-lookup"><span data-stu-id="0acdb-131">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="0acdb-132"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> オブジェクトと <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> オブジェクトは、AUDIENCE uri コレクションの値を使用して、オブジェクトで許可されている対象ユーザー uri 制限を構成し <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> ます。</span><span class="sxs-lookup"><span data-stu-id="0acdb-132"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="0acdb-133">`<audienceUris>`要素は、クラスによって表され <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> ます。</span><span class="sxs-lookup"><span data-stu-id="0acdb-133">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="0acdb-134">コレクションに追加された個々の URI は、クラスによって表され <xref:System.IdentityModel.Configuration.AudienceUriElement> ます。</span><span class="sxs-lookup"><span data-stu-id="0acdb-134">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0acdb-135">要素の `<audienceUris>` 子要素としての要素の使用は [\<identityConfiguration>](identityconfiguration.md) 非推奨とされましたが、旧バージョンとの互換性のために引き続きサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0acdb-135">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="0acdb-136">要素の設定は、要素の設定 `<securityTokenHandlerConfiguration>` よりも優先さ `<identityConfiguration>` れます。</span><span class="sxs-lookup"><span data-stu-id="0acdb-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0acdb-137">例</span><span class="sxs-lookup"><span data-stu-id="0acdb-137">Example</span></span>  

 <span data-ttu-id="0acdb-138">次の XML は、アプリケーションに対して許容される対象ユーザーの Uri を構成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0acdb-138">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="0acdb-139">この例では、単一の URI を構成します。</span><span class="sxs-lookup"><span data-stu-id="0acdb-139">This example configures a single URI.</span></span> <span data-ttu-id="0acdb-140">この URI にスコープが設定されているトークンは受け入れられ、それ以外はすべて拒否されます。</span><span class="sxs-lookup"><span data-stu-id="0acdb-140">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```

---
description: '詳細情報: <securityTokenHandlers>'
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 14937f6763644f9b7f43c0f7be71ea2352b21402
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782027"
---
# \<securityTokenHandlers>

<span data-ttu-id="a85a9-102">エンドポイントに登録されているセキュリティトークンハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a85a9-102">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="a85a9-103">構文</span><span class="sxs-lookup"><span data-stu-id="a85a9-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a85a9-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a85a9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a85a9-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a85a9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a85a9-106">属性</span><span class="sxs-lookup"><span data-stu-id="a85a9-106">Attributes</span></span>  
  
|<span data-ttu-id="a85a9-107">属性</span><span class="sxs-lookup"><span data-stu-id="a85a9-107">Attribute</span></span>|<span data-ttu-id="a85a9-108">説明</span><span class="sxs-lookup"><span data-stu-id="a85a9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a85a9-109">name</span><span class="sxs-lookup"><span data-stu-id="a85a9-109">name</span></span>|<span data-ttu-id="a85a9-110">トークンハンドラーコレクションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a85a9-110">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="a85a9-111">フレームワークによって認識される値は、"ActAs" と "OnBehalfOf" だけです。</span><span class="sxs-lookup"><span data-stu-id="a85a9-111">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="a85a9-112">これらのいずれかの名前でトークンハンドラーコレクションが指定されている場合、ActAs または OnBehalfOf トークンをそれぞれ処理するときにコレクションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a85a9-112">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a85a9-113">子要素</span><span class="sxs-lookup"><span data-stu-id="a85a9-113">Child Elements</span></span>  
  
|<span data-ttu-id="a85a9-114">要素</span><span class="sxs-lookup"><span data-stu-id="a85a9-114">Element</span></span>|<span data-ttu-id="a85a9-115">説明</span><span class="sxs-lookup"><span data-stu-id="a85a9-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="a85a9-116">トークンハンドラーコレクションにセキュリティトークンハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="a85a9-116">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="a85a9-117">すべてのセキュリティトークンハンドラーをトークンハンドラーコレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="a85a9-117">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="a85a9-118">トークンハンドラーコレクションからセキュリティトークンハンドラーを削除します。</span><span class="sxs-lookup"><span data-stu-id="a85a9-118">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="a85a9-119">トークンハンドラーのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="a85a9-119">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a85a9-120">親要素</span><span class="sxs-lookup"><span data-stu-id="a85a9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a85a9-121">要素</span><span class="sxs-lookup"><span data-stu-id="a85a9-121">Element</span></span>|<span data-ttu-id="a85a9-122">説明</span><span class="sxs-lookup"><span data-stu-id="a85a9-122">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="a85a9-123">サービスレベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="a85a9-123">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a85a9-124">解説</span><span class="sxs-lookup"><span data-stu-id="a85a9-124">Remarks</span></span>  

 <span data-ttu-id="a85a9-125">サービス構成では、セキュリティトークンハンドラーの1つ以上の名前付きコレクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a85a9-125">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="a85a9-126">属性を使用して、コレクションの名前を指定でき `name` ます。</span><span class="sxs-lookup"><span data-stu-id="a85a9-126">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="a85a9-127">フレームワークによって処理される名前は、"ActAs" と "OnBehalfOf" だけです。</span><span class="sxs-lookup"><span data-stu-id="a85a9-127">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="a85a9-128">これらのコレクションにハンドラーが存在する場合は、トークンの処理時に既定のハンドラーではなく、Security Token Service (STS) によって使用され `ActAs` `OnBehalfOf` ます。</span><span class="sxs-lookup"><span data-stu-id="a85a9-128">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="a85a9-129">既定では、コレクションには、、、、、、 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 、および <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> の各ハンドラー型が設定されます。</span><span class="sxs-lookup"><span data-stu-id="a85a9-129">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="a85a9-130">コレクションは、、、およびの各要素を使用して変更でき `<add>` `<remove>` `<clear>` ます。</span><span class="sxs-lookup"><span data-stu-id="a85a9-130">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="a85a9-131">コレクション内に存在する特定の種類のハンドラーが1つだけであることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a85a9-131">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="a85a9-132">たとえば、クラスからハンドラーを派生させる場合、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ハンドラーまたはが <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 1 つのコレクションで構成されていることがありますが、両方を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="a85a9-132">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="a85a9-133">`<securityTokenHandlerConfiguration>`コレクション内のハンドラーの構成設定を指定するには、要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="a85a9-133">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="a85a9-134">この要素によって指定された設定は、サービスで指定された設定よりも要素を介してオーバーライドされ [\<identityConfiguration>](identityconfiguration.md) ます。</span><span class="sxs-lookup"><span data-stu-id="a85a9-134">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="a85a9-135">いくつかの組み込みハンドラー型を含む一部のハンドラーは、要素の子要素を通じて追加の構成をサポートでき `<add>` ます。</span><span class="sxs-lookup"><span data-stu-id="a85a9-135">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="a85a9-136">ハンドラーに指定された設定は、コレクションまたはサービスで指定された同等の設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="a85a9-136">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>

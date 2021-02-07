---
description: '詳細情報: <serviceTokenResolver>'
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: ab24c92eee43324365adb3bb3a64c8a765017a53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698298"
---
# \<serviceTokenResolver>

<span data-ttu-id="af95d-102">トークンハンドラーコレクションのハンドラーによって使用されるサービストークンリゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="af95d-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="af95d-103">サービストークンリゾルバーは、受信トークンとメッセージの暗号化トークンを解決するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="af95d-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="af95d-104">構文</span><span class="sxs-lookup"><span data-stu-id="af95d-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af95d-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="af95d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="af95d-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="af95d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af95d-107">属性</span><span class="sxs-lookup"><span data-stu-id="af95d-107">Attributes</span></span>  
  
|<span data-ttu-id="af95d-108">属性</span><span class="sxs-lookup"><span data-stu-id="af95d-108">Attribute</span></span>|<span data-ttu-id="af95d-109">説明</span><span class="sxs-lookup"><span data-stu-id="af95d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af95d-110">type</span><span class="sxs-lookup"><span data-stu-id="af95d-110">type</span></span>|<span data-ttu-id="af95d-111">サービストークンリゾルバーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="af95d-111">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="af95d-112"><xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラスから派生した型または型 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="af95d-112">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="af95d-113">属性を指定する方法の詳細については `type` 、「[カスタム型参照]」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af95d-113">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="af95d-114">必須。</span><span class="sxs-lookup"><span data-stu-id="af95d-114">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af95d-115">子要素</span><span class="sxs-lookup"><span data-stu-id="af95d-115">Child Elements</span></span>  

 <span data-ttu-id="af95d-116">なし</span><span class="sxs-lookup"><span data-stu-id="af95d-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af95d-117">親要素</span><span class="sxs-lookup"><span data-stu-id="af95d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="af95d-118">要素</span><span class="sxs-lookup"><span data-stu-id="af95d-118">Element</span></span>|<span data-ttu-id="af95d-119">説明</span><span class="sxs-lookup"><span data-stu-id="af95d-119">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="af95d-120">セキュリティトークンハンドラーのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="af95d-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af95d-121">解説</span><span class="sxs-lookup"><span data-stu-id="af95d-121">Remarks</span></span>  

 <span data-ttu-id="af95d-122">サービストークンリゾルバーを使用して、受信トークンとメッセージの暗号化トークンを解決できます。</span><span class="sxs-lookup"><span data-stu-id="af95d-122">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="af95d-123">これは、受信トークンの暗号化を解除するために使用する必要があるキーを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="af95d-123">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="af95d-124">属性を指定する必要があり `type` ます。</span><span class="sxs-lookup"><span data-stu-id="af95d-124">You must specify the `type` attribute.</span></span> <span data-ttu-id="af95d-125">指定できる型は、 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> またはクラスから派生したカスタム型のいずれか <xref:System.IdentityModel.Selectors.SecurityTokenResolver> です。</span><span class="sxs-lookup"><span data-stu-id="af95d-125">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="af95d-126">一部のトークンハンドラーでは、構成でサービストークンリゾルバーの設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="af95d-126">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="af95d-127">個々のトークンハンドラーの設定は、セキュリティトークンハンドラーコレクションで指定された設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="af95d-127">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af95d-128">要素 `<serviceTokenResolver>` の子要素としての指定 [\<identityConfiguration>](identityconfiguration.md) は非推奨とされましたが、旧バージョンとの互換性のために引き続きサポートされています。</span><span class="sxs-lookup"><span data-stu-id="af95d-128">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="af95d-129">要素の設定は、要素の設定 `<securityTokenHandlerConfiguration>` よりも優先さ `<identityConfiguration>` れます。</span><span class="sxs-lookup"><span data-stu-id="af95d-129">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af95d-130">例</span><span class="sxs-lookup"><span data-stu-id="af95d-130">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```

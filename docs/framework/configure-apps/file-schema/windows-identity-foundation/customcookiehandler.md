---
description: '詳細情報: <customCookieHandler>'
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 6b433769c429ed4149efb324d7c4b216d6042705
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664081"
---
# \<customCookieHandler>

<span data-ttu-id="17dd5-102">カスタムクッキーハンドラーの種類を設定します。</span><span class="sxs-lookup"><span data-stu-id="17dd5-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="17dd5-103">この要素は `mode` 、要素の属性が "Custom" の場合にのみ存在する可能性があり `<cookieHandler>` ます。</span><span class="sxs-lookup"><span data-stu-id="17dd5-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="17dd5-104">カスタム型は、クラスから派生する必要があり <xref:System.IdentityModel.Services.CookieHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="17dd5-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="17dd5-105">構文</span><span class="sxs-lookup"><span data-stu-id="17dd5-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17dd5-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="17dd5-106">Attributes and Elements</span></span>  

 <span data-ttu-id="17dd5-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="17dd5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17dd5-108">属性</span><span class="sxs-lookup"><span data-stu-id="17dd5-108">Attributes</span></span>  
  
|<span data-ttu-id="17dd5-109">属性</span><span class="sxs-lookup"><span data-stu-id="17dd5-109">Attribute</span></span>|<span data-ttu-id="17dd5-110">説明</span><span class="sxs-lookup"><span data-stu-id="17dd5-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17dd5-111">type</span><span class="sxs-lookup"><span data-stu-id="17dd5-111">type</span></span>|<span data-ttu-id="17dd5-112">クラスから派生するカスタム型を指定し <xref:System.IdentityModel.Services.CookieHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="17dd5-112">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="17dd5-113">属性を指定する方法の詳細については `type` 、「 [カスタム型参照](../windows-workflow-foundation/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17dd5-113">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17dd5-114">子要素</span><span class="sxs-lookup"><span data-stu-id="17dd5-114">Child Elements</span></span>  

 <span data-ttu-id="17dd5-115">なし</span><span class="sxs-lookup"><span data-stu-id="17dd5-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17dd5-116">親要素</span><span class="sxs-lookup"><span data-stu-id="17dd5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="17dd5-117">要素</span><span class="sxs-lookup"><span data-stu-id="17dd5-117">Element</span></span>|<span data-ttu-id="17dd5-118">説明</span><span class="sxs-lookup"><span data-stu-id="17dd5-118">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="17dd5-119"><xref:System.IdentityModel.Services.CookieHandler>が <xref:System.IdentityModel.Services.SessionAuthenticationModule> cookie の読み取りと書き込みに使用するを構成します。</span><span class="sxs-lookup"><span data-stu-id="17dd5-119">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17dd5-120">解説</span><span class="sxs-lookup"><span data-stu-id="17dd5-120">Remarks</span></span>  

 <span data-ttu-id="17dd5-121">要素の属性を "Custom" に設定してカスタム cookie ハンドラーを指定する場合は、 `mode` `<cookieHandler>` `<customCookieHandler>` クッキーハンドラーの型を参照する子要素を含めることによって、カスタム cookie ハンドラーの型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17dd5-121">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="17dd5-122">`mode`属性が "Chunked" または "Default" に設定されている場合、この要素を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="17dd5-122">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="17dd5-123">カスタムクッキーハンドラーは、クラスから派生する必要があり <xref:System.IdentityModel.Services.CookieHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="17dd5-123">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="17dd5-124">`<customCookieHandler>`要素は、クラスによって表され <xref:System.IdentityModel.Configuration.CustomTypeElement> ます。</span><span class="sxs-lookup"><span data-stu-id="17dd5-124">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17dd5-125">例</span><span class="sxs-lookup"><span data-stu-id="17dd5-125">Example</span></span>  

 <span data-ttu-id="17dd5-126">次の例では、型のカスタム cookie ハンドラーを使用するように SAM を構成し `MyNamespace.MyCustomCookieHandler` ます。</span><span class="sxs-lookup"><span data-stu-id="17dd5-126">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="17dd5-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="17dd5-127">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>

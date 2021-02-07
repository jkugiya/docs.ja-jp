---
description: '詳細情報: <claimsAuthenticationManager>'
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 5a94861d6b2684b9f66c7d5e14f72aa419a0c66f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664250"
---
# \<claimsAuthenticationManager>

<span data-ttu-id="d3196-102">入力方向の要求に対して要求認証マネージャーを登録します。</span><span class="sxs-lookup"><span data-stu-id="d3196-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="d3196-103">構文</span><span class="sxs-lookup"><span data-stu-id="d3196-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3196-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d3196-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d3196-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3196-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3196-106">属性</span><span class="sxs-lookup"><span data-stu-id="d3196-106">Attributes</span></span>  
  
|<span data-ttu-id="d3196-107">属性</span><span class="sxs-lookup"><span data-stu-id="d3196-107">Attribute</span></span>|<span data-ttu-id="d3196-108">説明</span><span class="sxs-lookup"><span data-stu-id="d3196-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3196-109">type</span><span class="sxs-lookup"><span data-stu-id="d3196-109">type</span></span>|<span data-ttu-id="d3196-110">クラスから派生するカスタム型を指定し <xref:System.Security.Claims.ClaimsAuthenticationManager> ます。</span><span class="sxs-lookup"><span data-stu-id="d3196-110">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="d3196-111">属性を指定する方法の詳細については `type` 、「[カスタム型参照]」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3196-111">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3196-112">子要素</span><span class="sxs-lookup"><span data-stu-id="d3196-112">Child Elements</span></span>  

 <span data-ttu-id="d3196-113">属性が存在しない場合、 `type` または属性がクラスを参照している場合、 `type` 要素は <xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthenticationManager>` 子要素を受け取りません。ただし、から派生したクラス <xref:System.Security.Claims.ClaimsAuthenticationManager> は子構成要素を定義できます。</span><span class="sxs-lookup"><span data-stu-id="d3196-113">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3196-114">親要素</span><span class="sxs-lookup"><span data-stu-id="d3196-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d3196-115">要素</span><span class="sxs-lookup"><span data-stu-id="d3196-115">Element</span></span>|<span data-ttu-id="d3196-116">説明</span><span class="sxs-lookup"><span data-stu-id="d3196-116">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="d3196-117">サービスレベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="d3196-117">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3196-118">解説</span><span class="sxs-lookup"><span data-stu-id="d3196-118">Remarks</span></span>  

 <span data-ttu-id="d3196-119">クラスによって提供される既定の動作では、 <xref:System.Security.Claims.ClaimsAuthenticationManager> 入力方向の要求がエコーされます。</span><span class="sxs-lookup"><span data-stu-id="d3196-119">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="d3196-120">属性が指定されていない場合、 `type` または属性でクラスが指定されている場合、 `type` <xref:System.Security.Claims.ClaimsAuthenticationManager> 要素は `<claimsAuthenticationManager>` 子要素を受け取りません。</span><span class="sxs-lookup"><span data-stu-id="d3196-120">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="d3196-121">属性を指定して、 `type` クラスから派生した型を登録し、 <xref:System.Security.Claims.ClaimsAuthenticationManager> カスタム動作を実装することができます。</span><span class="sxs-lookup"><span data-stu-id="d3196-121">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="d3196-122">派生クラスでは、要素の子要素を使用した構成をサポートできます。これを行う `<claimsAuthenticationManager>` には、メソッドをオーバーライドして <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> これらの要素を処理します。</span><span class="sxs-lookup"><span data-stu-id="d3196-122">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="d3196-123">子要素に対して定義されているスキーマは、クラスのデザイナーによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="d3196-123">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="d3196-124">要素は、 `<claimsAuthenticationManager>` プロパティを設定し <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="d3196-124">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3196-125">例</span><span class="sxs-lookup"><span data-stu-id="d3196-125">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```

---
description: '詳細については、次を参照してください: <remove> of <claimTypeRequirements> 要素'
title: <remove><claimTypeRequirements>要素の
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 2ec917d27966954382e5b091fd538168b48b5ffb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786903"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="f45fb-103">\<remove>\<claimTypeRequirements>要素の</span><span class="sxs-lookup"><span data-stu-id="f45fb-103">\<remove> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="f45fb-104">フェデレーション資格情報から削除するクレームの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="f45fb-104">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="f45fb-105">構文</span><span class="sxs-lookup"><span data-stu-id="f45fb-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f45fb-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f45fb-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f45fb-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f45fb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f45fb-108">属性</span><span class="sxs-lookup"><span data-stu-id="f45fb-108">Attributes</span></span>  
  
|<span data-ttu-id="f45fb-109">属性</span><span class="sxs-lookup"><span data-stu-id="f45fb-109">Attribute</span></span>|<span data-ttu-id="f45fb-110">説明</span><span class="sxs-lookup"><span data-stu-id="f45fb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f45fb-111">claimType</span><span class="sxs-lookup"><span data-stu-id="f45fb-111">claimType</span></span>|<span data-ttu-id="f45fb-112">削除するクレームの種類を定義する URI。</span><span class="sxs-lookup"><span data-stu-id="f45fb-112">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f45fb-113">子要素</span><span class="sxs-lookup"><span data-stu-id="f45fb-113">Child Elements</span></span>  

 <span data-ttu-id="f45fb-114">なし。</span><span class="sxs-lookup"><span data-stu-id="f45fb-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f45fb-115">親要素</span><span class="sxs-lookup"><span data-stu-id="f45fb-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f45fb-116">要素</span><span class="sxs-lookup"><span data-stu-id="f45fb-116">Element</span></span>|<span data-ttu-id="f45fb-117">説明</span><span class="sxs-lookup"><span data-stu-id="f45fb-117">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="f45fb-118">必須のクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="f45fb-118">Specifies a collection of required claim types.</span></span> <span data-ttu-id="f45fb-119">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="f45fb-119">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="f45fb-120">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="f45fb-120">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="f45fb-121">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f45fb-121">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="f45fb-122">このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="f45fb-122">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f45fb-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f45fb-123">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

---
description: '詳細情報: <claimTypeRequirements> 要素の <clear>'
title: <claimTypeRequirements> 要素の <clear>
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: d25dad5afcec352f040ea4f8c08e5ffa2bc16d19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638887"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="9ed4c-103">\<claimTypeRequirements> 要素の \<clear></span><span class="sxs-lookup"><span data-stu-id="9ed4c-103">\<clear> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="9ed4c-104">すべてのクレームの種類をフェデレーション資格情報から削除するように指定します。</span><span class="sxs-lookup"><span data-stu-id="9ed4c-104">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="9ed4c-105">これにより、コレクションの初期値を確実に空にできます。</span><span class="sxs-lookup"><span data-stu-id="9ed4c-105">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="9ed4c-106">構文</span><span class="sxs-lookup"><span data-stu-id="9ed4c-106">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ed4c-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9ed4c-107">Attributes and Elements</span></span>  

 <span data-ttu-id="9ed4c-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ed4c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ed4c-109">属性</span><span class="sxs-lookup"><span data-stu-id="9ed4c-109">Attributes</span></span>  

 <span data-ttu-id="9ed4c-110">なし。</span><span class="sxs-lookup"><span data-stu-id="9ed4c-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ed4c-111">子要素</span><span class="sxs-lookup"><span data-stu-id="9ed4c-111">Child Elements</span></span>  

 <span data-ttu-id="9ed4c-112">なし。</span><span class="sxs-lookup"><span data-stu-id="9ed4c-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ed4c-113">親要素</span><span class="sxs-lookup"><span data-stu-id="9ed4c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="9ed4c-114">要素</span><span class="sxs-lookup"><span data-stu-id="9ed4c-114">Element</span></span>|<span data-ttu-id="9ed4c-115">説明</span><span class="sxs-lookup"><span data-stu-id="9ed4c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="9ed4c-116">必須のクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ed4c-116">Specifies a collection of required claim types.</span></span> <span data-ttu-id="9ed4c-117">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="9ed4c-117">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="9ed4c-118">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="9ed4c-118">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9ed4c-119">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ed4c-119">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9ed4c-120">このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ed4c-120">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ed4c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ed4c-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

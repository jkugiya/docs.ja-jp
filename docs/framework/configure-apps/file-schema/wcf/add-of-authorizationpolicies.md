---
description: 詳細については <add> 、 <authorizationPolicies>
title: <add> の <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 616f09abfad51f41348b0ffa8557a4fd54492437
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804102"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="4c5a4-103">\<add> の \<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="4c5a4-103">\<add> of \<authorizationPolicies></span></span>

<span data-ttu-id="4c5a4-104">クレームの変換の承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-104">Specifies an authorization policy for claim transformation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="4c5a4-105">構文</span><span class="sxs-lookup"><span data-stu-id="4c5a4-105">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="4c5a4-106">Type</span><span class="sxs-lookup"><span data-stu-id="4c5a4-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c5a4-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4c5a4-107">Attributes and Elements</span></span>  

 <span data-ttu-id="4c5a4-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c5a4-109">属性</span><span class="sxs-lookup"><span data-stu-id="4c5a4-109">Attributes</span></span>  
  
|<span data-ttu-id="4c5a4-110">属性</span><span class="sxs-lookup"><span data-stu-id="4c5a4-110">Attribute</span></span>|<span data-ttu-id="4c5a4-111">説明</span><span class="sxs-lookup"><span data-stu-id="4c5a4-111">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="4c5a4-112">必須の文字列属性。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-112">A required String attribute.</span></span><br /><br /> <span data-ttu-id="4c5a4-113">Windows Communication Foundation (WCF) アクセス制御モデルは、一連の承認ポリシーを型としてプロビジョニングすることをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-113">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="4c5a4-114">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-114">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="4c5a4-115">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-115">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c5a4-116">子要素</span><span class="sxs-lookup"><span data-stu-id="4c5a4-116">Child Elements</span></span>  

 <span data-ttu-id="4c5a4-117">なし。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c5a4-118">親要素</span><span class="sxs-lookup"><span data-stu-id="4c5a4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4c5a4-119">要素</span><span class="sxs-lookup"><span data-stu-id="4c5a4-119">Element</span></span>|<span data-ttu-id="4c5a4-120">説明</span><span class="sxs-lookup"><span data-stu-id="4c5a4-120">Description</span></span>|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|<span data-ttu-id="4c5a4-121">承認ポリシーの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-121">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c5a4-122">解説</span><span class="sxs-lookup"><span data-stu-id="4c5a4-122">Remarks</span></span>  

 <span data-ttu-id="4c5a4-123">各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-123">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="4c5a4-124">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-124">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="4c5a4-125">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-125">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="4c5a4-126">承認ポリシーのしくみの詳細については、「」 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> および「 [承認ポリシー](../../../wcf/samples/authorization-policy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c5a4-126">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5a4-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c5a4-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="4c5a4-128">サービス操作へのアクセスの承認</span><span class="sxs-lookup"><span data-stu-id="4c5a4-128">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="4c5a4-129">方法: サービスで使用するカスタム承認マネージャーを作成する</span><span class="sxs-lookup"><span data-stu-id="4c5a4-129">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="4c5a4-130">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="4c5a4-130">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)

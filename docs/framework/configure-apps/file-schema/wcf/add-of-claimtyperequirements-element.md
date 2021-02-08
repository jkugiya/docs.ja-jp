---
description: '詳細については、次を参照してください: <add> of <claimTypeRequirements> 要素'
title: <add><claimTypeRequirements>要素の
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 7ad93c4e1c2379704b38d3cdc68fddca62b3c057
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804037"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="bb0ec-103">\<add>\<claimTypeRequirements>要素の</span><span class="sxs-lookup"><span data-stu-id="bb0ec-103">\<add> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="bb0ec-104">フェデレーション資格情報に表示されると予想される必須のクレームおよび省略可能なクレームの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-104">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="bb0ec-105">たとえば、サービスは、クレームの種類の特定のセットを処理する必要がある受信資格情報について要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-105">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**
  
## <a name="syntax"></a><span data-ttu-id="bb0ec-106">構文</span><span class="sxs-lookup"><span data-stu-id="bb0ec-106">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb0ec-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bb0ec-107">Attributes and Elements</span></span>  

 <span data-ttu-id="bb0ec-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb0ec-109">属性</span><span class="sxs-lookup"><span data-stu-id="bb0ec-109">Attributes</span></span>  
  
|<span data-ttu-id="bb0ec-110">属性</span><span class="sxs-lookup"><span data-stu-id="bb0ec-110">Attribute</span></span>|<span data-ttu-id="bb0ec-111">説明</span><span class="sxs-lookup"><span data-stu-id="bb0ec-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bb0ec-112">claimType</span><span class="sxs-lookup"><span data-stu-id="bb0ec-112">claimType</span></span>|<span data-ttu-id="bb0ec-113">クレームの種類を定義する URI。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-113">A URI that defines the type of a claim.</span></span> <span data-ttu-id="bb0ec-114">たとえば、Web サイトから製品を購入するために、ユーザーは、十分な与信限度額を備えた有効なクレジット カードを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-114">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="bb0ec-115">クレームの種類として、クレジット カードの URI があります。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-115">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="bb0ec-116">isOptional</span><span class="sxs-lookup"><span data-stu-id="bb0ec-116">isOptional</span></span>|<span data-ttu-id="bb0ec-117">これが省略可能なクレームかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-117">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="bb0ec-118">これが必須のクレームの場合は、この属性を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-118">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="bb0ec-119">サービスが必須でない情報を求めるときにこの属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-119">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="bb0ec-120">たとえば、ユーザーが名、姓、住所を入力する必要があるのに、電話番号は任意であると判断したとします。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-120">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb0ec-121">子要素</span><span class="sxs-lookup"><span data-stu-id="bb0ec-121">Child Elements</span></span>  

 <span data-ttu-id="bb0ec-122">なし。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb0ec-123">親要素</span><span class="sxs-lookup"><span data-stu-id="bb0ec-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bb0ec-124">要素</span><span class="sxs-lookup"><span data-stu-id="bb0ec-124">Element</span></span>|<span data-ttu-id="bb0ec-125">説明</span><span class="sxs-lookup"><span data-stu-id="bb0ec-125">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="bb0ec-126">必須のクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-126">Specifies a collection of required claim types.</span></span> <span data-ttu-id="bb0ec-127">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-127">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="bb0ec-128">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-128">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="bb0ec-129">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-129">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="bb0ec-130">このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-130">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb0ec-131">解説</span><span class="sxs-lookup"><span data-stu-id="bb0ec-131">Remarks</span></span>  

 <span data-ttu-id="bb0ec-132">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-132">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="bb0ec-133">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-133">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="bb0ec-134">この要件はセキュリティ ポリシー内に明記されます。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-134">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="bb0ec-135">クライアントがフェデレーション サービスの資格情報 (CardSpace など) を要求する場合、クライアントは要件をトークン要求 (RequestSecurityToken) に設定します。これにより、フェデレーション サービスは、要件どおりの資格情報を発行できます。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-135">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb0ec-136">例</span><span class="sxs-lookup"><span data-stu-id="bb0ec-136">Example</span></span>  

 <span data-ttu-id="bb0ec-137">次の構成では、2 つのクレームの種類の要件をセキュリティ バインディングに追加しています。</span><span class="sxs-lookup"><span data-stu-id="bb0ec-137">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="bb0ec-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb0ec-138">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

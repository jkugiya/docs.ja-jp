---
description: 詳細については <issuerMetadata> 、 <issuedTokenParameters>
title: <issuerMetadata> の <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 6b0b5064254caf1c6bcf72c2e6d3449402853b98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802243"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="fd7a8-103">\<issuerMetadata> の \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="fd7a8-103">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="fd7a8-104">構文</span><span class="sxs-lookup"><span data-stu-id="fd7a8-104">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd7a8-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fd7a8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fd7a8-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fd7a8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd7a8-107">属性</span><span class="sxs-lookup"><span data-stu-id="fd7a8-107">Attributes</span></span>  
  
|<span data-ttu-id="fd7a8-108">属性</span><span class="sxs-lookup"><span data-stu-id="fd7a8-108">Attribute</span></span>|<span data-ttu-id="fd7a8-109">説明</span><span class="sxs-lookup"><span data-stu-id="fd7a8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd7a8-110">address</span><span class="sxs-lookup"><span data-stu-id="fd7a8-110">address</span></span>|<span data-ttu-id="fd7a8-111">必須。</span><span class="sxs-lookup"><span data-stu-id="fd7a8-111">Required.</span></span> <span data-ttu-id="fd7a8-112">エンドポイントのアドレスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="fd7a8-112">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="fd7a8-113">アドレスは、絶対 URI にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd7a8-113">The address must be an absolute URI.</span></span> <span data-ttu-id="fd7a8-114">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="fd7a8-114">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd7a8-115">子要素</span><span class="sxs-lookup"><span data-stu-id="fd7a8-115">Child Elements</span></span>  
  
|<span data-ttu-id="fd7a8-116">要素</span><span class="sxs-lookup"><span data-stu-id="fd7a8-116">Element</span></span>|<span data-ttu-id="fd7a8-117">説明</span><span class="sxs-lookup"><span data-stu-id="fd7a8-117">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="fd7a8-118">アドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="fd7a8-118">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="fd7a8-119">メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。</span><span class="sxs-lookup"><span data-stu-id="fd7a8-119">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd7a8-120">親要素</span><span class="sxs-lookup"><span data-stu-id="fd7a8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fd7a8-121">要素</span><span class="sxs-lookup"><span data-stu-id="fd7a8-121">Element</span></span>|<span data-ttu-id="fd7a8-122">説明</span><span class="sxs-lookup"><span data-stu-id="fd7a8-122">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="fd7a8-123">フェデレーション セキュリティのシナリオで発行されるセキュリティ トークンのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd7a8-123">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd7a8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd7a8-124">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fd7a8-125">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="fd7a8-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="fd7a8-126">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="fd7a8-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fd7a8-127">カスタム バインディングを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="fd7a8-127">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="fd7a8-128">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="fd7a8-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fd7a8-129">バインド</span><span class="sxs-lookup"><span data-stu-id="fd7a8-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fd7a8-130">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="fd7a8-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fd7a8-131">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="fd7a8-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="fd7a8-132">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="fd7a8-132">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="fd7a8-133">カスタム バインディング セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fd7a8-133">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)

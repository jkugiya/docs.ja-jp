---
description: 詳細については <issuer> 、 <issuedTokenParameters>
title: <issuer> の <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 7d67583eda22414750631b6dff40f6e6ea8831e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725650"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="d4f58-103">\<issuer> の \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="d4f58-103">\<issuer> of \<issuedTokenParameters></span></span>

<span data-ttu-id="d4f58-104">セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4f58-104">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="d4f58-105">構文</span><span class="sxs-lookup"><span data-stu-id="d4f58-105">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4f58-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d4f58-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d4f58-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4f58-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4f58-108">属性</span><span class="sxs-lookup"><span data-stu-id="d4f58-108">Attributes</span></span>  
  
|<span data-ttu-id="d4f58-109">属性</span><span class="sxs-lookup"><span data-stu-id="d4f58-109">Attribute</span></span>|<span data-ttu-id="d4f58-110">説明</span><span class="sxs-lookup"><span data-stu-id="d4f58-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4f58-111">address</span><span class="sxs-lookup"><span data-stu-id="d4f58-111">address</span></span>|<span data-ttu-id="d4f58-112">必須の文字列。</span><span class="sxs-lookup"><span data-stu-id="d4f58-112">Required string.</span></span> <span data-ttu-id="d4f58-113">STS の URL です。</span><span class="sxs-lookup"><span data-stu-id="d4f58-113">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4f58-114">子要素</span><span class="sxs-lookup"><span data-stu-id="d4f58-114">Child Elements</span></span>  
  
|<span data-ttu-id="d4f58-115">要素</span><span class="sxs-lookup"><span data-stu-id="d4f58-115">Element</span></span>|<span data-ttu-id="d4f58-116">説明</span><span class="sxs-lookup"><span data-stu-id="d4f58-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="d4f58-117">ビルダーが作成できるエンドポイントのアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="d4f58-117">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="d4f58-118">発行されたトークンを使用する場合、クライアントでサーバーの認証を有効にする設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4f58-118">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4f58-119">親要素</span><span class="sxs-lookup"><span data-stu-id="d4f58-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d4f58-120">要素</span><span class="sxs-lookup"><span data-stu-id="d4f58-120">Element</span></span>|<span data-ttu-id="d4f58-121">説明</span><span class="sxs-lookup"><span data-stu-id="d4f58-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="d4f58-122">現在発行されているトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4f58-122">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4f58-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4f58-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d4f58-124">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="d4f58-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d4f58-125">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="d4f58-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d4f58-126">カスタム バインディングを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="d4f58-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="d4f58-127">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="d4f58-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d4f58-128">バインド</span><span class="sxs-lookup"><span data-stu-id="d4f58-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d4f58-129">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="d4f58-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d4f58-130">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="d4f58-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="d4f58-131">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="d4f58-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="d4f58-132">カスタム バインディング セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d4f58-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)

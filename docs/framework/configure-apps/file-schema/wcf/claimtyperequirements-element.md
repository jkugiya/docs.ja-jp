---
description: '詳細情報: <claimTypeRequirements> 要素'
title: <claimTypeRequirements> 要素
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 9553c129c246a5f4980d597406bee19ea949bdcc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638913"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="e7c31-103">\<claimTypeRequirements> 要素</span><span class="sxs-lookup"><span data-stu-id="e7c31-103">\<claimTypeRequirements> element</span></span>

<span data-ttu-id="e7c31-104">必須のクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e7c31-104">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="e7c31-105">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="e7c31-105">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e7c31-106">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7c31-106">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e7c31-107">このコレクションの子要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須のクレームおよび省略可能なクレームの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7c31-107">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="e7c31-108">クレームの種類の要件は、発行されるトークンで要求されているクレームの種類の URI と、発行されるトークンでそのクレームの種類が必須かまたは省略可能かを示すブール型のパラメーターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="e7c31-108">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c31-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7c31-109">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e7c31-110">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="e7c31-110">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e7c31-111">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="e7c31-111">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e7c31-112">カスタム バインディングを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="e7c31-112">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="e7c31-113">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="e7c31-113">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="e7c31-114">バインド</span><span class="sxs-lookup"><span data-stu-id="e7c31-114">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e7c31-115">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="e7c31-115">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e7c31-116">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="e7c31-116">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="e7c31-117">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="e7c31-117">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="e7c31-118">カスタム バインディング セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e7c31-118">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)

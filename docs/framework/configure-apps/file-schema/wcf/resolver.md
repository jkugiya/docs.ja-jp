---
description: '詳細情報: <resolver>'
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 338f9342d1ef14f3d96dada17fb9f6d893c86bee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683360"
---
# \<resolver>

<span data-ttu-id="28381-102">ピア メッシュ ID を解決してメッシュに参加する複数ノードを表すピア アドレス セットを取得するためにピア リゾルバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="28381-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
## <a name="syntax"></a><span data-ttu-id="28381-103">構文</span><span class="sxs-lookup"><span data-stu-id="28381-103">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28381-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="28381-104">Attributes and Elements</span></span>  

 <span data-ttu-id="28381-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="28381-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28381-106">属性</span><span class="sxs-lookup"><span data-stu-id="28381-106">Attributes</span></span>  
  
|<span data-ttu-id="28381-107">属性</span><span class="sxs-lookup"><span data-stu-id="28381-107">Attribute</span></span>|<span data-ttu-id="28381-108">説明</span><span class="sxs-lookup"><span data-stu-id="28381-108">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="28381-109">このサービスに関連付けられるピア リゾルバー インスタンスが PNRP 固有、カスタム リゾルバー、自動的に決定されるのいずれであるかを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="28381-109">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="28381-110">この属性は <xref:System.ServiceModel.PeerResolvers.PeerResolverMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="28381-110">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="28381-111">ピア間で参照を共有する方法を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="28381-111">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="28381-112">この属性は <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy> 型です。</span><span class="sxs-lookup"><span data-stu-id="28381-112">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28381-113">子要素</span><span class="sxs-lookup"><span data-stu-id="28381-113">Child Elements</span></span>  
  
|<span data-ttu-id="28381-114">要素</span><span class="sxs-lookup"><span data-stu-id="28381-114">Element</span></span>|<span data-ttu-id="28381-115">説明</span><span class="sxs-lookup"><span data-stu-id="28381-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="28381-116">ユーザー設定のピア リゾルバー サービスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="28381-116">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28381-117">親要素</span><span class="sxs-lookup"><span data-stu-id="28381-117">Parent Elements</span></span>  
  
|<span data-ttu-id="28381-118">要素</span><span class="sxs-lookup"><span data-stu-id="28381-118">Element</span></span>|<span data-ttu-id="28381-119">説明</span><span class="sxs-lookup"><span data-stu-id="28381-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="28381-120">のすべてのバインディング機能を定義 [\<netPeerTcpBinding>](netpeertcpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="28381-120">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28381-121">解説</span><span class="sxs-lookup"><span data-stu-id="28381-121">Remarks</span></span>  

 <span data-ttu-id="28381-122">ピア名リゾルバーは、ピア メッシュに参加するピア ノードを検索するためにピア チャネルにより使用される探索サービスです。</span><span class="sxs-lookup"><span data-stu-id="28381-122">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="28381-123">またピア名リゾルバーは、ノードをピア メッシュに登録するために使用されます。ピア メッシュは、ピア メッシュからピア ノードを認識し、使用可能にするための機構です。</span><span class="sxs-lookup"><span data-stu-id="28381-123">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="28381-124">ピアリゾルバーの詳細については、「 [ピアリゾルバー](../../../wcf/feature-details/peer-resolvers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28381-124">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28381-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="28381-125">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="28381-126">ピア リゾルバー</span><span class="sxs-lookup"><span data-stu-id="28381-126">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="28381-127">[PeerChannel アプリケーションへのカスタム リゾルバーの追加](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="28381-127">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>

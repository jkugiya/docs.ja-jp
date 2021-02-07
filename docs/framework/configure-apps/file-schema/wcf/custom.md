---
description: '詳細情報: <custom>'
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 327a5d7ff1bab88a1633d7a10095e708e6b1a533
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725910"
---
# \<custom>

<span data-ttu-id="5f4b0-102">ユーザー設定のピア リゾルバー サービスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="5f4b0-102">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="5f4b0-103">構文</span><span class="sxs-lookup"><span data-stu-id="5f4b0-103">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f4b0-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5f4b0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5f4b0-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f4b0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f4b0-106">属性</span><span class="sxs-lookup"><span data-stu-id="5f4b0-106">Attributes</span></span>  
  
|<span data-ttu-id="5f4b0-107">属性</span><span class="sxs-lookup"><span data-stu-id="5f4b0-107">Attribute</span></span>|<span data-ttu-id="5f4b0-108">説明</span><span class="sxs-lookup"><span data-stu-id="5f4b0-108">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="5f4b0-109">カスタム ピア リゾルバー サービスをホストするピア ノードのエンドポイント アドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="5f4b0-109">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="5f4b0-110">カスタム ピア リゾルバー サービスの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="5f4b0-110">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f4b0-111">子要素</span><span class="sxs-lookup"><span data-stu-id="5f4b0-111">Child Elements</span></span>  
  
|<span data-ttu-id="5f4b0-112">要素</span><span class="sxs-lookup"><span data-stu-id="5f4b0-112">Element</span></span>|<span data-ttu-id="5f4b0-113">説明</span><span class="sxs-lookup"><span data-stu-id="5f4b0-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="5f4b0-114">この要素を使用して構成されたカスタム ピア リゾルバーの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="5f4b0-114">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="5f4b0-115">この要素は <xref:System.ServiceModel.Configuration.IdentityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="5f4b0-115">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="5f4b0-116">カスタム ピア リゾルバーによって処理される SOAP メッセージに使用するアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="5f4b0-116">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f4b0-117">親要素</span><span class="sxs-lookup"><span data-stu-id="5f4b0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5f4b0-118">要素</span><span class="sxs-lookup"><span data-stu-id="5f4b0-118">Element</span></span>|<span data-ttu-id="5f4b0-119">説明</span><span class="sxs-lookup"><span data-stu-id="5f4b0-119">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="5f4b0-120">ピア メッシュ ID を解決してメッシュに参加する複数ノードを表すピア ノード アドレスのセットを取得するために使用されるピア リゾルバー。</span><span class="sxs-lookup"><span data-stu-id="5f4b0-120">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f4b0-121">解説</span><span class="sxs-lookup"><span data-stu-id="5f4b0-121">Remarks</span></span>  

 <span data-ttu-id="5f4b0-122">この要素は、サービスをホストするピアのエンドポイント アドレスや特定のバインディング設定など、カスタム ピア リゾルバー サービスの基本設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="5f4b0-122">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="5f4b0-123">カスタム競合回避モジュールの作成の詳細については、「 [PeerChannel アプリケーションへのカスタム競合回避モジュールの追加](/previous-versions/ms730105(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f4b0-123">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4b0-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f4b0-124">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="5f4b0-125">ピア リゾルバー</span><span class="sxs-lookup"><span data-stu-id="5f4b0-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="5f4b0-126">[PeerChannel アプリケーションへのカスタム リゾルバーの追加](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5f4b0-126">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>

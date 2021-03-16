---
description: '詳細情報: <pnrpPeerResolver>'
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 4af6a63312fa300cfa33e578f01b8e07267ad3a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683542"
---
# \<pnrpPeerResolver>

<span data-ttu-id="00dfa-102">リゾルバーとして PNRP (Peer Name Resolution Protocol) リゾルバーを使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="00dfa-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="00dfa-103">PNRP は既定のリゾルバーであるため、この要素は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="00dfa-103">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="00dfa-104">構文</span><span class="sxs-lookup"><span data-stu-id="00dfa-104">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00dfa-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="00dfa-105">Attributes and Elements</span></span>  

 <span data-ttu-id="00dfa-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="00dfa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00dfa-107">属性</span><span class="sxs-lookup"><span data-stu-id="00dfa-107">Attributes</span></span>  
  
|<span data-ttu-id="00dfa-108">属性</span><span class="sxs-lookup"><span data-stu-id="00dfa-108">Attribute</span></span>|<span data-ttu-id="00dfa-109">説明</span><span class="sxs-lookup"><span data-stu-id="00dfa-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00dfa-110">resolverType</span><span class="sxs-lookup"><span data-stu-id="00dfa-110">resolverType</span></span>|<span data-ttu-id="00dfa-111">使用されるリゾルバーを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="00dfa-111">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="00dfa-112">この属性は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="00dfa-112">This attribute is optional.</span></span> <span data-ttu-id="00dfa-113">設定されていない場合、または空の文字列に設定されている場合は、PNRP が使用されます。</span><span class="sxs-lookup"><span data-stu-id="00dfa-113">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00dfa-114">子要素</span><span class="sxs-lookup"><span data-stu-id="00dfa-114">Child Elements</span></span>  

 <span data-ttu-id="00dfa-115">なし</span><span class="sxs-lookup"><span data-stu-id="00dfa-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00dfa-116">親要素</span><span class="sxs-lookup"><span data-stu-id="00dfa-116">Parent Elements</span></span>  
  
|<span data-ttu-id="00dfa-117">要素</span><span class="sxs-lookup"><span data-stu-id="00dfa-117">Element</span></span>|<span data-ttu-id="00dfa-118">説明</span><span class="sxs-lookup"><span data-stu-id="00dfa-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="00dfa-119">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="00dfa-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="00dfa-120">例</span><span class="sxs-lookup"><span data-stu-id="00dfa-120">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="00dfa-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="00dfa-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="00dfa-122">バインド</span><span class="sxs-lookup"><span data-stu-id="00dfa-122">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="00dfa-123">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="00dfa-123">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="00dfa-124">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="00dfa-124">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="00dfa-125">ピア リゾルバー</span><span class="sxs-lookup"><span data-stu-id="00dfa-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)

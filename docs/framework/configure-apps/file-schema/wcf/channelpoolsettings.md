---
description: '詳細情報: <channelPoolSettings>'
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 85220cac360aaf32195c0b0f1d2866729e11c442
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638978"
---
# \<channelPoolSettings>

<span data-ttu-id="f7b40-102">カスタム バインディングのチャネル プール設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="f7b40-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="f7b40-103">構文</span><span class="sxs-lookup"><span data-stu-id="f7b40-103">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7b40-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f7b40-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f7b40-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7b40-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7b40-106">属性</span><span class="sxs-lookup"><span data-stu-id="f7b40-106">Attributes</span></span>  
  
|<span data-ttu-id="f7b40-107">属性</span><span class="sxs-lookup"><span data-stu-id="f7b40-107">Attribute</span></span>|<span data-ttu-id="f7b40-108">説明</span><span class="sxs-lookup"><span data-stu-id="f7b40-108">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="f7b40-109">プール内のチャネルの接続が切断されるまでの最大アイドル時間を指定する正の <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="f7b40-109">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="f7b40-110">既定値は 00:02:00 です。</span><span class="sxs-lookup"><span data-stu-id="f7b40-110">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="f7b40-111">プールに返されたチャネルが閉じられるまでの時間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="f7b40-111">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="f7b40-112">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="f7b40-112">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="f7b40-113">各リモート エンドポイントのプール内に格納できるチャネルの最大数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="f7b40-113">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="f7b40-114">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="f7b40-114">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7b40-115">子要素</span><span class="sxs-lookup"><span data-stu-id="f7b40-115">Child Elements</span></span>  

 <span data-ttu-id="f7b40-116">なし。</span><span class="sxs-lookup"><span data-stu-id="f7b40-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7b40-117">親要素</span><span class="sxs-lookup"><span data-stu-id="f7b40-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f7b40-118">要素</span><span class="sxs-lookup"><span data-stu-id="f7b40-118">Element</span></span>|<span data-ttu-id="f7b40-119">説明</span><span class="sxs-lookup"><span data-stu-id="f7b40-119">Description</span></span>|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|<span data-ttu-id="f7b40-120">カスタム バインドでパケット ルーティングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f7b40-120">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7b40-121">解説</span><span class="sxs-lookup"><span data-stu-id="f7b40-121">Remarks</span></span>  

 <span data-ttu-id="f7b40-122">クォータは、リソースの過剰な消費を防ぐためのポリシー メカニズムとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f7b40-122">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="f7b40-123">クォータは、悪質な、または意図的でないサービス拒否 (DOS) 攻撃を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="f7b40-123">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="f7b40-124">カスタム チャネルにチャネル クォータを設定するには、この要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7b40-124">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="f7b40-125">`ChannelPoolSettings` では、次の 3 つのクォータを指定します。</span><span class="sxs-lookup"><span data-stu-id="f7b40-125">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="f7b40-126">`idleTimeout` クォータは、サーバーでは、長時間リソースを停滞させることによるサービス拒否 (DOS) 攻撃を軽減するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f7b40-126">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="f7b40-127">クライアントでは、適切な値を設定することで、サービスとの接続の信頼性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="f7b40-127">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="f7b40-128">既定値では、リソースが控えめに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="f7b40-128">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="f7b40-129">開発環境、および小規模のインストール シナリオに適しています。</span><span class="sxs-lookup"><span data-stu-id="f7b40-129">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="f7b40-130">インストールでリソースが不足している場合、または追加リソースが使用可能であるにもかかわらず接続が制限されている場合、サービス管理者は値を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7b40-130">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="f7b40-131">`leaseTimeout` クォータは、負荷分散機能との統合、および信頼性の向上のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f7b40-131">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="f7b40-132">既定値では、リソースが控えめに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="f7b40-132">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="f7b40-133">開発環境、および小規模のインストール シナリオに適しています。</span><span class="sxs-lookup"><span data-stu-id="f7b40-133">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="f7b40-134">インストールでリソースが不足している場合、または追加リソースが使用可能であるにもかかわらず接続が制限されている場合、サービス管理者は値を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7b40-134">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="f7b40-135">`maxOutboundChannelsPerEndpoint` クォータは、サーバーとクライアントの両方に対するキャッシュ制限を設定し、信頼性向上のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f7b40-135">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="f7b40-136">既定値ではリソースが控えめに割り当てられており、開発環境および小規模なインストール シナリオに適しています。</span><span class="sxs-lookup"><span data-stu-id="f7b40-136">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="f7b40-137">インストールでリソースが不足している場合、または追加リソースが使用可能であるにもかかわらず接続が制限されている場合、サービス管理者は値を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7b40-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7b40-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7b40-138">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [<span data-ttu-id="f7b40-139">バインド</span><span class="sxs-lookup"><span data-stu-id="f7b40-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f7b40-140">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="f7b40-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f7b40-141">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="f7b40-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

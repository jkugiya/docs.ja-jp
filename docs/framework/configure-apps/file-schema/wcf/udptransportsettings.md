---
description: '詳細情報: <udpTransportSettings>'
title: <udpTransportSettings>
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: bfd862009401fef160939fb9acaa66fc9ca23ddb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749156"
---
# \<udpTransportSettings>

<span data-ttu-id="058b1-102">この構成要素は、の UDP トランスポート設定を公開 [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md) します。</span><span class="sxs-lookup"><span data-stu-id="058b1-102">This configuration element exposes UDP transport settings for [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpDiscoveryEndpoint>**](udpdiscoveryendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="058b1-103">構文</span><span class="sxs-lookup"><span data-stu-id="058b1-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="058b1-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="058b1-104">Attributes and Elements</span></span>  

 <span data-ttu-id="058b1-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="058b1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="058b1-106">属性</span><span class="sxs-lookup"><span data-stu-id="058b1-106">Attributes</span></span>  
  
|<span data-ttu-id="058b1-107">属性</span><span class="sxs-lookup"><span data-stu-id="058b1-107">Attribute</span></span>|<span data-ttu-id="058b1-108">説明</span><span class="sxs-lookup"><span data-stu-id="058b1-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="058b1-109">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="058b1-109">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="058b1-110">重複するメッセージを特定するためにトランスポートによって使用されるメッセージ ハッシュの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="058b1-110">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="058b1-111">重複の検出は、TransportManager レベルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="058b1-111">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="058b1-112">このプロパティを 0 に設定すると、重複の検出は無効になります。</span><span class="sxs-lookup"><span data-stu-id="058b1-112">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="058b1-113">この属性を使用して、システムの管理者や開発者は重複するメッセージの検出アルゴリズムをオフにできます。</span><span class="sxs-lookup"><span data-stu-id="058b1-113">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="058b1-114">これは、独自の重複検出アルゴリズムを実行する場合に望ましいことがあります。</span><span class="sxs-lookup"><span data-stu-id="058b1-114">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="058b1-115">既定値は 4112 です。</span><span class="sxs-lookup"><span data-stu-id="058b1-115">The default is 4112.</span></span>|  
|<span data-ttu-id="058b1-116">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="058b1-116">maxBufferPoolSize</span></span>|<span data-ttu-id="058b1-117">トランスポートによって使用されるバッファー プールの最大サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="058b1-117">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="058b1-118">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="058b1-118">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="058b1-119">メッセージを (最初に送信した後に) 再送信する最大回数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="058b1-119">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="058b1-120">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="058b1-120">The default is 2.</span></span>|  
|<span data-ttu-id="058b1-121">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="058b1-121">maxPendingMessageCount</span></span>|<span data-ttu-id="058b1-122">受信して、各チャネル インスタンスの InputQueue からまだ削除していないメッセージの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="058b1-122">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="058b1-123">InputQueue が保留メッセージ数の上限に達すると、メッセージは削除されます。</span><span class="sxs-lookup"><span data-stu-id="058b1-123">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="058b1-124">既定値は 32 です。</span><span class="sxs-lookup"><span data-stu-id="058b1-124">The default is 32.</span></span>|  
|<span data-ttu-id="058b1-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="058b1-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="058b1-126">バインディングで処理できるメッセージの最大サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="058b1-126">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="058b1-127">既定値は 65507 です。</span><span class="sxs-lookup"><span data-stu-id="058b1-127">The default value is 65507.</span></span>|  
|<span data-ttu-id="058b1-128">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="058b1-128">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="058b1-129">メッセージを (最初に送信した後に) 再送信する最大回数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="058b1-129">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="058b1-130">メッセージをユニキャスト アドレスに送信し、対応する RelatesTo ヘッダーの付いた応答メッセージを受信すると、再送信は早期に (再送信の回数が構成された回数に到達する前に) 終了することがあります。</span><span class="sxs-lookup"><span data-stu-id="058b1-130">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="058b1-131">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="058b1-131">The default value is 1.</span></span>|  
|<span data-ttu-id="058b1-132">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="058b1-132">multicastInterfaceId</span></span>|<span data-ttu-id="058b1-133">マルチホーム コンピューター上でマルチキャスト トラフィックを送受信するときに使用するネットワーク アダプターを一意に識別する文字列。</span><span class="sxs-lookup"><span data-stu-id="058b1-133">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="058b1-134">実行時には、トランスポートは、この属性値を使用してインターフェイスのインデックスを参照します。このインデックスは、その後、`IP_MULTICAST_IF` および `IPV6_MULTICAST_IF` のソケット オプションの設定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="058b1-134">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="058b1-135">マルチキャスト グループに参加するときには、同じインターフェイス インデックスが使用されます (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="058b1-135">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="058b1-136">既定値は `null` です。</span><span class="sxs-lookup"><span data-stu-id="058b1-136">The default value is `null`.</span></span>|  
|<span data-ttu-id="058b1-137">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="058b1-137">socketReceiveBufferSize</span></span>|<span data-ttu-id="058b1-138">基になる WinSock ソケットの受信バッファー サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="058b1-138">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="058b1-139">受信チャネルのユーザーは、バインディング上のこの属性を使用して、データ受信時のシステム動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="058b1-139">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="058b1-140">たとえば、受信 WCF メッセージを最大しきい値で利用するアプリケーションがある場合、この属性値よりも大きい値を使用すると、アプリケーションが処理できるようになるまで待機している間、メッセージを WinSock バッファーにスタックできます。</span><span class="sxs-lookup"><span data-stu-id="058b1-140">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="058b1-141">同じ状況で低い値を使用すると、メッセージが破棄される原因となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="058b1-141">Using a lower value in the same situation would result in messages getting dropped.</span></span> <span data-ttu-id="058b1-142">この属性は、基になる WinSock ソケットオプションを公開し `SO_RCVBUF` ます。この属性値は、以上のサイズである必要があり `maxReceivedMessageSize` ます。</span><span class="sxs-lookup"><span data-stu-id="058b1-142">This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="058b1-143">これをより小さい値に設定する `maxReceivedMessageSize` と、ランタイム例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="058b1-143">Setting it to a value smaller than the `maxReceivedMessageSize` will result in a runtime exception.</span></span><br /><br /> <span data-ttu-id="058b1-144">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="058b1-144">The default value is 65536.</span></span>|  
|<span data-ttu-id="058b1-145">timeToLive</span><span class="sxs-lookup"><span data-stu-id="058b1-145">timeToLive</span></span>|<span data-ttu-id="058b1-146">マルチキャスト パケットが走査できるネットワーク セグメント ホップの数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="058b1-146">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="058b1-147">この属性は、`IP_MULTICAST_TTL` および `IP_TTL` ソケット オプションに関連付けられている機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="058b1-147">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="058b1-148">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="058b1-148">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="058b1-149">子要素</span><span class="sxs-lookup"><span data-stu-id="058b1-149">Child Elements</span></span>  

 <span data-ttu-id="058b1-150">なし。</span><span class="sxs-lookup"><span data-stu-id="058b1-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="058b1-151">親要素</span><span class="sxs-lookup"><span data-stu-id="058b1-151">Parent Elements</span></span>  
  
|<span data-ttu-id="058b1-152">要素</span><span class="sxs-lookup"><span data-stu-id="058b1-152">Element</span></span>|<span data-ttu-id="058b1-153">説明</span><span class="sxs-lookup"><span data-stu-id="058b1-153">Description</span></span>|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|<span data-ttu-id="058b1-154">固定探索コントラクトと UDP トランスポート バインディングを持つ標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="058b1-154">A standard endpoint that has fixed discovery contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="058b1-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="058b1-155">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>

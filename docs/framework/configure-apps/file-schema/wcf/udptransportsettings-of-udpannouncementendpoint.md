---
description: 詳細については <udpTransportSettings> 、 <udpAnnouncementEndpoint>
title: <udpTransportSettings> の <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
ms.openlocfilehash: 2997004e162728b20daa4f137e1edf132cd33d52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749208"
---
# <a name="udptransportsettings-of-udpannouncementendpoint"></a><span data-ttu-id="c49db-103">\<udpTransportSettings> の \<udpAnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="c49db-103">\<udpTransportSettings> of \<udpAnnouncementEndpoint></span></span>

<span data-ttu-id="c49db-104">この構成要素は、の UDP トランスポート設定を公開 [\<udpAnnouncementEndpoint>](udpannouncementendpoint.md) します。</span><span class="sxs-lookup"><span data-stu-id="c49db-104">This configuration element exposes UDP transport settings for [\<udpAnnouncementEndpoint>](udpannouncementendpoint.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpAnnouncementEndpoint>**](udpannouncementendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**  

## <a name="syntax"></a><span data-ttu-id="c49db-105">構文</span><span class="sxs-lookup"><span data-stu-id="c49db-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpAnnouncementEndpoint>
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
    </udpAnnouncementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c49db-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c49db-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c49db-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c49db-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c49db-108">属性</span><span class="sxs-lookup"><span data-stu-id="c49db-108">Attributes</span></span>  
  
|<span data-ttu-id="c49db-109">属性</span><span class="sxs-lookup"><span data-stu-id="c49db-109">Attribute</span></span>|<span data-ttu-id="c49db-110">説明</span><span class="sxs-lookup"><span data-stu-id="c49db-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c49db-111">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="c49db-111">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="c49db-112">重複するメッセージを特定するためにトランスポートによって使用されるメッセージ ハッシュの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="c49db-112">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="c49db-113">重複の検出は、TransportManager レベルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="c49db-113">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="c49db-114">このプロパティを 0 に設定すると、重複の検出は無効になります。</span><span class="sxs-lookup"><span data-stu-id="c49db-114">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="c49db-115">この属性を使用して、システムの管理者や開発者は重複するメッセージの検出アルゴリズムをオフにできます。</span><span class="sxs-lookup"><span data-stu-id="c49db-115">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="c49db-116">これは、独自の重複検出アルゴリズムを実行する場合に望ましいことがあります。</span><span class="sxs-lookup"><span data-stu-id="c49db-116">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="c49db-117">既定値は 4112 です。</span><span class="sxs-lookup"><span data-stu-id="c49db-117">The default is 4112.</span></span>|  
|<span data-ttu-id="c49db-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c49db-118">maxBufferPoolSize</span></span>|<span data-ttu-id="c49db-119">トランスポートによって使用されるバッファー プールの最大サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="c49db-119">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="c49db-120">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="c49db-120">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="c49db-121">メッセージを (最初に送信した後に) 再送信する最大回数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="c49db-121">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="c49db-122">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="c49db-122">The default is 2.</span></span>|  
|<span data-ttu-id="c49db-123">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="c49db-123">maxPendingMessageCount</span></span>|<span data-ttu-id="c49db-124">受信して、各チャネル インスタンスの InputQueue からまだ削除していないメッセージの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="c49db-124">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="c49db-125">InputQueue が保留メッセージ数の上限に達すると、メッセージは削除されます。</span><span class="sxs-lookup"><span data-stu-id="c49db-125">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="c49db-126">既定値は 32 です。</span><span class="sxs-lookup"><span data-stu-id="c49db-126">The default is 32.</span></span>|  
|<span data-ttu-id="c49db-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c49db-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="c49db-128">バインディングで処理できるメッセージの最大サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="c49db-128">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="c49db-129">既定値は 65507 です。</span><span class="sxs-lookup"><span data-stu-id="c49db-129">The default value is 65507.</span></span>|  
|<span data-ttu-id="c49db-130">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="c49db-130">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="c49db-131">メッセージを (最初に送信した後に) 再送信する最大回数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="c49db-131">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="c49db-132">メッセージをユニキャスト アドレスに送信し、対応する RelatesTo ヘッダーの付いた応答メッセージを受信すると、再送信は早期に (再送信の回数が構成された回数に到達する前に) 終了することがあります。</span><span class="sxs-lookup"><span data-stu-id="c49db-132">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="c49db-133">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="c49db-133">The default value is 1.</span></span>|  
|<span data-ttu-id="c49db-134">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="c49db-134">multicastInterfaceId</span></span>|<span data-ttu-id="c49db-135">マルチホーム コンピューター上でマルチキャスト トラフィックを送受信するときに使用するネットワーク アダプターを一意に識別する文字列。</span><span class="sxs-lookup"><span data-stu-id="c49db-135">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="c49db-136">実行時には、トランスポートは、この属性値を使用してインターフェイスのインデックスを参照します。このインデックスは、その後、`IP_MULTICAST_IF` および `IPV6_MULTICAST_IF` のソケット オプションの設定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c49db-136">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="c49db-137">マルチキャスト グループに参加するときには、同じインターフェイス インデックスが使用されます (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="c49db-137">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="c49db-138">既定値は `null` です。</span><span class="sxs-lookup"><span data-stu-id="c49db-138">The default value is `null`.</span></span>|  
|<span data-ttu-id="c49db-139">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="c49db-139">socketReceiveBufferSize</span></span>|<span data-ttu-id="c49db-140">基になる WinSock ソケットの受信バッファー サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="c49db-140">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="c49db-141">受信チャネルのユーザーは、バインディング上のこの属性を使用して、データ受信時のシステム動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="c49db-141">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="c49db-142">たとえば、受信 WCF メッセージを最大しきい値で利用するアプリケーションがある場合、この属性値よりも大きい値を使用すると、アプリケーションが処理できるようになるまで待機している間、メッセージを WinSock バッファーにスタックできます。</span><span class="sxs-lookup"><span data-stu-id="c49db-142">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="c49db-143">同じ状況で属性値よりも小さい値を使用すると、メッセージは削除されることになります。この属性は、基になる WinSock `SO_RCVBUF` ソケット オプションを公開します。この属性値には、`maxReceivedMessageSize` のサイズ以上の値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c49db-143">Using a lower value in the same situation would result in messages getting dropped.This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="c49db-144">この値を `maxReceivedMessageSize` よりも小さい値に設定すると、ランタイム例外が発生する原因になります。</span><span class="sxs-lookup"><span data-stu-id="c49db-144">Setting it to a value smaller than the `maxReceivedMessageSize` will result in runtime exception.</span></span><br /><br /> <span data-ttu-id="c49db-145">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="c49db-145">The default value is 65536.</span></span>|  
|<span data-ttu-id="c49db-146">timeToLive</span><span class="sxs-lookup"><span data-stu-id="c49db-146">timeToLive</span></span>|<span data-ttu-id="c49db-147">マルチキャスト パケットが走査できるネットワーク セグメント ホップの数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="c49db-147">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="c49db-148">この属性は、`IP_MULTICAST_TTL` および `IP_TTL` ソケット オプションに関連付けられている機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="c49db-148">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="c49db-149">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="c49db-149">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c49db-150">子要素</span><span class="sxs-lookup"><span data-stu-id="c49db-150">Child Elements</span></span>  

 <span data-ttu-id="c49db-151">なし。</span><span class="sxs-lookup"><span data-stu-id="c49db-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c49db-152">親要素</span><span class="sxs-lookup"><span data-stu-id="c49db-152">Parent Elements</span></span>  
  
|<span data-ttu-id="c49db-153">要素</span><span class="sxs-lookup"><span data-stu-id="c49db-153">Element</span></span>|<span data-ttu-id="c49db-154">説明</span><span class="sxs-lookup"><span data-stu-id="c49db-154">Description</span></span>|  
|-------------|-----------------|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|<span data-ttu-id="c49db-155">固定アナウンス コントラクトと UDP トランスポート バインディングを持つ標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="c49db-155">A standard endpoint that has fixed announcement contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c49db-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="c49db-156">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>

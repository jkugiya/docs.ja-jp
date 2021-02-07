---
description: '詳細情報: <namedPipeTransport>'
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 68714404492be92ce789dbde95a39199f5de16d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684101"
---
# \<namedPipeTransport>

<span data-ttu-id="3a059-102">チャネルがカスタム バインドに含まれているときに名前付きパイプを使用してメッセージを転送するトランスポートを定義します。</span><span class="sxs-lookup"><span data-stu-id="3a059-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="3a059-103">構文</span><span class="sxs-lookup"><span data-stu-id="3a059-103">Syntax</span></span>  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a059-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3a059-104">Attributes and Elements</span></span>  

<span data-ttu-id="3a059-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3a059-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a059-106">属性</span><span class="sxs-lookup"><span data-stu-id="3a059-106">Attributes</span></span>  

<span data-ttu-id="3a059-107">なし。</span><span class="sxs-lookup"><span data-stu-id="3a059-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a059-108">子要素</span><span class="sxs-lookup"><span data-stu-id="3a059-108">Child Elements</span></span>  
  
|<span data-ttu-id="3a059-109">要素</span><span class="sxs-lookup"><span data-stu-id="3a059-109">Element</span></span>|<span data-ttu-id="3a059-110">説明</span><span class="sxs-lookup"><span data-stu-id="3a059-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a059-111">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="3a059-111">ChannelInitializationTimeout</span></span>|<span data-ttu-id="3a059-112">接続が切断されるまでのチャネルの初期化ステータスの最大時間を決定する <xref:System.TimeSpan> を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-112">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="3a059-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="3a059-113">ConnectionBufferSize</span></span>|<span data-ttu-id="3a059-114">クライアントまたサービスからネットワークでシリアル化されたメッセージのチャンクを転送するために使用されるバッファーのサイズを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-114">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="3a059-115">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="3a059-115">hostNameComparisonMode</span></span>|<span data-ttu-id="3a059-116">URI で一致する場合にサービスに到達するためにホスト名を使用するかどうかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-116">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="3a059-117">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="3a059-117">manualAddressing</span></span>|<span data-ttu-id="3a059-118">メッセージの手動アドレス指定が必要かどうかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-118">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="3a059-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="3a059-119">maxBufferPoolSize</span></span>|<span data-ttu-id="3a059-120">トランスポートが使用するバッファー プールの最大サイズ (バイト単位) を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-120">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="3a059-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="3a059-121">maxBufferSize</span></span>|<span data-ttu-id="3a059-122">使用するバッファーの最大サイズを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-122">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="3a059-123">ストリーム メッセージの場合、この値は少なくともメッセージ ヘッダーで使用できる最大サイズにする必要があります。これは、バッファー モードで読み取られます。</span><span class="sxs-lookup"><span data-stu-id="3a059-123">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="3a059-124">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="3a059-124">maxOutputDelay</span></span>|<span data-ttu-id="3a059-125">メッセージのチャンクまたは完全なメッセージを、送信前にメモリ内のバッファーに残したままにできる最長期間を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-125">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="3a059-126">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="3a059-126">maxPendingAccepts</span></span>|<span data-ttu-id="3a059-127">サービスへの受信接続を処理するためにサービスがリスナーで待機できるチャネルの最大数を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-127">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="3a059-128">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="3a059-128">maxPendingConnections</span></span>|<span data-ttu-id="3a059-129">サービスでディスパッチを待機している最大接続数を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-129">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="3a059-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="3a059-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="3a059-131">受信できるメッセージの最大サイズをバイト単位で取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-131">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="3a059-132">transferMode</span><span class="sxs-lookup"><span data-stu-id="3a059-132">transferMode</span></span>|<span data-ttu-id="3a059-133">接続指向のトランスポートでメッセージをバッファーするか、ストリーム配信するかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-133">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="3a059-134">\<namedPipeTransport> の \<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="3a059-134">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="3a059-135">名前付きパイプ バインディングの追加の接続プール設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="3a059-135">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a059-136">親要素</span><span class="sxs-lookup"><span data-stu-id="3a059-136">Parent Elements</span></span>  
  
|<span data-ttu-id="3a059-137">要素</span><span class="sxs-lookup"><span data-stu-id="3a059-137">Element</span></span>|<span data-ttu-id="3a059-138">説明</span><span class="sxs-lookup"><span data-stu-id="3a059-138">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="3a059-139">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="3a059-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a059-140">解説</span><span class="sxs-lookup"><span data-stu-id="3a059-140">Remarks</span></span>  

<span data-ttu-id="3a059-141">このトランスポートは、"net.pipe://hostname/path" の形式の URI を使用します。</span><span class="sxs-lookup"><span data-stu-id="3a059-141">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="3a059-142">他の URI コンポーネントは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3a059-142">Other URI components are optional.</span></span>  
  
<span data-ttu-id="3a059-143">`namedPipeTransport` 要素は、名前付きパイプ トランスポート プロトコルを実装するカスタム バインディングを作成する場合の開始点となります。</span><span class="sxs-lookup"><span data-stu-id="3a059-143">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="3a059-144">このトランスポートは、コンピューター上での WCF (Windows Communication Foundation) 間の通信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3a059-144">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a059-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a059-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3a059-146">トランスポート</span><span class="sxs-lookup"><span data-stu-id="3a059-146">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="3a059-147">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="3a059-147">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="3a059-148">バインド</span><span class="sxs-lookup"><span data-stu-id="3a059-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3a059-149">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="3a059-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3a059-150">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="3a059-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

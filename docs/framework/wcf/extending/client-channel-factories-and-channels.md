---
description: '詳細については、「クライアント: チャネルファクトリとチャネル」を参照してください。'
title: クライアント:チャネル ファクトリとチャネル
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: b61c37743899b8ba74ec18cc84397e4521e7bde7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803036"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="d9d63-103">クライアント:チャネル ファクトリとチャネル</span><span class="sxs-lookup"><span data-stu-id="d9d63-103">Client: Channel Factories and Channels</span></span>

<span data-ttu-id="d9d63-104">ここでは、チャネル ファクトリとチャネルの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-104">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="d9d63-105">チャネル ファクトリとチャネル</span><span class="sxs-lookup"><span data-stu-id="d9d63-105">Channel Factories and Channels</span></span>  

 <span data-ttu-id="d9d63-106">チャネル ファクトリには、チャネルを作成する役割があります。</span><span class="sxs-lookup"><span data-stu-id="d9d63-106">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="d9d63-107">チャネル ファクトリによって作成されるチャネルは、メッセージの送信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d9d63-107">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="d9d63-108">このチャネルは、上の層からメッセージを取得し、必要な処理を実行し、そのメッセージを下の層に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9d63-108">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="d9d63-109">このプロセスを説明する図を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-109">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="d9d63-110">![クライアント ファクトリおよびチャネル](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="d9d63-110">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="d9d63-111">チャネル ファクトリがチャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-111">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="d9d63-112">終了時に、チャネル ファクトリは、作成したチャネルのうちまだ閉じていないチャネルを閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9d63-112">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="d9d63-113">チャネル リスナーを閉じたとき、新しいチャネルの受け入れだけが停止され、既存のチャネルは開いたままで、メッセージの受信を続行できるので、ここに示すモデルは非対称です。</span><span class="sxs-lookup"><span data-stu-id="d9d63-113">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="d9d63-114">WCF には、このプロセスの基底クラスヘルパーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d9d63-114">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="d9d63-115">(このトピックで説明するチャネルヘルパークラスの図については、「 [チャネルモデルの概要](channel-model-overview.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="d9d63-115">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="d9d63-116"><xref:System.ServiceModel.Channels.CommunicationObject>クラスは、 <xref:System.ServiceModel.ICommunicationObject> 「[チャネルの開発](developing-channels.md)」の手順 2. で説明されているステートマシンを実装し、適用します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-116">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="d9d63-117"><xref:System.ServiceModel.Channels.ChannelManagerBase> クラスには <xref:System.ServiceModel.Channels.CommunicationObject> が実装され、<xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> と <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType> の統合基本クラスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d9d63-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d9d63-118"><xref:System.ServiceModel.Channels.ChannelManagerBase> クラスは、<xref:System.ServiceModel.Channels.ChannelBase> を実装する基本クラスである <xref:System.ServiceModel.Channels.IChannel> との組み合わせによって動作します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-118">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="d9d63-119"><xref:System.ServiceModel.Channels.ChannelFactoryBase>クラスは <xref:System.ServiceModel.Channels.ChannelManagerBase> 、とを実装し、オーバーロードを <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` 1 つの抽象メソッドに統合し `OnCreateChannel` ます。</span><span class="sxs-lookup"><span data-stu-id="d9d63-119">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="d9d63-120"><xref:System.ServiceModel.Channels.ChannelListenerBase> クラスは、<xref:System.ServiceModel.Channels.IChannelListener> を実装しています。</span><span class="sxs-lookup"><span data-stu-id="d9d63-120">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="d9d63-121">基本状態管理を行います。</span><span class="sxs-lookup"><span data-stu-id="d9d63-121">It takes care of basic state management.</span></span>
  
 <span data-ttu-id="d9d63-122">次の説明は、 [Transport: UDP](../samples/transport-udp.md) サンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="d9d63-122">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="d9d63-123">チャネル ファクトリの作成</span><span class="sxs-lookup"><span data-stu-id="d9d63-123">Creating a Channel Factory</span></span>  

 <span data-ttu-id="d9d63-124">`UdpChannelFactory` は <xref:System.ServiceModel.Channels.ChannelFactoryBase> から派生します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-124">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="d9d63-125">サンプルでは、<xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> をオーバーライドして、メッセージ エンコーダーのメッセージ バージョンにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="d9d63-125">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="d9d63-126">さらに、<xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> をオーバーライドして、ステート マシンの移行時に <xref:System.ServiceModel.Channels.BufferManager> のインスタンスを破棄します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-126">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="d9d63-127">UDP 出力チャネル</span><span class="sxs-lookup"><span data-stu-id="d9d63-127">The UDP Output Channel</span></span>  

 <span data-ttu-id="d9d63-128">`UdpOutputChannel` では、<xref:System.ServiceModel.Channels.IOutputChannel> が実装されます。</span><span class="sxs-lookup"><span data-stu-id="d9d63-128">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="d9d63-129">このコンストラクターは、引数を検証し、渡される <xref:System.Net.EndPoint> に基づいて出力先の <xref:System.ServiceModel.EndpointAddress> オブジェクトを構築します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-129">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="d9d63-130"><xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> のオーバーライドによって、この <xref:System.Net.EndPoint> にメッセージを送信するために使用されるソケットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d9d63-130">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="d9d63-131">チャネルが閉じる際には、正常終了することも異常終了することもあります。</span><span class="sxs-lookup"><span data-stu-id="d9d63-131">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="d9d63-132">チャネルが正常に閉じた場合はソケットも終了し、基本クラスの `OnClose` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d9d63-132">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="d9d63-133">このときに例外がスローされると、インフラストラクチャによって `Abort` が呼び出され、チャネルがクリーンアップされます。</span><span class="sxs-lookup"><span data-stu-id="d9d63-133">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="d9d63-134">`Send()`およびを実装 `BeginSend()` / `EndSend()` します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-134">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="d9d63-135">この実装は、2 つの主要セクションに分かれます。</span><span class="sxs-lookup"><span data-stu-id="d9d63-135">This breaks down into two main sections.</span></span> <span data-ttu-id="d9d63-136">最初に、メッセージを次のようにシリアル化してバイト配列で表します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-136">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="d9d63-137">次に、結果として生成されたデータを次のようにネットワークに送信します。</span><span class="sxs-lookup"><span data-stu-id="d9d63-137">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9d63-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9d63-138">See also</span></span>

- [<span data-ttu-id="d9d63-139">チャネルの開発</span><span class="sxs-lookup"><span data-stu-id="d9d63-139">Developing Channels</span></span>](developing-channels.md)

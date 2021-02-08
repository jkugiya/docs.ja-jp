---
description: '詳細については、「トランスポート: WSE 3.0 TCP 相互運用性」を参照してください。'
title: トランスポート:WSE 3.0 TCP 相互運用性
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 2e0a5927b8f16116dc07910970268ff6ec35f396
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798239"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="405a1-103">トランスポート:WSE 3.0 TCP 相互運用性</span><span class="sxs-lookup"><span data-stu-id="405a1-103">Transport: WSE 3.0 TCP Interoperability</span></span>

<span data-ttu-id="405a1-104">WSE 3.0 TCP 相互運用性トランスポートサンプルは、TCP 二重セッションをカスタム Windows Communication Foundation (WCF) トランスポートとして実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="405a1-104">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="405a1-105">さらに、チャネル レイヤーの拡張機能を使用して、ネットワーク経由で既存の配置システムと連結する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="405a1-105">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="405a1-106">次の手順は、このカスタム WCF トランスポートを構築する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="405a1-106">The following steps show how to build this custom WCF transport:</span></span>  
  
1. <span data-ttu-id="405a1-107">まず TCP ソケットを使用して、DIME フレームを使用する <xref:System.ServiceModel.Channels.IDuplexSessionChannel> のクライアント実装とサーバー実装を作成し、メッセージ境界を決定します。</span><span class="sxs-lookup"><span data-stu-id="405a1-107">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2. <span data-ttu-id="405a1-108">WSE TCP サービスに接続してクライアント <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 経由でフレーム メッセージを送信する、チャネル ファクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="405a1-108">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3. <span data-ttu-id="405a1-109">受信 TCP 接続を受け入れて対応するチャネルを作成するチャネル リスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="405a1-109">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4. <span data-ttu-id="405a1-110">ネットワーク固有の例外が、<xref:System.ServiceModel.CommunicationException> の適切な派生クラスに標準化されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="405a1-110">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5. <span data-ttu-id="405a1-111">チャネル スタックにカスタム トランスポートを追加するバインド要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="405a1-111">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="405a1-112">詳細については、「バインディング要素の追加」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="405a1-112">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="405a1-113">IDuplexSessionChannel の作成</span><span class="sxs-lookup"><span data-stu-id="405a1-113">Creating IDuplexSessionChannel</span></span>  

 <span data-ttu-id="405a1-114">WSE 3.0 TCP 相互運用性トランスポートを作成するには、まず、<xref:System.ServiceModel.Channels.IDuplexSessionChannel> 上に <xref:System.Net.Sockets.Socket> の実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="405a1-114">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="405a1-115">`WseTcpDuplexSessionChannel` は、<xref:System.ServiceModel.Channels.ChannelBase> から派生します。</span><span class="sxs-lookup"><span data-stu-id="405a1-115">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="405a1-116">メッセージ送信のロジックは、(1) メッセージをバイトにエンコードし、(2) それらのバイトをフレーム化してネットワーク上に送信するという、2 つの主要部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="405a1-116">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="405a1-117">さらに、Send() 呼び出しが IDuplexSessionChannel の順序の保証を保持し、基になるソケットに対する呼び出しが正しく同期されるように、ロックを取得します。</span><span class="sxs-lookup"><span data-stu-id="405a1-117">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="405a1-118">`WseTcpDuplexSessionChannel` は、<xref:System.ServiceModel.Channels.MessageEncoder> と byte[] を相互に変換するために、<xref:System.ServiceModel.Channels.Message> を使用します。</span><span class="sxs-lookup"><span data-stu-id="405a1-118">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="405a1-119">`WseTcpDuplexSessionChannel` はトランスポートであるため、チャネルが構成されたリモート アドレスの適用も行います。</span><span class="sxs-lookup"><span data-stu-id="405a1-119">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="405a1-120">`EncodeMessage` は、この変換ロジックをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="405a1-120">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="405a1-121"><xref:System.ServiceModel.Channels.Message> がバイトにエンコードされたら、ネットワーク上に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="405a1-121">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="405a1-122">これを行うには、メッセージ境界を定義するシステムが必要です。</span><span class="sxs-lookup"><span data-stu-id="405a1-122">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="405a1-123">WSE 3.0 では、フレームプロトコルとしてのバージョンの [DIME](/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="405a1-123">WSE 3.0 uses a version of [DIME](/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) as its framing protocol.</span></span> <span data-ttu-id="405a1-124">`WriteData` はこのフレーム ロジックをカプセル化して、byte[] を一連の DIME レコードにラップします。</span><span class="sxs-lookup"><span data-stu-id="405a1-124">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="405a1-125">メッセージを受信するためのロジックも似ています。</span><span class="sxs-lookup"><span data-stu-id="405a1-125">The logic for receiving messages is similar.</span></span> <span data-ttu-id="405a1-126">主な複雑さは、ソケットの読み取りが要求されたバイト数よりも小さいバイト数を返す可能性があるということです。</span><span class="sxs-lookup"><span data-stu-id="405a1-126">The main complexity is handling the fact that a socket read can return fewer bytes than were requested.</span></span> <span data-ttu-id="405a1-127">メッセージを受信するには、`WseTcpDuplexSessionChannel` がネットワーク経由でないバイトを読み取って DIME フレームを復号化し、その後<xref:System.ServiceModel.Channels.MessageEncoder> を使用して byte[] を <xref:System.ServiceModel.Channels.Message> に変換します。</span><span class="sxs-lookup"><span data-stu-id="405a1-127">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="405a1-128">基本の `WseTcpDuplexSessionChannel` は、接続されたソケットを受信することを前提とします。</span><span class="sxs-lookup"><span data-stu-id="405a1-128">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="405a1-129">この基本クラスでは、ソケットのシャットダウンが処理されます。</span><span class="sxs-lookup"><span data-stu-id="405a1-129">The base class handles socket shutdown.</span></span> <span data-ttu-id="405a1-130">ソケットの終了と連動する場所は、次の 3 つです。</span><span class="sxs-lookup"><span data-stu-id="405a1-130">There are three places that interface with socket closure:</span></span>  
  
- <span data-ttu-id="405a1-131">OnAbort -- ソケットを異常終了します (強制終了)。</span><span class="sxs-lookup"><span data-stu-id="405a1-131">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
- <span data-ttu-id="405a1-132">On[Begin]Close -- ソケットを正常に終了します (正常終了)。</span><span class="sxs-lookup"><span data-stu-id="405a1-132">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
- <span data-ttu-id="405a1-133">セッション.CloseOutputSession--送信データストリーム (半終了) をシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="405a1-133">session.CloseOutputSession -- shut down the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="405a1-134">チャネル ファクトリ</span><span class="sxs-lookup"><span data-stu-id="405a1-134">Channel Factory</span></span>  

 <span data-ttu-id="405a1-135">TCP トランスポートを記述する次の手順では、クライアント チャネルでの <xref:System.ServiceModel.Channels.IChannelFactory> の実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="405a1-135">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
- <span data-ttu-id="405a1-136">`WseTcpChannelFactory`から派生 <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel> します。</span><span class="sxs-lookup"><span data-stu-id="405a1-136">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="405a1-137">このファクトリは、`OnCreateChannel` をオーバーライドして、クライアント チャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="405a1-137">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- <span data-ttu-id="405a1-138">`ClientWseTcpDuplexSessionChannel` ベースにロジックを追加して、 `WseTcpDuplexSessionChannel` TCP サーバーに接続し `channel.Open` ます。</span><span class="sxs-lookup"><span data-stu-id="405a1-138">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="405a1-139">まず、次のコードに示すようにホスト名を解決して IP アドレスに変換します。</span><span class="sxs-lookup"><span data-stu-id="405a1-139">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- <span data-ttu-id="405a1-140">次のコードに示すように、ホスト名はループ内で最初に利用可能な IP アドレスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="405a1-140">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- <span data-ttu-id="405a1-141">チャネル コントラクトの一部として、`SocketException` の <xref:System.ServiceModel.CommunicationException> など、ドメイン固有の任意の例外をラップします。</span><span class="sxs-lookup"><span data-stu-id="405a1-141">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="405a1-142">チャネル リスナー</span><span class="sxs-lookup"><span data-stu-id="405a1-142">Channel Listener</span></span>  

 <span data-ttu-id="405a1-143">TCP トランスポートを記述する次の手順では、サーバー チャネルを受け入れるための <xref:System.ServiceModel.Channels.IChannelListener> の実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="405a1-143">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
- <span data-ttu-id="405a1-144">`WseTcpChannelListener`<xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel> は、から派生し、[Begin] Open と On [begin] によってオーバーライドされ、リッスンソケットの有効期間を制御します。</span><span class="sxs-lookup"><span data-stu-id="405a1-144">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="405a1-145">OnOpen で、IP_ANY でリッスンするソケットを作成します。</span><span class="sxs-lookup"><span data-stu-id="405a1-145">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="405a1-146">より高度な実装では、同様に IPv6 でリッスンする 2 つ目のソケットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="405a1-146">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="405a1-147">そのような実装では、IP アドレスをホスト名で指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="405a1-147">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="405a1-148">新しいソケットが受け入れられると、サーバー チャネルがこのソケットで初期化されます。</span><span class="sxs-lookup"><span data-stu-id="405a1-148">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="405a1-149">すべての入出力は既に基本クラスに実装されているので、このチャネルでソケットの初期化に対応します。</span><span class="sxs-lookup"><span data-stu-id="405a1-149">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="405a1-150">バインド要素の追加</span><span class="sxs-lookup"><span data-stu-id="405a1-150">Adding a Binding Element</span></span>  

 <span data-ttu-id="405a1-151">ファクトリおよびチャネルを作成したら、バインディングを使用してそれらを ServiceModel ランタイムに開示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="405a1-151">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="405a1-152">バインディングは、サービス アドレスに関連する通信スタックを表すバインド要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="405a1-152">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="405a1-153">スタックの各要素は、バインド要素によって表されます。</span><span class="sxs-lookup"><span data-stu-id="405a1-153">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="405a1-154">このサンプルでは、バインド要素は `WseTcpTransportBindingElement` で、<xref:System.ServiceModel.Channels.TransportBindingElement> から派生しています。</span><span class="sxs-lookup"><span data-stu-id="405a1-154">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="405a1-155"><xref:System.ServiceModel.Channels.IDuplexSessionChannel> がサポートされており、次のメソッドをオーバーライドして、バインディングに関連したファクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="405a1-155">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="405a1-156">また、この要素には、`BindingElement` を複製したり、スキーム (wse.tcp) を返したりするためのメンバーも含まれます。</span><span class="sxs-lookup"><span data-stu-id="405a1-156">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="405a1-157">WSE TCP テスト コンソール</span><span class="sxs-lookup"><span data-stu-id="405a1-157">The WSE TCP Test Console</span></span>  

 <span data-ttu-id="405a1-158">このサンプルのトランスポートを使用するテスト コードは、TestCode.cs で使用できます。</span><span class="sxs-lookup"><span data-stu-id="405a1-158">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="405a1-159">WSE `TcpSyncStockService` サンプルの設定方法を次の手順に示します。</span><span class="sxs-lookup"><span data-stu-id="405a1-159">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="405a1-160">このテスト コードでは、MTOM をエンコーディングとして使用し、`WseTcpTransport` をトランスポートとして使用するカスタム バインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="405a1-160">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="405a1-161">さらに、AddressingVersion を、次のコードに示すように WSE 3.0 に準拠するように設定します。</span><span class="sxs-lookup"><span data-stu-id="405a1-161">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="405a1-162">テスト コードは 2 つのテストで構成されます。1 つ目のテストは、WSE 3.0 WSDL から生成されたコードを使用して型指定のあるクライアントを設定します。</span><span class="sxs-lookup"><span data-stu-id="405a1-162">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="405a1-163">2番目のテストでは、チャネル Api の上に直接メッセージを送信することによって、WCF をクライアントとサーバーの両方として使用します。</span><span class="sxs-lookup"><span data-stu-id="405a1-163">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="405a1-164">このサンプルを実行すると、次の出力が予測されます。</span><span class="sxs-lookup"><span data-stu-id="405a1-164">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="405a1-165">クライアント: </span><span class="sxs-lookup"><span data-stu-id="405a1-165">Client:</span></span>  
  
```console  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 <span data-ttu-id="405a1-166">サーバー: </span><span class="sxs-lookup"><span data-stu-id="405a1-166">Server:</span></span>  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="405a1-167">サンプルをセットアップ、ビルド、および実行する</span><span class="sxs-lookup"><span data-stu-id="405a1-167">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="405a1-168">このサンプルを実行するには、 [Microsoft .NET 用の Web サービス拡張 (wse) 3.0](https://www.microsoft.com/download/details.aspx?id=14089) と wse サンプルがインストールされている必要があり `TcpSyncStockService` ます。</span><span class="sxs-lookup"><span data-stu-id="405a1-168">To run this sample, you must have [Web Services Enhancements (WSE) 3.0 for Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) and the WSE `TcpSyncStockService` sample installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="405a1-169">WSE 3.0 は Windows Server 2008 ではサポートされていないため、この `TcpSyncStockService` オペレーティングシステムにサンプルをインストールしたり、実行したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="405a1-169">Because WSE 3.0 is not supported on Windows Server 2008, you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1. <span data-ttu-id="405a1-170">`TcpSyncStockService` サンプルをインストールしたら、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="405a1-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1. <span data-ttu-id="405a1-171">`TcpSyncStockService`Visual Studio でを開きます。</span><span class="sxs-lookup"><span data-stu-id="405a1-171">Open the `TcpSyncStockService` in Visual Studio.</span></span> <span data-ttu-id="405a1-172">(TcpSyncStockService サンプルは、WSE 3.0 と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="405a1-172">(The TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="405a1-173">このサンプルコードの一部ではありません)。</span><span class="sxs-lookup"><span data-stu-id="405a1-173">It is not part of this sample's code.)</span></span>  
  
    2. <span data-ttu-id="405a1-174">StockService プロジェクトをスタートアッププロジェクトとして設定します。</span><span class="sxs-lookup"><span data-stu-id="405a1-174">Set the StockService project as the start-up project.</span></span>  
  
    3. <span data-ttu-id="405a1-175">StockService プロジェクトの StockService.cs を開き、`StockService` クラスの [Policy] 属性をコメント化します。</span><span class="sxs-lookup"><span data-stu-id="405a1-175">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="405a1-176">これにより、サンプルのセキュリティが無効になります。</span><span class="sxs-lookup"><span data-stu-id="405a1-176">This disables security from the sample.</span></span> <span data-ttu-id="405a1-177">WCF は WSE 3.0 のセキュリティで保護されたエンドポイントと相互運用することができますが、このサンプルをカスタム TCP トランスポートに重点を置くため、セキュリティは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="405a1-177">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4. <span data-ttu-id="405a1-178">F5 キーを押して、`TcpSyncStockService` を開始します。</span><span class="sxs-lookup"><span data-stu-id="405a1-178">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="405a1-179">サービスが新しいコンソール ウィンドウで開始します。</span><span class="sxs-lookup"><span data-stu-id="405a1-179">The service starts in a new console window.</span></span>  
  
    5. <span data-ttu-id="405a1-180">Visual Studio で、この TCP トランスポートのサンプルを開きます。</span><span class="sxs-lookup"><span data-stu-id="405a1-180">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6. <span data-ttu-id="405a1-181">TestCode.cs 内の hostname 変数の値を、`TcpSyncStockService` が実行されているコンピューター名に一致するように更新します。</span><span class="sxs-lookup"><span data-stu-id="405a1-181">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7. <span data-ttu-id="405a1-182">F5 キーを押して、TCP トランスポートのサンプルを開始します。</span><span class="sxs-lookup"><span data-stu-id="405a1-182">Press F5 to start the TCP transport sample.</span></span>  
  
    8. <span data-ttu-id="405a1-183">TCP トランスポートのテスト クライアントが、新しいコンソールで開始します。</span><span class="sxs-lookup"><span data-stu-id="405a1-183">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="405a1-184">クライアントはサービスに株価情報を要求し、その結果がコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="405a1-184">The client requests stock quotes from the service and then displays the results in its console window.</span></span>

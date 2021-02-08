---
description: 詳細については、「クライアント Channel-Level プログラミング」を参照してください。
title: クライアントのチャネル レベルのプログラミング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: 7e4e977231339fbbede7111e38a67054eb24eed9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802997"
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="41edd-103">クライアントのチャネル レベルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="41edd-103">Client Channel-Level Programming</span></span>

<span data-ttu-id="41edd-104">このトピックでは、 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> クラスとそれに関連付けられているオブジェクトモデルを使用せずに、Windows Communication Foundation (WCF) クライアントアプリケーションを記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="41edd-104">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="41edd-105">sending messages</span><span class="sxs-lookup"><span data-stu-id="41edd-105">Sending Messages</span></span>  

 <span data-ttu-id="41edd-106">メッセージを送信し、応答を受信して処理できるようにするには、次の手順に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="41edd-106">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1. <span data-ttu-id="41edd-107">バインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="41edd-107">Create a binding.</span></span>  
  
2. <span data-ttu-id="41edd-108">チャネル ファクトリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="41edd-108">Build a channel factory.</span></span>  
  
3. <span data-ttu-id="41edd-109">チャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="41edd-109">Create a channel.</span></span>  
  
4. <span data-ttu-id="41edd-110">要求を送信し、応答を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="41edd-110">Send a request and read the reply.</span></span>  
  
5. <span data-ttu-id="41edd-111">すべてのチャネル オブジェクトを閉じます。</span><span class="sxs-lookup"><span data-stu-id="41edd-111">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="41edd-112">バインディングの作成</span><span class="sxs-lookup"><span data-stu-id="41edd-112">Creating a Binding</span></span>  

 <span data-ttu-id="41edd-113">受信側のケース (「 [サービス Channel-Level プログラミング](service-channel-level-programming.md)」を参照) と同様に、メッセージの送信はバインドを作成することから始まります。</span><span class="sxs-lookup"><span data-stu-id="41edd-113">Similar to the receiving case (see [Service Channel-Level Programming](service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="41edd-114">この例では、新しい <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> を作成し、その要素コレクションに <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> を追加します。</span><span class="sxs-lookup"><span data-stu-id="41edd-114">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="41edd-115">ChannelFactory のビルド</span><span class="sxs-lookup"><span data-stu-id="41edd-115">Building a ChannelFactory</span></span>  

 <span data-ttu-id="41edd-116"><xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType> を作成する代わりに、今回はバインディングで型パラメーターを <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> にして <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> を呼び出すことで、<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType> を作成します。</span><span class="sxs-lookup"><span data-stu-id="41edd-116">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41edd-117">チャネル リスナーは受信メッセージを待機する側で使用されますが、チャネル ファクトリはチャネルを作成するために通信を開始する側で使用されます。</span><span class="sxs-lookup"><span data-stu-id="41edd-117">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="41edd-118">チャネル リスナーと同様に、チャネル ファクトリも使用する前に開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="41edd-118">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="41edd-119">チャネルの作成</span><span class="sxs-lookup"><span data-stu-id="41edd-119">Creating a Channel</span></span>  

 <span data-ttu-id="41edd-120">次に <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> を呼び出して、<xref:System.ServiceModel.Channels.IRequestChannel> を作成します。</span><span class="sxs-lookup"><span data-stu-id="41edd-120">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="41edd-121">この呼び出しには、新しく作成するチャネルを使用して通信を行う対象となるエンドポイントのアドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="41edd-121">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="41edd-122">チャネルを作成したら、このチャネルで Open を呼び出して通信できる状態にします。</span><span class="sxs-lookup"><span data-stu-id="41edd-122">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="41edd-123">この Open の呼び出しにより、トランスポートの性質に応じて、目的のエンドポイントとの接続が開始されることもあれば、ネットワーク上では何も起こらないこともあります。</span><span class="sxs-lookup"><span data-stu-id="41edd-123">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="41edd-124">要求の送信と応答の読み取り</span><span class="sxs-lookup"><span data-stu-id="41edd-124">Sending a Request and Reading the Reply</span></span>  

 <span data-ttu-id="41edd-125">チャネルが開かれると、メッセージを作成して、チャネルの Request メソッドを使用して要求を送信し、応答が返ってくるのを待機できます。</span><span class="sxs-lookup"><span data-stu-id="41edd-125">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="41edd-126">Request メソッドが終了すると、応答メッセージを取得して読み取り、エンドポイントの応答内容を確認できます。</span><span class="sxs-lookup"><span data-stu-id="41edd-126">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="41edd-127">オブジェクトの終了</span><span class="sxs-lookup"><span data-stu-id="41edd-127">Closing Objects</span></span>  

 <span data-ttu-id="41edd-128">リソースのリークを避けるには、通信に使用したオブジェクトが不要になったら、これを終了します。</span><span class="sxs-lookup"><span data-stu-id="41edd-128">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="41edd-129">次のコード例に、メッセージを送信して応答を読み取るためにチャネル ファクトリを使用する基本的なクライアントを示します。</span><span class="sxs-lookup"><span data-stu-id="41edd-129">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]

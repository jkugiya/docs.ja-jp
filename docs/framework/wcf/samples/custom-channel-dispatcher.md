---
description: 詳細については、「カスタムチャネルディスパッチャー」を参照してください。
title: カスタム チャネル ディスパッチャー
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: cb56c21b540f359d78e71d8769e9f2d9ccf65a63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732593"
---
# <a name="custom-channel-dispatcher"></a><span data-ttu-id="f2159-103">カスタム チャネル ディスパッチャー</span><span class="sxs-lookup"><span data-stu-id="f2159-103">Custom Channel Dispatcher</span></span>

<span data-ttu-id="f2159-104">このサンプルでは、<xref:System.ServiceModel.ServiceHostBase> を直接実装することによって、カスタマイズした方法でチャネル スタックを作成する方法と、Web ホスト環境でカスタム チャネル ディスパッチャーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f2159-104">This sample demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span> <span data-ttu-id="f2159-105">チャネル ディスパッチャーは、<xref:System.ServiceModel.Channels.IChannelListener> と対話してチャネルを受け入れ、チャネル スタックからメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="f2159-105">The channel dispatcher interacts with <xref:System.ServiceModel.Channels.IChannelListener> to accept channels and retrieves messages from the channel stack.</span></span> <span data-ttu-id="f2159-106">このサンプルには、<xref:System.ServiceModel.Activation.VirtualPathExtension> を使用して Web ホスト環境でチャネル スタックを作成する方法を示す基本的なサンプルも用意されています。</span><span class="sxs-lookup"><span data-stu-id="f2159-106">This sample also provides a basic sample to show how to build a channel stack in a Web host environment by using <xref:System.ServiceModel.Activation.VirtualPathExtension>.</span></span>  
  
## <a name="custom-servicehostbase"></a><span data-ttu-id="f2159-107">カスタム ServiceHostBase</span><span class="sxs-lookup"><span data-stu-id="f2159-107">Custom ServiceHostBase</span></span>  

 <span data-ttu-id="f2159-108">このサンプルでは、ではなく基本型を実装し、 <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.ServiceHost> WINDOWS COMMUNICATION FOUNDATION (WCF) スタックの実装をチャネルスタック上のカスタムメッセージ処理レイヤーに置き換える方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f2159-108">This sample implements the base type <xref:System.ServiceModel.ServiceHostBase> instead of <xref:System.ServiceModel.ServiceHost> to demonstrate how to replace the Windows Communication Foundation (WCF) stack implementation with a custom message handling layer on top of the channel stack.</span></span> <span data-ttu-id="f2159-109">仮想メソッド <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> をオーバーライドして、チャネル リスナーとチャネル ディスパッチャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2159-109">You override the virtual method <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> to build channel listeners and the channel dispatcher.</span></span>  
  
 <span data-ttu-id="f2159-110">Web ホスト サービスを実装するには、サービス拡張 <xref:System.ServiceModel.Activation.VirtualPathExtension> を <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> コレクションから取得し、<xref:System.ServiceModel.Channels.BindingParameterCollection> に追加します。これにより、トランスポート層で、ホスト環境の設定 (つまり、インターネット インフォメーション サービス (IIS) および Windows プロセス アクティブ化サービス (WAS) の設定) に基づいてチャネル リスナーを構成する方法を認識できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f2159-110">To implement a Web-hosted service, get the service extension <xref:System.ServiceModel.Activation.VirtualPathExtension> from the <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> collection and add it to the <xref:System.ServiceModel.Channels.BindingParameterCollection> so that the transport layer knows how to configure the channel listener based on the hosting environment settings, that is, the Internet Information Services (IIS)/Windows Process Activation Service (WAS) settings.</span></span>  
  
## <a name="custom-channel-dispatcher"></a><span data-ttu-id="f2159-111">カスタム チャネル ディスパッチャー</span><span class="sxs-lookup"><span data-stu-id="f2159-111">Custom Channel Dispatcher</span></span>  

 <span data-ttu-id="f2159-112">カスタム チャネル ディスパッチャーは型 <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase> を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f2159-112">The custom channel dispatcher extends the type <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>.</span></span> <span data-ttu-id="f2159-113">この型はチャネル層のプログラミング ロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="f2159-113">This type implements the channel-layer programming logic.</span></span> <span data-ttu-id="f2159-114">このサンプルでは、要求/応答メッセージ交換パターンでサポートされるのは <xref:System.ServiceModel.Channels.IReplyChannel> だけですが、カスタム チャネル ディスパッチャーは他の種類のチャネルに簡単に拡張できます。</span><span class="sxs-lookup"><span data-stu-id="f2159-114">In this sample, only <xref:System.ServiceModel.Channels.IReplyChannel> is supported for request-reply message exchange pattern, but the custom channel dispatcher can be easily extended to other channel types.</span></span>  
  
 <span data-ttu-id="f2159-115">ディスパッチャーは、まずチャネル リスナーを開き、次にシングルトン応答チャネルを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="f2159-115">The dispatcher first opens the channel listener and then accepts the singleton reply channel.</span></span> <span data-ttu-id="f2159-116">このチャネルを使用して、無限ループでメッセージ (応答) の送信を開始します。</span><span class="sxs-lookup"><span data-stu-id="f2159-116">With the channel, it starts to send messages (requests) in an infinite loop.</span></span> <span data-ttu-id="f2159-117">要求ごとに、応答メッセージを作成し、クライアントに返信します。</span><span class="sxs-lookup"><span data-stu-id="f2159-117">For each request, it creates a reply message and sends it back to the client.</span></span>  
  
## <a name="creating-a-response-message"></a><span data-ttu-id="f2159-118">応答メッセージの作成</span><span class="sxs-lookup"><span data-stu-id="f2159-118">Creating a Response Message</span></span>  

 <span data-ttu-id="f2159-119">メッセージ処理は型 `MyServiceManager` で実装されます。</span><span class="sxs-lookup"><span data-stu-id="f2159-119">The message processing is implemented in the type `MyServiceManager`.</span></span> <span data-ttu-id="f2159-120">`HandleRequest` メソッドでは、要求がサポートされているかどうか確認するために、メッセージの `Action` ヘッダーが最初にチェックされます。</span><span class="sxs-lookup"><span data-stu-id="f2159-120">In the `HandleRequest` method, the `Action` header of the message is first checked to see whether the request is supported.</span></span> <span data-ttu-id="f2159-121">定義済みの SOAP アクション " http://tempuri.org/HelloWorld/Hello " は、メッセージのフィルター処理を提供するために定義されています。</span><span class="sxs-lookup"><span data-stu-id="f2159-121">A predefined SOAP action "http://tempuri.org/HelloWorld/Hello" is defined to provide message filtering.</span></span> <span data-ttu-id="f2159-122">これは、の WCF 実装でのサービスコントラクトの概念に似てい <xref:System.ServiceModel.ServiceHost> ます。</span><span class="sxs-lookup"><span data-stu-id="f2159-122">This is similar to the service contract concept in the WCF implementation of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="f2159-123">正しい SOAP アクションの場合、サンプルでは、<xref:System.ServiceModel.ServiceHost> の場合と同じように、要求されたメッセージ データを取得し、要求に対して対応する応答を生成します。</span><span class="sxs-lookup"><span data-stu-id="f2159-123">For the correct SOAP action case, the sample retrieves the requested message data and generates a corresponding response to the request similar to what is seen in the <xref:System.ServiceModel.ServiceHost> case.</span></span>  
  
 <span data-ttu-id="f2159-124">特に、この場合、正しくコンパイルされていることを確認するためにブラウザーからサービスを参照できるように、カスタム HTML メッセージを返して HTTP-GET 動詞を処理します。</span><span class="sxs-lookup"><span data-stu-id="f2159-124">You specially handled the HTTP-GET verb by returning a custom HTML message, in this, case so that you can browse the service from a browser to see that it is compiled correctly.</span></span> <span data-ttu-id="f2159-125">SOAP アクションが一致しない場合は、エラー メッセージを返信して、要求がサポートされていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="f2159-125">If the SOAP action does not match, send a fault message back to indicate that the request is not supported.</span></span>  
  
 <span data-ttu-id="f2159-126">このサンプルのクライアントは、サービスからのものを想定していない通常の WCF クライアントです。</span><span class="sxs-lookup"><span data-stu-id="f2159-126">The client of this sample is a normal WCF client that does not assume anything from the service.</span></span> <span data-ttu-id="f2159-127">そのため、サービスは、通常の WCF 実装から取得したものと一致するように特別に設計されてい <xref:System.ServiceModel.ServiceHost> ます。</span><span class="sxs-lookup"><span data-stu-id="f2159-127">So, the service is specially designed to match what you get from a normal WCF<xref:System.ServiceModel.ServiceHost> implementation.</span></span> <span data-ttu-id="f2159-128">したがって、クライアントに必要なのはサービス コントラクトだけです。</span><span class="sxs-lookup"><span data-stu-id="f2159-128">As a result, only a service contract is required on the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="f2159-129">サンプルの使用</span><span class="sxs-lookup"><span data-stu-id="f2159-129">Using the sample</span></span>  

 <span data-ttu-id="f2159-130">クライアント アプリケーションを直接実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f2159-130">Running the client application directly produces the following output.</span></span>  
  
```output  
Client is talking to a request/reply WCF service.
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 <span data-ttu-id="f2159-131">HTTP-GET メッセージがサーバーで処理されるように、ブラウザーからサービスを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="f2159-131">You can also browse the service from a browser so that an HTTP-GET message gets processed on the server.</span></span> <span data-ttu-id="f2159-132">この場合、適切に書式設定された HTML テキストが返信されます。</span><span class="sxs-lookup"><span data-stu-id="f2159-132">This gets you well-formatted HTML text back.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f2159-133">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f2159-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f2159-134">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f2159-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f2159-135">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="f2159-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f2159-136">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f2159-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`

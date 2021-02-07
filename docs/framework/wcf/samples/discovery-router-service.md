---
description: 詳細については、「探索ルーターサービス」を参照してください。
title: 探索ルーター サービス
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: f5fa4cd19758bef0b867fafc5af4b9cf6df27028
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726716"
---
# <a name="discovery-router-service"></a><span data-ttu-id="4e418-103">探索ルーター サービス</span><span class="sxs-lookup"><span data-stu-id="4e418-103">Discovery Router Service</span></span>

<span data-ttu-id="4e418-104">このサンプルでは、探索メッセージを別のエンドポイントに転送する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4e418-104">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4e418-105">対象</span><span class="sxs-lookup"><span data-stu-id="4e418-105">Demonstrates</span></span>  

 <span data-ttu-id="4e418-106">探索ルーティング</span><span class="sxs-lookup"><span data-stu-id="4e418-106">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4e418-107">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="4e418-107">Discussion</span></span>  

 <span data-ttu-id="4e418-108">探索ルーティングは、プロキシがサービスを認識しないが、別のプロキシのことは認識する場合に、クライアントがプロキシを使用してそのようなサービスを検索するシナリオで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="4e418-108">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="4e418-109">このプロキシは、探索パケットをこのクライアントから 2 番目のプロキシに転送できます。</span><span class="sxs-lookup"><span data-stu-id="4e418-109">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="4e418-110">2 番目のプロキシはサービスを検索し、応答を元のクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="4e418-110">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="4e418-111">このサンプルでは、クライアントはメッセージを探索ルーティング コンポーネントに送信します。</span><span class="sxs-lookup"><span data-stu-id="4e418-111">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="4e418-112">このメッセージは、探索ルーター上の特定のエンドポイントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="4e418-112">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="4e418-113">その後、このルーターはメッセージを UDP マルチキャスト エンドポイントに転送します。</span><span class="sxs-lookup"><span data-stu-id="4e418-113">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="4e418-114">プローブ メッセージはマルチキャスト エンドポイントに送信され、UDP マルチキャスト アドレスをリッスンするサービスは、その探索ルーターに応答します。</span><span class="sxs-lookup"><span data-stu-id="4e418-114">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="4e418-115">探索ルーターは応答を収集し、クライアントにその応答を返します。</span><span class="sxs-lookup"><span data-stu-id="4e418-115">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4e418-116">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="4e418-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4e418-117">サンプルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="4e418-117">Build the sample.</span></span>  
  
2. <span data-ttu-id="4e418-118">DiscoveryRouter 実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="4e418-118">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="4e418-119">ビルド ディレクトリからサービス実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="4e418-119">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="4e418-120">クライアント実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="4e418-120">Run the client executable.</span></span> <span data-ttu-id="4e418-121">クライアントでサービスが検索されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4e418-121">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4e418-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="4e418-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4e418-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4e418-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4e418-124">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="4e418-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e418-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4e418-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`

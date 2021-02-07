---
description: '詳細情報: Reliable Secure Profile'
title: Reliable Secure Profile
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: 6e9552b3a6e715f6eac6742f89b2e70a34f926a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703823"
---
# <a name="reliable-secure-profile"></a><span data-ttu-id="bd4d7-103">Reliable Secure Profile</span><span class="sxs-lookup"><span data-stu-id="bd4d7-103">Reliable Secure Profile</span></span>

<span data-ttu-id="bd4d7-104">このサンプルでは、WCF および [Reliable Secure Profile (RSP)](http://www.ws-i.org/Profiles/ReliableSecureProfile-1.0.html)を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-104">This sample demonstrates how to compose WCF and [Reliable Secure Profile (RSP)](http://www.ws-i.org/Profiles/ReliableSecureProfile-1.0.html).</span></span> <span data-ttu-id="bd4d7-105">このサンプルでは、信頼性の高いメッセージングと、必要に応じてセキュリティで保護されたチャネルを組み合わせることによって、RSP 仕様に基づく信頼性の高いセキュリティで保護されたバインディングを作成するための、 [Make 接続](http://docs.oasis-open.org/ws-rx/wsmc/200702/wsmc-1.0-spec-cs-01.pdf) チャネルの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-105">This sample demonstrates the implementation of a [Make Connection](http://docs.oasis-open.org/ws-rx/wsmc/200702/wsmc-1.0-spec-cs-01.pdf) channel, which can be composed together with Reliable Messaging and optionally a secure channel to create a Reliable Secure Binding based on the RSP specification.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bd4d7-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd4d7-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bd4d7-108">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd4d7-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a><span data-ttu-id="bd4d7-110">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="bd4d7-110">Discussion</span></span>  

 <span data-ttu-id="bd4d7-111">このサンプルでは、信頼できる非同期の双方向メッセージ交換シナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-111">This sample demonstrates a reliable asynchronous two-way message exchange scenario.</span></span> <span data-ttu-id="bd4d7-112">サービスには双方向コントラクトがあり、クライアントには双方向コールバック コントラクトが実装されます。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-112">The service has a duplex contract and the client implements the duplex callback contract.</span></span> <span data-ttu-id="bd4d7-113">クライアントからサービスに対して要求が開始され、要求に対しては個別の接続で応答する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-113">The client initiates a request to a service, for which a response is expected on a separate connection.</span></span> <span data-ttu-id="bd4d7-114">要求メッセージは信頼できる方法で送信されます。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-114">The request message is sent reliably.</span></span> <span data-ttu-id="bd4d7-115">クライアントでは、終端にある待機エンドポイントを開きません。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-115">The client does not want to open a listening endpoint at its end.</span></span> <span data-ttu-id="bd4d7-116">したがって、クライアントは "Make Connection" 要求を使用してサービスをポーリングし、サービスはこの "Make Connection" 要求のバック チャネルで応答を返信します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-116">Thus, it polls the service with ‘Make Connection’ requests for the service to send back the response on the back channel of this ‘Make Connection’ request.</span></span> <span data-ttu-id="bd4d7-117">このサンプルでは、クライアントで待機エンドポイントを公開せずに (また、ファイアウォールの例外を設けずに)、HTTP を介してセキュリティで保護された信頼できる双方向通信を実現する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-117">This sample demonstrates how to have secure reliable duplex communication over HTTP without the client exposing a listening endpoint (and creating a firewall exception).</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bd4d7-118">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="bd4d7-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bd4d7-119">**ReliableSecureProfile** ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-119">Open the **ReliableSecureProfile** solution.</span></span>  
  
2. <span data-ttu-id="bd4d7-120">**ソリューションエクスプローラー** で **サービス** プロジェクトを右クリックし、コンテキストメニューの [**デバッグ**]、[**新しいインスタンスを開始**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-120">Right click the **Service** project in **Solution Explorer**, select **Debug**, **Start new instance** from the context menu.</span></span> <span data-ttu-id="bd4d7-121">サービス ホストが開始されます。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-121">This starts up the service host.</span></span>  
  
3. <span data-ttu-id="bd4d7-122">**ソリューションエクスプローラー** で **クライアント** プロジェクトを右クリックし、コンテキストメニューの [**デバッグ**]、[**新しいインスタンスを開始**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-122">Right click the **Client** project in **Solution Explorer**, select **Debug**, **Start new instance** from the context menu.</span></span> <span data-ttu-id="bd4d7-123">クライアントが開始されます。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-123">This starts up the client.</span></span>  
  
4. <span data-ttu-id="bd4d7-124">クライアント コンソール ウィンドウのプロンプトに任意の文字列を入力し、Enter キーを押します。入力文字列がサービスに送信され、この文字列のハッシュが計算されます。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-124">Type in any string in the prompt on the client console window and click ENTER.This sends the input string to the service, which computes a hash of this string.</span></span>  
  
5. <span data-ttu-id="bd4d7-125">クライアント コンソール ウィンドウに結果を表示するためにサービスから双方向コールバック コントラクト操作がコールバックされたら、クライアント ウィンドウで結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-125">View the result on the client windows when the service calls back the duplex callback contract operation to display the result on the client console window.</span></span> <span data-ttu-id="bd4d7-126">実行に時間のかかるデータ処理操作を再現するために、サービスからの応答は意図的に遅延されます。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-126">There is an intentional delay on the service to simulate a long running operation of processing the data.</span></span>  
  
6. <span data-ttu-id="bd4d7-127">HTTP トラフィックの監視 (ネットワーク モニター、Fiddler などのオンライン ネットワーク監視ツールを使用) により、Reliable Secure Profile で規定されているように通信のシーケンスがクライアントとサービスの間で確立されていること、およびどのようにクライアントが "Make Connection" 要求を使用してサービスをポーリングしているかが示されます。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-127">Monitoring the HTTP traffic (by any of the online network monitoring tools like Network Monitor, Fiddler and so on) shows that a sequence for communication is established between the client and the service as laid down by the Reliable Secure Profile, and how the client polls the service with ‘Make Connection’ requests.</span></span> <span data-ttu-id="bd4d7-128">サービスでは、処理した応答を返信できる状態になると、最後の "Make Connection" 要求のバック チャネルを使用して、結果を返信します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-128">When the service gets ready to send back the processed response, it uses the back channel of the last ‘Make Connection’ request to send back the results.</span></span>  
  
7. <span data-ttu-id="bd4d7-129">サービス コンソール ウィンドウで Enter キーを押してサービスを終了します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-129">Press ENTER on the service console window to close the service.</span></span> <span data-ttu-id="bd4d7-130">クライアント コンソール ウィンドウで Enter キーを押してクライアントを終了します。</span><span class="sxs-lookup"><span data-stu-id="bd4d7-130">Press ENTER on the client console window to close the client.</span></span>

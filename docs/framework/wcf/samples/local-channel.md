---
description: '詳細情報: ローカルチャネル'
title: ローカル チャネル
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: a580abc1e8dcd89c40c9fdc02001deb094eb0b05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631750"
---
# <a name="local-channel"></a><span data-ttu-id="398a3-103">ローカル チャネル</span><span class="sxs-lookup"><span data-stu-id="398a3-103">Local Channel</span></span>

<span data-ttu-id="398a3-104">ローカルチャネルは、同じアプリケーションドメイン内の通信に使用される Windows Communication Foundation (WCF) トランスポートチャネルです。</span><span class="sxs-lookup"><span data-stu-id="398a3-104">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="398a3-105">これは、クライアントとサービスが同じアプリケーション ドメイン内で実行されており、通常の WCF チャネル スタックのオーバーヘッド (メッセージのシリアル化と逆シリアル化) を回避する必要がある場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="398a3-105">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="398a3-106">対象</span><span class="sxs-lookup"><span data-stu-id="398a3-106">Demonstrates</span></span>  

 <span data-ttu-id="398a3-107">ローカル チャネル</span><span class="sxs-lookup"><span data-stu-id="398a3-107">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="398a3-108">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="398a3-108">Discussion</span></span>  

 <span data-ttu-id="398a3-109">このサンプルは、2 つのプロジェクト ファイルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="398a3-109">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="398a3-110">**Localchannel**: 現在のアプリケーションドメイン内のローカルチャネルのプログラムによる表現。</span><span class="sxs-lookup"><span data-stu-id="398a3-110">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="398a3-111">このプロジェクトでは、送信側コンポーネントがメッセージをメモリ内キューに入れて、受信側コンポーネントがメッセージをキューから削除して受信します。</span><span class="sxs-lookup"><span data-stu-id="398a3-111">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="398a3-112">**Clientandservice**: このプロジェクトは、コンソールアプリケーションでサービスをホストし、クライアントを実行して、同じアプリケーションドメイン内からサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="398a3-112">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="398a3-113">ローカル チャネルのデザインでは、速度を上げるためにチャネル スタックとシリアル化プロセスの両方がスキップされます。</span><span class="sxs-lookup"><span data-stu-id="398a3-113">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="398a3-114">ローカル トランスポート チャネルは、キューを使用してサービス呼び出しをクライアントからサービスに転送し、値をクライアントに返すことによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="398a3-114">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="398a3-115">このサンプルでは、パラメーターと戻り値をシリアル化するのではなく、オブジェクトをコピーします。</span><span class="sxs-lookup"><span data-stu-id="398a3-115">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="398a3-116">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="398a3-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="398a3-117">LocalChannel ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="398a3-117">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="398a3-118">サービス ホストが起動し、クライアントがローカル チャネルを使用してサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="398a3-118">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="398a3-119">コンソール ウィンドウが表示され、サービス呼び出しの結果が示されます。</span><span class="sxs-lookup"><span data-stu-id="398a3-119">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="398a3-120">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="398a3-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="398a3-121">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="398a3-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="398a3-122">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="398a3-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="398a3-123">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="398a3-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`

---
description: '詳細情報: ConcurrencyMode リエントラント'
title: ConcurrencyMode 再入
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: f423722d87a8ab9567e0631afbb6bff68fd22b7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778517"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="356d4-103">ConcurrencyMode 再入</span><span class="sxs-lookup"><span data-stu-id="356d4-103">ConcurrencyMode Reentrant</span></span>

<span data-ttu-id="356d4-104">このサンプルでは、サービス実装で ConcurrencyMode.Reentrant を使用する必要性と影響を示します。</span><span class="sxs-lookup"><span data-stu-id="356d4-104">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="356d4-105">ConcurrencyMode.Reentrant は、サービス (またはコールバック) が指定された時間で処理するメッセージが 1 つだけであることを示します (`ConcurencyMode.Single` に似ています)。</span><span class="sxs-lookup"><span data-stu-id="356d4-105">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="356d4-106">スレッドセーフを確保するために、Windows Communication Foundation (WCF) は、メッセージの処理をロックして、 `InstanceContext` 他のメッセージを処理できないようにします。</span><span class="sxs-lookup"><span data-stu-id="356d4-106">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="356d4-107">再入モードの場合、サービスが呼び出しの送信を行う直前に `InstanceContext` のロックが解除されます。これによりその後の呼び出しが可能になり (サンプルに示すように再入可能になり)、次回サービスに呼び出しが届いたときにロックされます。</span><span class="sxs-lookup"><span data-stu-id="356d4-107">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="356d4-108">この動作を示すために、サンプルでは、クライアントとサービスが双方向コントラクトを使用してメッセージを相互に送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="356d4-108">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="356d4-109">定義されているコントラクトは双方向コントラクトで、サービスによって実装される `Ping` メソッドと、クライアントによって実装されるコールバック メソッド `Pong` を含みます。</span><span class="sxs-lookup"><span data-stu-id="356d4-109">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="356d4-110">クライアントは、サーバーの `Ping` メソッドを呼び出します。このメソッドには、呼び出しを初期化するチック カウントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="356d4-110">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="356d4-111">サービスはチック カウントが 0 でないことを確認し、チック カウントをデクリメントしながらコールバックの `Pong` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="356d4-111">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="356d4-112">これは、サンプルの次のコードによって行います。</span><span class="sxs-lookup"><span data-stu-id="356d4-112">This is done by the following code in the sample.</span></span>  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 コールバックの `Pong` 実装のロジックは、`Ping` 実装のロジックと同じです。 つまり、このメソッドはチック カウントが 0 でないことを確認し、その後コールバック チャネル (この場合は、元の `Ping` メッセージの送信に使用されたチャネル) の `Ping` メソッドを呼び出し、チック カウントを 1 だけデクリメントします。 チック カウントが 0 になると、このメソッドは返されます。これによってすべての応答のラップが解除され、クライアントが呼び出して初期化した最初の呼び出しに戻されます。 <span data-ttu-id="356d4-116">これを、コールバック実装で示します。</span><span class="sxs-lookup"><span data-stu-id="356d4-116">This is shown in the callback implementation.</span></span>  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 `Ping` メソッドと `Pong` メソッドはどちらも要求/応答です。つまり、`Ping` の最初の呼び出しは、`CallbackChannel<T>.Pong()` の呼び出しが返される以前には返されません。 クライアントでは、`Pong` メソッドは、このメソッドを返す次の `Ping` 呼び出しが返される以前には返されません。 <span data-ttu-id="356d4-119">コールバックとサービスはどちらも、保留中の要求に対して応答できるように、あらかじめ要求/応答の呼び出しを送信する必要があるので、どちらの実装も ConcurrencyMode.Reentrant 動作でマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="356d4-119">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="356d4-120">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="356d4-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="356d4-121">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="356d4-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="356d4-122">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="356d4-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="356d4-123">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="356d4-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="356d4-124">対象</span><span class="sxs-lookup"><span data-stu-id="356d4-124">Demonstrates</span></span>  

 <span data-ttu-id="356d4-125">サンプルを実行するには、クライアント プロジェクトとサーバー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="356d4-125">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="356d4-126">次に、2つのコマンドウィンドウを開き、ディレクトリを変更して、ディレクトリを変更し \<sample> \<sample> ます。</span><span class="sxs-lookup"><span data-stu-id="356d4-126">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="356d4-127">次に、「」と入力してサービスを開始し `service.exe` ます。次に、入力引数として渡されたタイマー刻みの初期値を使用して Client.exe を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="356d4-127">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="356d4-128">サンプルでは、チックとして 10 が出力されます。</span><span class="sxs-lookup"><span data-stu-id="356d4-128">A sample output for 10 ticks is shown.</span></span>  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="356d4-129">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="356d4-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="356d4-130">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="356d4-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="356d4-131">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="356d4-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="356d4-132">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="356d4-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  

---
description: '詳細情報: 予想される例外'
title: 予期される例外
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 9ccb857da76143a37ed520f2fac8c515b332a565
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752406"
---
# <a name="expected-exceptions"></a><span data-ttu-id="a8e1d-103">予期される例外</span><span class="sxs-lookup"><span data-stu-id="a8e1d-103">Expected Exceptions</span></span>

<span data-ttu-id="a8e1d-104">このサンプルでは、型指定のあるクライアントを使用する際に、予期される例外をキャッチする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-104">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="a8e1d-105">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="a8e1d-106">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-106">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8e1d-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a8e1d-108">このサンプルでは、正しいプログラムが処理する必要のある `TimeoutException` および `CommunicationException` という 2 種類の予期される例外を、キャッチして処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-108">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="a8e1d-109">Windows Communication Foundation (WCF) クライアントの通信メソッドからスローされた例外は、予期されているか、予期していません。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-109">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="a8e1d-110">予期しない例外には、`OutOfMemoryException` などの致命的なエラーや、`ArgumentNullException` や `InvalidOperationException` などのプログラミング エラーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-110">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="a8e1d-111">通常、予期しないエラーを処理するための便利な方法はありません。そのため、WCF クライアントの通信方法を呼び出すときには、通常はこれらをキャッチしないでください。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-111">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="a8e1d-112">WCF クライアントの通信メソッドからの予期される例外には `TimeoutException` 、、 `CommunicationException` 、およびの任意の派生クラスが含ま `CommunicationException` れます。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-112">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="a8e1d-113">これらは、WCF クライアントを中止して通信エラーを報告することによって安全に処理できる通信中に問題を示します。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-113">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="a8e1d-114">どのアプリケーションでも外部要因によってこうしたエラーが発生する可能性があるので、正しいアプリケーションはこのようなエラーをキャッチし、発生した場合には回復させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-114">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="a8e1d-115">`CommunicationException` の派生クラスには、クライアントがスローできるものがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-115">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="a8e1d-116">状況によっては、アプリケーションでこれらのサブクラスをキャッチして特別な処理を行うこともできます。しかし、それ以外の場合は `CommunicationException` として処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-116">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="a8e1d-117">この処理は、より具体的な例外の種類を最初にキャッチし、後の catch 句で `CommunicationException` をキャッチすることによって実現できます。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-117">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="a8e1d-118">クライアントの通信メソッドを呼び出すコードでは、`TimeoutException` と `CommunicationException` をキャッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-118">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="a8e1d-119">こうしたエラーの処理方法の 1 つに、クライアントを中止して通信エラーを報告するという方法があります。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-119">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="a8e1d-120">予期される例外が発生した場合、それ以降、クライアントを使用できる場合もできない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-120">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="a8e1d-121">クライアントがそのまま使用可能かどうかを確認するには、`State` プロパティが `CommunicationState`.Opened であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-121">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="a8e1d-122">Opened の場合は、そのまま使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-122">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="a8e1d-123">それ以外の場合は、クライアントを中止してすべての参照を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-123">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="a8e1d-124">一般に、セッションを持つクライアントは、例外発生後に使用できなくなり、セッションを持たないクライアントは、例外発生後も使用可能なままです。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-124">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="a8e1d-125">ただし、どちらも必ずそうなるとは限りません。したがって、例外発生後も引き続きクライアントを使用する場合は、アプリケーションで `State` プロパティをチェックし、クライアントが Opened 状態のままであることを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-125">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="a8e1d-126">このサンプルを実行すると、操作応答と例外がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="a8e1d-127">クライアント プロセスでは 2 つのシナリオが実行されます。各シナリオでは、`Add`、`Divide` の順に呼び出しが試行されます。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-127">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="a8e1d-128">最初のシナリオでは、`Divide` を呼び出す前にクライアントを中止することによってネットワーク問題をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-128">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="a8e1d-129">2 番目のシナリオでは、メソッドを完了できないようにタイムアウト値をごく短く設定することによって、タイムアウトを発生させます。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-129">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="a8e1d-130">クライアント プロセスから予期される出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-130">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a8e1d-131">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="a8e1d-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a8e1d-132">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a8e1d-133">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a8e1d-134">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8e1d-135">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a8e1d-136">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a8e1d-137">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8e1d-138">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a8e1d-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  

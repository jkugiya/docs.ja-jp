---
description: '詳細情報: インスタンス化'
title: インスタンス化
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 88cff6912e3285370a456d5d8575c995ff15ef57
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726456"
---
# <a name="instancing"></a><span data-ttu-id="404e2-103">インスタンス化</span><span class="sxs-lookup"><span data-stu-id="404e2-103">Instancing</span></span>

<span data-ttu-id="404e2-104">インスタンス化のサンプルでは、インスタンス化動作の設定を示します。この設定は、クライアント要求への応答として作成される、サービス クラスのインスタンスの作成方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="404e2-104">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="404e2-105">このサンプルは、サービスコントラクトを実装する [はじめに](getting-started-sample.md)に基づいてい `ICalculator` ます。</span><span class="sxs-lookup"><span data-stu-id="404e2-105">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="404e2-106">このサンプルでは、`ICalculatorInstance` から継承される新しいコントラクト `ICalculator` を定義します。</span><span class="sxs-lookup"><span data-stu-id="404e2-106">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="404e2-107">`ICalculatorInstance` によって指定されるコントラクトにより、サービス インスタンスの状態を検査するための 3 つの操作が追加されます。</span><span class="sxs-lookup"><span data-stu-id="404e2-107">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="404e2-108">インスタンス化設定を変更することにより、クライアントを実行して動作の変更を確認できます。</span><span class="sxs-lookup"><span data-stu-id="404e2-108">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="404e2-109">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="404e2-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="404e2-110">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="404e2-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="404e2-111">次のインスタンス化モードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="404e2-111">The following instancing modes are available:</span></span>  
  
- <span data-ttu-id="404e2-112"><xref:System.ServiceModel.InstanceContextMode.PerCall> : 新しいサービス インスタンスがクライアント要求ごとに作成されます。</span><span class="sxs-lookup"><span data-stu-id="404e2-112"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
- <span data-ttu-id="404e2-113"><xref:System.ServiceModel.InstanceContextMode.PerSession> : 新しいインスタンスが新しいクライアント セッションごとに作成され、そのセッションの有効期間中保持されます (セッションをサポートするバインディングが必要です)。</span><span class="sxs-lookup"><span data-stu-id="404e2-113"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
- <span data-ttu-id="404e2-114"><xref:System.ServiceModel.InstanceContextMode.Single> : アプリケーションの有効期間中、サービス クラスの単一のインスタンスがすべてのクライアント要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="404e2-114"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="404e2-115">サービス クラスは、`[ServiceBehavior(InstanceContextMode=<setting>)]` 属性を使用してインスタンス化動作を指定します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="404e2-115">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="404e2-116">コメント化されている行を変更すると、各インスタンス モードの動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="404e2-116">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="404e2-117">インスタンス モードを変更したら、サービスを再ビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="404e2-117">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="404e2-118">クライアントでは、インスタンス化に関連する設定は行いません。</span><span class="sxs-lookup"><span data-stu-id="404e2-118">There are no instancing-related settings to specify on the client.</span></span>  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="404e2-119">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="404e2-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="404e2-120">サービスで実行されているインスタンス モードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="404e2-120">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="404e2-121">各操作後に、インスタンス モードの動作が反映されたインスタンス ID と操作数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="404e2-121">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="404e2-122">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="404e2-122">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="404e2-123">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="404e2-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="404e2-124">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="404e2-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="404e2-125">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="404e2-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="404e2-126">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="404e2-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="404e2-127">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="404e2-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="404e2-128">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="404e2-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="404e2-129">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="404e2-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="404e2-130">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="404e2-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  

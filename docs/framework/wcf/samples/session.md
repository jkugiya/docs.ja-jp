---
description: '詳細情報: セッション'
title: セッション
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: ba8d2d44d0be22243bd1562f9bd499d68a1112af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793026"
---
# <a name="session"></a><span data-ttu-id="6572f-103">セッション</span><span class="sxs-lookup"><span data-stu-id="6572f-103">Session</span></span>

<span data-ttu-id="6572f-104">このセッションのサンプルでは、セッションを必要とするコントラクトを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6572f-104">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="6572f-105">セッションは、複数の操作を実行するためのコンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="6572f-105">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="6572f-106">これにより、サービスは特定のセッションに状態を関連付けることができ、後続の操作はその前の操作の状態を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6572f-106">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="6572f-107">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="6572f-107">This sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="6572f-108">`ICalculator` コントラクトは、一連の算術演算を実行して実行結果を保持できるように変更されました。</span><span class="sxs-lookup"><span data-stu-id="6572f-108">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="6572f-109">この機能は `ICalculatorSession` コントラクトによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="6572f-109">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="6572f-110">サービスは、複数のサービス操作が呼び出されて計算を実行する際に、クライアントの状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="6572f-110">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="6572f-111">クライアントは `Result()` を呼び出して現在の結果を取得したり、`Clear()` を呼び出してその結果をクリアし、0 にすることができます。</span><span class="sxs-lookup"><span data-stu-id="6572f-111">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="6572f-112">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="6572f-112">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6572f-113">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6572f-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6572f-114">コントラクトの <xref:System.ServiceModel.SessionMode> を `Required` に設定すると、コントラクトが特定のバインディングを介して公開される場合に、そのバインディングはセッションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6572f-114">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="6572f-115">バインディングがセッションをサポートしない場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6572f-115">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="6572f-116">`ICalculatorSession` インターフェイスは、1 つまたは複数の操作が呼び出されるように定義されており、これによって実行結果が変更されます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6572f-116">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="6572f-117">サービスは、<xref:System.ServiceModel.InstanceContextMode> の <xref:System.ServiceModel.InstanceContextMode.PerSession> を使用して、指定されたサービス インスタンスのコンテキストを各入力セッションにバインドします。</span><span class="sxs-lookup"><span data-stu-id="6572f-117">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="6572f-118">これにより、サービスは、ローカルのメンバ変数内に各セッションの実行結果を保持できます。</span><span class="sxs-lookup"><span data-stu-id="6572f-118">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 <span data-ttu-id="6572f-119">このサンプルを実行すると、クライアントはサーバーに対していくつかの要求を行い、その後、その要求がクライアント コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6572f-119">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="6572f-120">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6572f-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6572f-121">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="6572f-121">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6572f-122">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="6572f-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6572f-123">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6572f-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6572f-124">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6572f-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6572f-125">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6572f-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6572f-126">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6572f-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6572f-127">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="6572f-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6572f-128">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6572f-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  

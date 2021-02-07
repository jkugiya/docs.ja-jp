---
description: 詳細については、「WS トランザクションフロー」を参照してください。
title: WS トランザクション フロー
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 4d0a0af77dd516bf98c5dc8318ac110a31e731e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668371"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="ea499-103">WS トランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="ea499-103">WS Transaction Flow</span></span>

<span data-ttu-id="ea499-104">このサンプルでは、クライアントによって調整されるトランザクションの使用方法と、WS-AtomicTransaction プロトコルまたは OleTransactions プロトコルを使用するトランザクション フローに関するクライアントとサーバーのオプションの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ea499-104">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="ea499-105">このサンプルは、電卓サービスを実装する[はじめに](getting-started-sample.md)に基づいていますが、操作には、TransactionFlowOption 列挙でを使用して、 `TransactionFlowAttribute` どの程度トランザクションフローが有効になっているかを判断する方法が示されています。 </span><span class="sxs-lookup"><span data-stu-id="ea499-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="ea499-106">フローされたトランザクションのスコープ内では、要求された操作のログがデータベースに書き込まれ、クライアント調整トランザクションが完了するまで保持されます。クライアント トランザクションが完了しない場合は、データベースに対する該当する更新はコミットされません。</span><span class="sxs-lookup"><span data-stu-id="ea499-106">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea499-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea499-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ea499-108">サービスとトランザクションへの接続を開始した後で、クライアントは複数のサービス操作にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ea499-108">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="ea499-109">サービスのコントラクトは次のように定義されています。操作はそれぞれ、`TransactionFlowOption` の設定が異なります。</span><span class="sxs-lookup"><span data-stu-id="ea499-109">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);
}  
```

 <span data-ttu-id="ea499-110">操作は、処理される順に次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ea499-110">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="ea499-111">`Add` (加算) 操作要求には、フローされたトランザクションが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea499-111">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="ea499-112">`Subtract` (減算) 操作要求には、フローされたトランザクションが含まれていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="ea499-112">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="ea499-113">`Multiply` (乗算) 操作要求には、フローされたトランザクションが含まれてはならないことが、明示的な NotAllowed 設定で指定されています。</span><span class="sxs-lookup"><span data-stu-id="ea499-113">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="ea499-114">`Divide` (除算) 操作要求には、フローされたトランザクションが含まれてはならないことが、`TransactionFlow` 属性の省略によって指定されています。</span><span class="sxs-lookup"><span data-stu-id="ea499-114">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="ea499-115">トランザクションフローを有効にするには、 [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) 適切な操作属性に加えて、プロパティが有効になっているバインドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea499-115">To enable transaction flow, bindings with the [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="ea499-116">このサンプルでは、サービスの構成は Metadata Exchange エンドポイントのほかに TCP エンドポイントと HTTP エンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="ea499-116">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="ea499-117">TCP エンドポイントと HTTP エンドポイントは、次のバインディングを使用します。どちらのバインディングでも、 [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) プロパティが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="ea499-117">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
> <span data-ttu-id="ea499-118">システムで提供される netTcpBinding では transactionProtocol を指定できるのに対し、システムで提供される wsHttpBinding では、相互運用性に優れた WSAtomicTransactionOctober2004 プロトコルのみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-118">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="ea499-119">OleTransactions プロトコルは、Windows Communication Foundation (WCF) クライアントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea499-119">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="ea499-120">`ICalculator` インターフェイスを実装するクラスでは、すべてのメソッドの属性で <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> プロパティが `true` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="ea499-120">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="ea499-121">この設定は、メソッド内で実行されるすべてのアクションがトランザクションのスコープ内で実行されることを宣言するものです。</span><span class="sxs-lookup"><span data-stu-id="ea499-121">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="ea499-122">この場合、実行されるアクションには、ログ データベースへの記録が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ea499-122">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="ea499-123">操作要求の中に、フローされたトランザクションが含まれている場合は、受信トランザクションのスコープ内でアクションが実行されるか、新しいトランザクションが自動生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-123">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea499-124"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> プロパティは、サービス メソッド実装固有の動作を定義しますが、トランザクションをフローさせるためのクライアントの機能や要件は定義しません。</span><span class="sxs-lookup"><span data-stu-id="ea499-124">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 <span data-ttu-id="ea499-125">クライアントでは、操作に対するサービスの `TransactionFlowOption` 設定が、クライアントで生成される `ICalculator` インターフェイスの定義に反映されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-125">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="ea499-126">さらに、サービスの `transactionFlow` プロパティの設定はクライアントのアプリケーション構成に反映されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-126">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="ea499-127">クライアントでは、適切な `endpointConfigurationName` を選択することによってトランスポートとプロトコルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ea499-127">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="ea499-128">このサンプルを実行したときの動作は、選択したプロトコルとトランスポートの種類にかかわらず同一です。</span><span class="sxs-lookup"><span data-stu-id="ea499-128">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="ea499-129">サービスへの接続を開始した後で、クライアントは次のように、サービス操作の呼び出しを囲む新しい `TransactionScope` を作成します。</span><span class="sxs-lookup"><span data-stu-id="ea499-129">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 <span data-ttu-id="ea499-130">操作の呼び出しは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ea499-130">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="ea499-131">`Add` 要求によって、必須のトランザクションがサービスにフローされ、サービスのアクションはクライアントのトランザクション スコープ内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-131">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="ea499-132">最初の `Subtract` 要求も、許可されたトランザクションをサービスにフローするので、このときもサービスのアクションはクライアントのトランザクション スコープ内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-132">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="ea499-133">2 番目の `Subtract` 要求は、`TransactionScopeOption.Suppress` オプションと共に宣言された新しいトランザクション スコープ内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-133">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="ea499-134">これによって、クライアントの最初の外側トランザクションが抑制されます。また、新しいトランザクションがサービスにフローされることはありません。</span><span class="sxs-lookup"><span data-stu-id="ea499-134">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="ea499-135">この方法を使用すると、クライアントは、トランザクションをサービスにフローすることが必要ない場合に、このことを行わないように明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="ea499-135">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="ea499-136">サービスのアクションは、新しい独立したトランザクションのスコープ内で発生します。</span><span class="sxs-lookup"><span data-stu-id="ea499-136">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="ea499-137">`Multiply` 要求はトランザクションをサービスにフローしません。クライアントで生成された `ICalculator` インターフェイスの定義には <xref:System.ServiceModel.TransactionFlowAttribute><xref:System.ServiceModel.TransactionFlowOption> に設定された `NotAllowed` が含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="ea499-137">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="ea499-138">`Divide` 要求は、トランザクションをサービスにフローしません。同様に、クライアントで生成された `ICalculator` インターフェイスの定義には `TransactionFlowAttribute` が含まれていないためです。</span><span class="sxs-lookup"><span data-stu-id="ea499-138">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="ea499-139">このときも、サービスのアクションは別の新しい独立したトランザクションのスコープ内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-139">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="ea499-140">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-140">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ea499-141">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ea499-141">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="ea499-142">サービス操作要求のログ記録は、サービスのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-142">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="ea499-143">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ea499-143">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="ea499-144">実行が正常に終了すると、クライアントのトランザクション スコープが完了し、そのスコープ内で実行されたすべてのアクションがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="ea499-144">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="ea499-145">具体的には、ここに示した 5 レコードがサービスのデータベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-145">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="ea499-146">最初の 2 レコードは、クライアントのトランザクションのスコープ内で発生しています。</span><span class="sxs-lookup"><span data-stu-id="ea499-146">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="ea499-147">クライアントの `TransactionScope` 内の場所で例外が発生した場合、トランザクションは完了しません。</span><span class="sxs-lookup"><span data-stu-id="ea499-147">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="ea499-148">その結果、そのスコープ内でログに記録されたレコードはデータベースにコミットされなくなります。</span><span class="sxs-lookup"><span data-stu-id="ea499-148">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="ea499-149">この影響を確認するには、外側の `TransactionScope` を完了させる呼び出しをコメント化した後にサンプルをもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="ea499-149">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="ea499-150">この実行では、最後の 3 つのアクション (2 番目の `Subtract` 要求、`Multiply` 要求、`Divide` 要求) だけがログに記録されます。クライアント トランザクションはこれらのアクションにフローしないためです。</span><span class="sxs-lookup"><span data-stu-id="ea499-150">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ea499-151">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="ea499-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ea499-152">ソリューションの C# または Visual Basic .NET バージョンをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ea499-152">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="ea499-153">SQL Server Express Edition または SQL Server がインストールされ、接続文字列が、サービスのアプリケーション構成ファイルで正しく設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ea499-153">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="ea499-154">データベースを使用せずにサンプルを実行するには、サービスのアプリケーション構成ファイルで `usingSql` の値を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="ea499-154">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="ea499-155">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ea499-155">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ea499-156">複数コンピューター構成の場合は、次の説明に従って分散トランザクション コーディネーターを有効にし、Windows SDK の WsatConfig.exe ツールを使用して WCF トランザクション ネットワークのサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ea499-156">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="ea499-157">WsatConfig.exe の設定の詳細については、「 [WS-Atomic トランザクションサポートの構成](../feature-details/configuring-ws-atomic-transaction-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea499-157">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="ea499-158">サンプルを同じコンピューターで実行するか、別のコンピューターで実行するかにかかわらず、ネットワークトランザクションフローを有効にするために Microsoft 分散トランザクションコーディネーター (MSDTC) を構成し、WsatConfig.exe ツールを使用して WCF トランザクションネットワークサポートを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea499-158">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="ea499-159">Microsoft 分散トランザクション コーディネーター (MSDTC) を構成してサンプルを実行できるようにするには</span><span class="sxs-lookup"><span data-stu-id="ea499-159">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="ea499-160">Windows Server 2003 または Windows XP が動作するサービス コンピューターで、次の説明に従い、受信ネットワーク トランザクションを許可するよう MSDTC を構成します。</span><span class="sxs-lookup"><span data-stu-id="ea499-160">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="ea499-161">[ **スタート** ] メニューから、[ **コントロールパネル**]、[ **管理ツール**]、[ **コンポーネントサービス**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="ea499-161">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="ea499-162">[ **コンポーネントサービス**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="ea499-162">Expand **Component Services**.</span></span> <span data-ttu-id="ea499-163">[ **コンピューター** ] フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ea499-163">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="ea499-164">**マイコンピューター** を右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea499-164">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="ea499-165">[ **MSDTC** ] タブで、[ **セキュリティの構成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea499-165">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="ea499-166">**ネットワーク DTC アクセス** を確認し、**受信を許可** します。</span><span class="sxs-lookup"><span data-stu-id="ea499-166">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="ea499-167">[ **OK**] をクリックし、[ **はい** ] をクリックして MSDTC サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="ea499-167">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="ea499-168">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ea499-168">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="ea499-169">Windows Server 2008 または Windows Vista が動作するサービス コンピューターで、次の説明に従い、受信ネットワーク トランザクションを許可するよう MSDTC を構成します。</span><span class="sxs-lookup"><span data-stu-id="ea499-169">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="ea499-170">[ **スタート** ] メニューから、[ **コントロールパネル**]、[ **管理ツール**]、[ **コンポーネントサービス**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="ea499-170">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="ea499-171">[ **コンポーネントサービス**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="ea499-171">Expand **Component Services**.</span></span> <span data-ttu-id="ea499-172">[ **コンピューター** ] フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ea499-172">Open the **Computers** folder.</span></span> <span data-ttu-id="ea499-173">[ **分散トランザクションコーディネーター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea499-173">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="ea499-174">[ **DTC コーディネーター** ] を右クリックし、[ **プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea499-174">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="ea499-175">[ **セキュリティ** ] タブで、[ **ネットワーク DTC アクセス** と **受信を許可する**] をオンにします。</span><span class="sxs-lookup"><span data-stu-id="ea499-175">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="ea499-176">[ **OK**] をクリックし、[ **はい** ] をクリックして MSDTC サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="ea499-176">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="ea499-177">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ea499-177">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="ea499-178">クライアント コンピューターで、送信ネットワーク トランザクションを許可するよう MSDTC を構成します。</span><span class="sxs-lookup"><span data-stu-id="ea499-178">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="ea499-179">[ **スタート** ] メニューから、 `Control Panel` [ **管理ツール**]、[ **コンポーネントサービス**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="ea499-179">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="ea499-180">**マイコンピューター** を右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea499-180">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="ea499-181">[ **MSDTC** ] タブで、[ **セキュリティの構成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea499-181">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="ea499-182">**ネットワーク DTC アクセス** を確認し、**送信を許可** します。</span><span class="sxs-lookup"><span data-stu-id="ea499-182">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="ea499-183">[ **OK**] をクリックし、[ **はい** ] をクリックして MSDTC サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="ea499-183">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="ea499-184">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ea499-184">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ea499-185">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="ea499-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ea499-186">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ea499-186">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ea499-187">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="ea499-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ea499-188">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ea499-188">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`

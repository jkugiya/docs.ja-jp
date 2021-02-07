---
description: '詳細については、次を参照してください: Transport: UDP 経由のカスタムトランザクションサンプル'
title: 'トランスポート : UDP 経由のカスタム トランザクションのサンプル'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: 609576c74a8a3c0cd55829335545818028d444bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668514"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="0cbd9-103">トランスポート : UDP 経由のカスタム トランザクションのサンプル</span><span class="sxs-lookup"><span data-stu-id="0cbd9-103">Transport: Custom Transactions over UDP Sample</span></span>

<span data-ttu-id="0cbd9-104">このサンプルは、Windows Communication Foundation (WCF)[トランスポート拡張](transport-extensibility.md)における[transport: UDP](transport-udp.md)サンプルを基にしています。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-104">This sample is based on the [Transport: UDP](transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](transport-extensibility.md).</span></span> <span data-ttu-id="0cbd9-105">ここでは、カスタム トランザクション フローをサポートするように UDP トランスポートのサンプルを拡張し、<xref:System.ServiceModel.Channels.TransactionMessageProperty> プロパティの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-105">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="0cbd9-106">UDP トランスポート サンプルのコードの変更</span><span class="sxs-lookup"><span data-stu-id="0cbd9-106">Code Changes in the UDP Transport Sample</span></span>  

 <span data-ttu-id="0cbd9-107">トランザクション フローを示すため、サンプルでは、`ICalculatorContract` のサービス コントラクトが `CalculatorService.Add()` のトランザクション スコープを要求するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-107">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="0cbd9-108">また、サンプルでは、別の `System.Guid` パラメータを `Add` 操作のコントラクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-108">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="0cbd9-109">このパラメータは、クライアント トランザクションの識別子をサービスに渡すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-109">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```csharp  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="0cbd9-110">[Transport: udp](transport-udp.md)サンプルでは、udp パケットを使用して、クライアントとサービスの間でメッセージを受け渡します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-110">The [Transport: UDP](transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="0cbd9-111">[トランスポート: カスタムトランスポートのサンプル](transport-custom-transactions-over-udp-sample.md)では、同じメカニズムを使用してメッセージを転送しますが、トランザクションがフローされるときには、エンコードされたメッセージと共に UDP パケットに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-111">The [Transport: Custom Transport Sample](transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="0cbd9-112">`TransactionMessageBuffer.WriteTransactionMessageBuffer` は、メッセージ エンティティを使用して現在のトランザクションの反映トークンをマージし、それをバッファに配置する新しい機能を持つヘルパー メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-112">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="0cbd9-113">カスタムトランザクションフロートランスポートの場合、クライアントの実装では、トランザクションフローが必要なサービス操作を認識し、この情報を WCF に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-113">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="0cbd9-114">また、ユーザー トランザクションをトランスポート層に転送するための機構もあります。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-114">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="0cbd9-115">このサンプルでは、"WCF メッセージインスペクター" を使用してこの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-115">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="0cbd9-116">ここで実装されるクライアント メッセージ インスペクタは `TransactionFlowInspector` と呼ばれ、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-116">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="0cbd9-117">指定されたメッセージ アクションに対してトランザクションをフローする必要があるかどうかを判断します (これは `IsTxFlowRequiredForThisOperation()` で行われます)。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-117">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="0cbd9-118">トランザクションをフローする必要がある場合、`TransactionFlowProperty` を使用して現在のアンビエント トランザクションをメッセージにアタッチします (これは `BeforeSendRequest()` で行われます)。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-118">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```csharp  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="0cbd9-119">`TransactionFlowInspector` 自体は、カスタム動作 `TransactionFlowBehavior` を使用してフレームワークに渡されます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-119">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```csharp  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="0cbd9-120">上記の機構を使用して、ユーザー コードは、サービス操作を呼び出す前に `TransactionScope` を作成します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-120">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="0cbd9-121">メッセージ インスペクタは、トランザクションをサービス操作にフローする必要がある場合に、トランザクションがトランスポートに渡されるようにします。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-121">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```csharp  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="0cbd9-122">クライアントから UDP パケットを受け取ると、サービスはこれを逆シリアル化して、メッセージとトランザクション (可能な場合) を抽出します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-122">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="0cbd9-123">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` は、`TransactionMessageBuffer.WriteTransactionMessageBuffer()` によって行われたシリアル化プロセスを元に戻すヘルパー メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-123">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="0cbd9-124">トランザクションがフローされた場合、トランザクションは `TransactionMessageProperty` のメッセージに追加されます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-124">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="0cbd9-125">これにより、ディスパッチャはディスパッチ時にトランザクションを取得し、メッセージによってアドレス指定されたサービス操作を呼び出すときにそのトランザクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-125">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0cbd9-126">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="0cbd9-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0cbd9-127">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-127">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="0cbd9-128">現在のサンプルは、 [Transport: UDP](transport-udp.md) サンプルと同様に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-128">The current sample should be run similarly to the [Transport: UDP](transport-udp.md) sample.</span></span> <span data-ttu-id="0cbd9-129">実行するには、UdpTestService.exe を使用してサービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-129">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="0cbd9-130">Windows Vista を実行している場合は、昇格された特権でサービスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-130">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="0cbd9-131">これを行うには、エクスプローラーで UdpTestService.exe を右クリックし、[ **管理者として実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-131">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="0cbd9-132">これによって次の文字列が出力されます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-132">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="0cbd9-133">この時点で、UdpTestClient.exe を実行してクライアントを開始できます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-133">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="0cbd9-134">クライアントによって生成される出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-134">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="0cbd9-135">サービスの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-135">The service output is as follows.</span></span>  
  
    ```console
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6. <span data-ttu-id="0cbd9-136">`The client transaction has flowed to the service` 操作の `clientTransactionId` パラメータで、クライアントによって送信されたトランザクション識別子がサービス トランザクションの識別子と一致する場合、サービス アプリケーションには、"`CalculatorService.Add()`" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-136">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="0cbd9-137">クライアント トランザクションがサービスにフローされた場合にのみ、一致が取得されます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-137">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="0cbd9-138">構成を使用して公開されたエンドポイントに対してクライアント アプリケーションを実行するには、サービス側のアプリケーション ウィンドウで Enter キーを押して、テスト クライアントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-138">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="0cbd9-139">サービスには、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-139">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="0cbd9-140">サービスに対してクライアントを実行すると、前の出力と同様の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-140">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="0cbd9-141">Svcutil.exe を使用してクライアント コードと構成を再生成するには、サービス アプリケーションを開始し、次にサンプルのルート ディレクトリで次のように Svcutil.exe コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-141">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="0cbd9-142">Svcutil.exe を実行しても `sampleProfileUdpBinding` のバインディング拡張構成は生成されません。したがって、次のコードを手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-142">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="0cbd9-143">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0cbd9-144">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0cbd9-145">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0cbd9-146">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0cbd9-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="0cbd9-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cbd9-147">See also</span></span>

- [<span data-ttu-id="0cbd9-148">トランスポート:UDP</span><span class="sxs-lookup"><span data-stu-id="0cbd9-148">Transport: UDP</span></span>](transport-udp.md)

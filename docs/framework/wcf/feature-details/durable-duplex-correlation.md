---
description: '詳細情報: 永続的な二重の相関関係'
title: 永続的な二重の相関関係
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: e30356e03ccb6f8fae7ca735d2ad674bbe2a191d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704954"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="cec13-103">永続的な二重の相関関係</span><span class="sxs-lookup"><span data-stu-id="cec13-103">Durable Duplex Correlation</span></span>

<span data-ttu-id="cec13-104">永続的な二重の相関関係 (コールバック相関関係) は、ワークフロー サービスがコールバックを最初の呼び出し元に送信する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cec13-104">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="cec13-105">WCF の二重とは異なり、コールバックは、将来のどの時点でも発生する可能性があり、同じチャネルにも同じチャネルの有効期間にも関連付けられていません。唯一の要件は、呼び出し元にコールバック メッセージをリッスンするアクティブなエンドポイントを用意することです。</span><span class="sxs-lookup"><span data-stu-id="cec13-105">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="cec13-106">このため、2 つのワークフロー サービスが長時間のメッセージ交換を使用して通信できます。</span><span class="sxs-lookup"><span data-stu-id="cec13-106">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="cec13-107">このトピックでは、永続的な二重の相関関係について概説します。</span><span class="sxs-lookup"><span data-stu-id="cec13-107">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="cec13-108">永続的な二重の相関関係の使用</span><span class="sxs-lookup"><span data-stu-id="cec13-108">Using Durable Duplex Correlation</span></span>  

 <span data-ttu-id="cec13-109">永続的な二重の相関関係を使用するには、2 つのサービスが、<xref:System.ServiceModel.NetTcpContextBinding> や <xref:System.ServiceModel.WSHttpContextBinding> など、双方向の操作をサポートするコンテキスト対応バインドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cec13-109">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="cec13-110">呼び出し側サービスは、クライアントの <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> で使用するバインドを指定して <xref:System.ServiceModel.Endpoint> を登録します。</span><span class="sxs-lookup"><span data-stu-id="cec13-110">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="cec13-111">受信側サービスは、このデータを最初の呼び出しで受信し、呼び出し側サービスへのコールバックを行う <xref:System.ServiceModel.Endpoint> アクティビティにおいて、受信側サービス自体の <xref:System.ServiceModel.Activities.Send> でこのデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="cec13-111">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="cec13-112">次の例では、2 つのサービスが互いに通信しています。</span><span class="sxs-lookup"><span data-stu-id="cec13-112">In this example, two services communicate with each other.</span></span> <span data-ttu-id="cec13-113">1 つ目のサービスは、2 つ目のサービスに対してメソッドを呼び出し、応答を待機します。</span><span class="sxs-lookup"><span data-stu-id="cec13-113">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="cec13-114">2 つ目のサービスでは、コールバック メソッドの名前が認識されていますが、このメソッドを実装するサービスのエンドポイントは、設計時には認識されていません。</span><span class="sxs-lookup"><span data-stu-id="cec13-114">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cec13-115">エンドポイントの <xref:System.ServiceModel.Channels.AddressingVersion> が <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A> で構成される場合は、永続的な二重のみが使用できます。</span><span class="sxs-lookup"><span data-stu-id="cec13-115">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="cec13-116">そうでない場合は、 <xref:System.InvalidOperationException> 次のメッセージと共に例外がスローされます。 "メッセージには、 [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing)のエンドポイント参照を含むコールバックコンテキストヘッダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cec13-116">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="cec13-117">コールバックコンテキストは、AddressingVersion が ' WSAddressing10 ' で構成されている場合にのみ送信できます。</span><span class="sxs-lookup"><span data-stu-id="cec13-117">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="cec13-118">次の例では、<xref:System.ServiceModel.Endpoint> を使用してコールバック <xref:System.ServiceModel.WSHttpContextBinding> を作成するワークフロー サービスがホストされます。</span><span class="sxs-lookup"><span data-stu-id="cec13-118">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 <span data-ttu-id="cec13-119">このワークフロー サービスを実装するワークフローは、ワークフロー自体の <xref:System.ServiceModel.Activities.Send> アクティビティを使用してコールバック相関関係を初期化し、<xref:System.ServiceModel.Activities.Receive> と相関関係にある <xref:System.ServiceModel.Activities.Send> アクティビティからこのコールバック エンドポイントを参照します。</span><span class="sxs-lookup"><span data-stu-id="cec13-119">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="cec13-120">次の例は、`GetWF1` メソッドから返されるワークフローです。</span><span class="sxs-lookup"><span data-stu-id="cec13-120">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="cec13-121">2 つ目のワークフロー サービスは、システムが提供するコンテキスト ベースのバインドを使用してホストされます。</span><span class="sxs-lookup"><span data-stu-id="cec13-121">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 <span data-ttu-id="cec13-122">このワークフロー サービスを実装するワークフローは、<xref:System.ServiceModel.Activities.Receive> アクティビティから開始されます。</span><span class="sxs-lookup"><span data-stu-id="cec13-122">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="cec13-123">この受信アクティビティは、このサービスのコールバック相関関係を初期化し、一定の遅延時間を設けて長時間の作業をシミュレーションして、サービスへの最初の呼び出しで渡されたコールバック コンテキストを使用して、最初のサービスにコールバックします。</span><span class="sxs-lookup"><span data-stu-id="cec13-123">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="cec13-124">次の例は、`GetWF2` への呼び出しから返されるワークフローです。</span><span class="sxs-lookup"><span data-stu-id="cec13-124">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="cec13-125"><xref:System.ServiceModel.Activities.Send> アクティビティには、`http://www.contoso.com` のプレースホルダー アドレスが設定されていることに注意してください。実行時に使用される実際のアドレスは、指定されたコールバック アドレスです。</span><span class="sxs-lookup"><span data-stu-id="cec13-125">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="cec13-126">`StartOrder` メソッドが最初のワークフローで呼び出されると、次の出力が表示されます。これは、2 つのワークフローの実行フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="cec13-126">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
```output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 <span data-ttu-id="cec13-127">この例では、どちらのワークフローも <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> を使用して相関関係を明示的に管理しています。</span><span class="sxs-lookup"><span data-stu-id="cec13-127">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="cec13-128">サンプル ワークフローには相関関係が 1 つしかないため、既定の <xref:System.ServiceModel.Activities.CorrelationHandle> で十分に管理できます。</span><span class="sxs-lookup"><span data-stu-id="cec13-128">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>

---
description: '詳細情報: カスタムメッセージフィルター'
title: カスタム メッセージ フィルター
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 41205badf4d1133dc160fb0b1c4da8e0edb47a16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752484"
---
# <a name="custom-message-filter"></a><span data-ttu-id="ad56a-103">カスタム メッセージ フィルター</span><span class="sxs-lookup"><span data-stu-id="ad56a-103">Custom Message Filter</span></span>

<span data-ttu-id="ad56a-104">このサンプルでは、Windows Communication Foundation (WCF) がメッセージをエンドポイントにディスパッチするために使用するメッセージフィルターを置き換える方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ad56a-104">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad56a-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad56a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ad56a-106">チャネルでの最初のメッセージがサーバーに到着すると、サーバーは、URI に関連付けられているエンドポイントがある場合に、どのエンドポイントがメッセージを受信する必要があるかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad56a-106">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="ad56a-107">この処理は、<xref:System.ServiceModel.Dispatcher.MessageFilter> に関連付けられている <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> オブジェクトで制御されます。</span><span class="sxs-lookup"><span data-stu-id="ad56a-107">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="ad56a-108">サービスの各エンドポイントには、単一の <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> があります。</span><span class="sxs-lookup"><span data-stu-id="ad56a-108">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="ad56a-109"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher> には、<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> と <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> の両方があります。</span><span class="sxs-lookup"><span data-stu-id="ad56a-109">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="ad56a-110">これら 2 つのフィルタを結合したものが、このエンドポイントに使用されるメッセージ フィルタです。</span><span class="sxs-lookup"><span data-stu-id="ad56a-110">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="ad56a-111">エンドポイントの <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> の既定では、アドレス指定されているメッセージと、サービス エンドポイントの <xref:System.ServiceModel.EndpointAddress> に一致するアドレスを照合します。</span><span class="sxs-lookup"><span data-stu-id="ad56a-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="ad56a-112">既定では、 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> エンドポイントのは、受信メッセージのアクションを検査し、サービスエンドポイントコントラクトの操作のいずれかのアクションに対応するアクションと一致する任意のメッセージを照合し `IsInitiating` = `true` ます (アクションだけが考慮されます)。</span><span class="sxs-lookup"><span data-stu-id="ad56a-112">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="ad56a-113">その結果、エンドポイントのフィルタの既定で一致と見なされるのは、メッセージの To ヘッダーがエンドポイントの <xref:System.ServiceModel.EndpointAddress> に一致し、メッセージのアクションがエンドポイントの操作のいずれかのアクションと一致するという、2 つの条件がどちらも満たされる場合だけです。</span><span class="sxs-lookup"><span data-stu-id="ad56a-113">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="ad56a-114">これらのフィルタは、動作を使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="ad56a-114">These filters can be changed using a behavior.</span></span> <span data-ttu-id="ad56a-115">サンプルのサービスは、次のように <xref:System.ServiceModel.Description.IEndpointBehavior> を作成して、<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> の <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> と <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ad56a-115">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 <span data-ttu-id="ad56a-116">2 つのアドレス フィルタは、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ad56a-116">Two address filters are defined:</span></span>  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 <span data-ttu-id="ad56a-117">`FilteringEndpointBehavior` は構成可能になり、2 つの異なるバリエーションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="ad56a-117">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 <span data-ttu-id="ad56a-118">バリエーション 1 では 'e' が含まれる (ただし任意のアクションを含む) アドレスのみを照合します。これに対して、バリエーション 2 では 'e' が含まれないアドレスのみを照合します。</span><span class="sxs-lookup"><span data-stu-id="ad56a-118">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="ad56a-119">構成ファイルでは、サービスは次のように新しい動作を登録します。</span><span class="sxs-lookup"><span data-stu-id="ad56a-119">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 <span data-ttu-id="ad56a-120">次に、各バリエーションの `endpointBehavior` 構成を次のように作成します。</span><span class="sxs-lookup"><span data-stu-id="ad56a-120">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 <span data-ttu-id="ad56a-121">最後に、サービスのエンドポイントは、`behaviorConfigurations` の 1 つを次のように参照します。</span><span class="sxs-lookup"><span data-stu-id="ad56a-121">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="ad56a-122">クライアント アプリケーションの実装は単純で、URI の値を 2 番目の (`via`) パラメータとして <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> に渡すことによって、2 つのチャネルをサービスの URI に作成し、各チャネルに 1 つのメッセージを送信します。ただし、チャネルごとに異なるエンドポイント アドレスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ad56a-122">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="ad56a-123">この結果、次のクライアントの出力に示すように、クライアントからの送信メッセージにはそれぞれ異なる宛先が指定され、サーバーはこれに応じて応答します。</span><span class="sxs-lookup"><span data-stu-id="ad56a-123">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="ad56a-124">サーバーの構成ファイルのバリエーションを切り替えると、フィルターが入れ替わり、クライアントには逆の動作が表示されます (`urn:e` へのメッセージは正常に送信されますが、`urn:a` へのメッセージはエラーになります)。</span><span class="sxs-lookup"><span data-stu-id="ad56a-124">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="ad56a-125">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="ad56a-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ad56a-126">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ad56a-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ad56a-127">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="ad56a-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ad56a-128">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ad56a-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ad56a-129">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="ad56a-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ad56a-130">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ad56a-130">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="ad56a-131">サンプルを単一コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ad56a-131">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ad56a-132">複数コンピューター構成でサンプルを実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md) 」の手順に従って、Client.cs の次の行を変更します。</span><span class="sxs-lookup"><span data-stu-id="ad56a-132">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="ad56a-133">つまり、localhost をサーバー名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ad56a-133">Replace localhost with the name of server.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  

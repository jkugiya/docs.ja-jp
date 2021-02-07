---
description: 詳細については、NetHttpBinding の使用に関するページを参照してください。
title: NetHttpBinding の使用
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 3964c3c3e563d143df1edfcd1f98d3250301c209
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756046"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="2cad1-103">NetHttpBinding の使用</span><span class="sxs-lookup"><span data-stu-id="2cad1-103">Using the NetHttpBinding</span></span>

<span data-ttu-id="2cad1-104"><xref:System.ServiceModel.NetHttpBinding> は、HTTP や WebSocket のサービスを使用するために設計されたバインドで、既定ではバイナリ エンコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="2cad1-104"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="2cad1-105"><xref:System.ServiceModel.NetHttpBinding> は、要求-応答コントラクトと二重のコントラクトのどちらで使用されているかを検出し、一致するように動作を変更します。要求-応答コントラクトには HTTP、二重のコントラクトには Websocket を使用します。</span><span class="sxs-lookup"><span data-stu-id="2cad1-105"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="2cad1-106">この動作は、<xref:System.ServiceModel.Channels.WebSocketTransportUsage> 設定を使用してオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="2cad1-106">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="2cad1-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> -これにより、要求/応答コントラクトでも Websocket が強制的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="2cad1-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="2cad1-108"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> -Websocket が使用されないようにします。</span><span class="sxs-lookup"><span data-stu-id="2cad1-108"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> - This prevents WebSockets from being used.</span></span> <span data-ttu-id="2cad1-109">この設定で二重のコントラクトを使用しようとすると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="2cad1-109">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="2cad1-110"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> -これは既定値で、前述のように動作します。</span><span class="sxs-lookup"><span data-stu-id="2cad1-110"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="2cad1-111"><xref:System.ServiceModel.NetHttpBinding> は、HTTP モードと WebSocket モードの両方で信頼できるセッションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2cad1-111"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="2cad1-112">WebSocket モードでは、セッションがトランスポートによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="2cad1-112">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2cad1-113"><xref:System.ServiceModel.NetHttpBinding> を使用していて、バインドの TransferMode が TransferMode.Streamed に設定されている場合、大きいストリームによってデッドロックが発生する可能性があり、呼び出しがタイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="2cad1-113">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="2cad1-114">この問題を回避するには、小さいメッセージを送信するか、TransferMode.Buffered を使用してください。</span><span class="sxs-lookup"><span data-stu-id="2cad1-114">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="2cad1-115">NetHttpBinding を使用するサービスの構成</span><span class="sxs-lookup"><span data-stu-id="2cad1-115">Configuring a Service to use NetHttpBinding</span></span>  

 <span data-ttu-id="2cad1-116"><xref:System.ServiceModel.NetHttpBinding> は、他のバインドと同様に構成できます。</span><span class="sxs-lookup"><span data-stu-id="2cad1-116">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="2cad1-117">次の構成スニペットは、<xref:System.ServiceModel.NetHttpBinding> を使用して WCF サービスを構成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2cad1-117">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 <span data-ttu-id="2cad1-118">次のコード スニペットは、コードで <xref:System.ServiceModel.NetHttpBinding> を追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2cad1-118">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cad1-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cad1-119">See also</span></span>

- [<span data-ttu-id="2cad1-120">サービスのバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="2cad1-120">Configuring Bindings for Services</span></span>](../configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="2cad1-121">バインド</span><span class="sxs-lookup"><span data-stu-id="2cad1-121">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="2cad1-122">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="2cad1-122">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="2cad1-123">双方向サービス</span><span class="sxs-lookup"><span data-stu-id="2cad1-123">Duplex Services</span></span>](duplex-services.md)

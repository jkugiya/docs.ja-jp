---
title: 負荷分散
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: ccb915c33be217d2a8d00a54c5bd57384286140f
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548098"
---
# <a name="load-balancing"></a><span data-ttu-id="10298-102">負荷分散</span><span class="sxs-lookup"><span data-stu-id="10298-102">Load Balancing</span></span>

<span data-ttu-id="10298-103">Windows Communication Foundation (WCF) アプリケーションの容量を増やす方法の1つは、負荷分散されたサーバーファームに配置することによってスケールアウトすることです。</span><span class="sxs-lookup"><span data-stu-id="10298-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="10298-104">WCF アプリケーションは、Windows ネットワーク負荷分散やハードウェアベースの負荷分散アプライアンスなどのソフトウェアロードバランサーを含む、標準的な負荷分散手法を使用して負荷分散することができます。</span><span class="sxs-lookup"><span data-stu-id="10298-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="10298-105">以下のセクションでは、さまざまなシステム指定のバインディングを使用して構築された WCF アプリケーションの負荷分散に関する考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="10298-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="10298-106">基本 HTTP バインディングによる負荷分散</span><span class="sxs-lookup"><span data-stu-id="10298-106">Load Balancing with the Basic HTTP Binding</span></span>  

 <span data-ttu-id="10298-107">負荷分散の観点から見ると、を使用して通信する WCF アプリケーション <xref:System.ServiceModel.BasicHttpBinding> は、他の一般的な種類の HTTP ネットワークトラフィック (静的な HTML コンテンツ、ASP.NET ページ、または ASMX Web サービス) とは異なります。</span><span class="sxs-lookup"><span data-stu-id="10298-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="10298-108">このバインディングを使用する WCF チャネルは本質的にステートレスであり、チャネルが閉じられると接続を終了します。</span><span class="sxs-lookup"><span data-stu-id="10298-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="10298-109">したがって、<xref:System.ServiceModel.BasicHttpBinding> には既存の HTTP 負荷分散の手法で十分に対応できます。</span><span class="sxs-lookup"><span data-stu-id="10298-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="10298-110">既定では、<xref:System.ServiceModel.BasicHttpBinding> は、メッセージの接続 HTTP ヘッダーで `Keep-Alive` 値を送信することで、サポートするサービスにクライアントが永続的な接続を確立できるようにします。</span><span class="sxs-lookup"><span data-stu-id="10298-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="10298-111">この構成では、以前に確立した接続を再使用して同じサーバーへの後続するメッセージを送信できるため、スループットが向上します。</span><span class="sxs-lookup"><span data-stu-id="10298-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="10298-112">ただし、接続を再使用すると、クライアントが負荷分散ファーム内の特定サーバーと強く関連付けられてしまうため、ラウンドロビン方式の負荷分散の効果を損ねることがあります。</span><span class="sxs-lookup"><span data-stu-id="10298-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="10298-113">これを回避するには、`Keep-Alive` またはユーザー定義の <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> で <xref:System.ServiceModel.Channels.CustomBinding> プロパティを使用して、サーバーの HTTP <xref:System.ServiceModel.Channels.Binding> を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="10298-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="10298-114">構成を使用してこれを行う例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="10298-114">The following example shows how to do this using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="10298-115">.NET Framework 4 で導入された簡略化された構成を使用すると、次の簡略化された構成を使用して同じ動作を実現できます。</span><span class="sxs-lookup"><span data-stu-id="10298-115">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="10298-116">既定のエンドポイントについては、「[Simplified Configuration](simplified-configuration.md)」 (簡易構成) と「[Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md)」 (WCF サービスの簡易構成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10298-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="10298-117">WSHttp バインディングおよび WSDualHttp バインディングによる負荷分散</span><span class="sxs-lookup"><span data-stu-id="10298-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  

 <span data-ttu-id="10298-118"><xref:System.ServiceModel.WSHttpBinding> と <xref:System.ServiceModel.WSDualHttpBinding> はどちらも、既定のバインド構成をいくつか変更すれば、HTTP の負荷分散手法を使用して負荷分散できます。</span><span class="sxs-lookup"><span data-stu-id="10298-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="10298-119">セキュリティコンテキストの確立を無効にするか、ステートフルなセキュリティセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="10298-119">Turn off Security Context Establishment or use stateful security sessions.</span></span> <span data-ttu-id="10298-120">セキュリティコンテキストの確立は、のプロパティをに設定することによって無効にすることができ <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> <xref:System.ServiceModel.WSHttpBinding> `false` ます。</span><span class="sxs-lookup"><span data-stu-id="10298-120">Security Context Establishment can be turned off by setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="10298-121">またはのセキュリティセッションを使用している場合は <xref:System.ServiceModel.WSDualHttpBinding> 、「セキュリティで [保護されたセッション](./feature-details/secure-sessions.md)」で説明されているように、ステートフルなセキュリティセッションを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="10298-121">If you are using <xref:System.ServiceModel.WSDualHttpBinding> or security sessions are required, it is possible to use stateful security sessions as described in [Secure Sessions](./feature-details/secure-sessions.md).</span></span> <span data-ttu-id="10298-122">ステートフルなセキュリティセッションを使用すると、セキュリティセッションのすべての状態が保護セキュリティトークンの一部として各要求と共に送信されるため、サービスをステートレスな状態に保つことができます。</span><span class="sxs-lookup"><span data-stu-id="10298-122">Stateful security sessions enable the service to remain stateless, as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="10298-123">ステートフルなセキュリティセッションを有効にするには、またはユーザー定義を使用する必要があります。これは、 <xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.Binding> 必要な構成設定がシステムに用意されているおよびでは公開されないため <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSDualHttpBinding> です。</span><span class="sxs-lookup"><span data-stu-id="10298-123">To enable a stateful security session, you must use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>, as the necessary configuration settings are not exposed on the system-provided <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding>.</span></span>

- <span data-ttu-id="10298-124">セキュリティコンテキストの確立を無効にした場合は、サービス資格情報のネゴシエーションを無効にする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="10298-124">If you turn off Security Context Establishment, you also need to turn off Service Credential Negotiation.</span></span> <span data-ttu-id="10298-125">オフにするに <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential> は、のプロパティ <xref:System.ServiceModel.WSHttpBinding> をに設定し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="10298-125">To turn it off, set the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="10298-126">サービス資格情報のネゴシエーションを無効にするには、クライアントでエンドポイント id を明示的に指定する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="10298-126">To disable Service Credential Negotiation, you may need to explicitly specify the endpoint identity on the client.</span></span>
  
- <span data-ttu-id="10298-127">信頼できるセッションを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="10298-127">Do not use reliable sessions.</span></span> <span data-ttu-id="10298-128">この機能は既定では無効です。</span><span class="sxs-lookup"><span data-stu-id="10298-128">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="10298-129">Net.TCP バインディングの負荷分散</span><span class="sxs-lookup"><span data-stu-id="10298-129">Load Balancing the Net.TCP Binding</span></span>  

 <span data-ttu-id="10298-130"><xref:System.ServiceModel.NetTcpBinding> は、IP レイヤー負荷分散の手法を使用して負荷分散できます。</span><span class="sxs-lookup"><span data-stu-id="10298-130">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="10298-131">ただし、<xref:System.ServiceModel.NetTcpBinding> は接続の待ち時間を減らすために、既定で TCP 接続のプールを作成します。</span><span class="sxs-lookup"><span data-stu-id="10298-131">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="10298-132">この最適化は、負荷分散の基本的なメカニズムに干渉します。</span><span class="sxs-lookup"><span data-stu-id="10298-132">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="10298-133"><xref:System.ServiceModel.NetTcpBinding> を最適化するための主な構成値はリース タイムアウトで、これは接続プール設定の一部です。</span><span class="sxs-lookup"><span data-stu-id="10298-133">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="10298-134">接続プールによって、クライアントの接続がファーム内の特定サーバーと関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="10298-134">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="10298-135">このような接続の有効期間 (これはリース タイムアウトの設定で制御される要素です) が長くなるにつれて、ファーム内の各サーバーの負荷分散がうまくいかなくなります。</span><span class="sxs-lookup"><span data-stu-id="10298-135">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="10298-136">その結果、平均呼び出し時間が増加します。</span><span class="sxs-lookup"><span data-stu-id="10298-136">As a result the average call time increases.</span></span> <span data-ttu-id="10298-137">したがって、<xref:System.ServiceModel.NetTcpBinding> を負荷分散シナリオで使用する場合は、バインディングによって使用される既定のリース タイムアウトを少なくすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="10298-137">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="10298-138">負荷分散のシナリオでは、30 秒のリース タイムアウトから始めるのが合理的ですが、最適値はアプリケーションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="10298-138">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="10298-139">チャネルのリースタイムアウトおよびその他のトランスポートクォータの詳細については、「 [トランスポートクォータ](./feature-details/transport-quotas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10298-139">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="10298-140">負荷分散のシナリオで最適なパフォーマンスを実現するには、<xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> または <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>) を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="10298-140">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10298-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="10298-141">See also</span></span>

- [<span data-ttu-id="10298-142">インターネット インフォメーション サービス ホスティングのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="10298-142">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)

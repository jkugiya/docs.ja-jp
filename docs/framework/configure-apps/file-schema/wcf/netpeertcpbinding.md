---
description: '詳細情報: <netPeerTcpBinding>'
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 11f1618236c7219143225e2535e272254af6b81d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683906"
---
# \<netPeerTcpBinding>

<span data-ttu-id="4aaa3-102">ピア チャネル固有の TCP メッセージングのバインディングを定義します。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="4aaa3-103">構文</span><span class="sxs-lookup"><span data-stu-id="4aaa3-103">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding name="string"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           listenIPAddress="String"
           maxBufferPoolSize="integer"
           maxReceiveMessageSize="Integer"
           port="Integer">
    <security mode="None/Transport/Message/TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4aaa3-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4aaa3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="4aaa3-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4aaa3-106">属性</span><span class="sxs-lookup"><span data-stu-id="4aaa3-106">Attributes</span></span>  
  
|<span data-ttu-id="4aaa3-107">属性</span><span class="sxs-lookup"><span data-stu-id="4aaa3-107">Attribute</span></span>|<span data-ttu-id="4aaa3-108">説明</span><span class="sxs-lookup"><span data-stu-id="4aaa3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4aaa3-109">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="4aaa3-109">closeTimeout</span></span>|<span data-ttu-id="4aaa3-110">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4aaa3-111">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4aaa3-112">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-112">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4aaa3-113">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="4aaa3-113">listenIPAddress</span></span>|<span data-ttu-id="4aaa3-114">ピア ノードが TCP メッセージをリッスンする IP アドレスを指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-114">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="4aaa3-115">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-115">The default is `null`.</span></span>|  
|<span data-ttu-id="4aaa3-116">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4aaa3-116">maxBufferPoolSize</span></span>|<span data-ttu-id="4aaa3-117">このバインディングに使用するバッファー プール サイズの上限を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-117">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="4aaa3-118">既定は 524,288 バイト (512 \* 1024) です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="4aaa3-119">Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="4aaa3-120">使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4aaa3-121">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4aaa3-122">これで、バッファーの作成と破棄のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="4aaa3-123">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4aaa3-123">maxReceivedMessageSize</span></span>|<span data-ttu-id="4aaa3-124">このバインディングで構成されるチャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) をバイト単位で指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-124">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="4aaa3-125">この制限を超えるメッセージの送信者が、SOAP エラーを受信します。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-125">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="4aaa3-126">メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-126">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4aaa3-127">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-127">The default is 65536.</span></span>|  
|<span data-ttu-id="4aaa3-128">name</span><span class="sxs-lookup"><span data-stu-id="4aaa3-128">name</span></span>|<span data-ttu-id="4aaa3-129">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-129">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4aaa3-130">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-130">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4aaa3-131">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-131">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4aaa3-132">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-132">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="4aaa3-133">openTimeout</span><span class="sxs-lookup"><span data-stu-id="4aaa3-133">openTimeout</span></span>|<span data-ttu-id="4aaa3-134">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4aaa3-135">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4aaa3-136">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-136">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4aaa3-137">port</span><span class="sxs-lookup"><span data-stu-id="4aaa3-137">port</span></span>|<span data-ttu-id="4aaa3-138">このバインディングがピア チャネルの TCP メッセージを処理するネットワーク インターフェイス ポートを指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-138">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="4aaa3-139">この値の有効値の範囲は <xref:System.Net.IPEndPoint.MinPort> ～ <xref:System.Net.IPEndPoint.MaxPort> です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-139">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="4aaa3-140">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-140">The default is 0.</span></span>|  
|<span data-ttu-id="4aaa3-141">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="4aaa3-141">receiveTimeout</span></span>|<span data-ttu-id="4aaa3-142">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-142">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4aaa3-143">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-143">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4aaa3-144">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-144">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="4aaa3-145">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="4aaa3-145">sendTimeout</span></span>|<span data-ttu-id="4aaa3-146">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4aaa3-147">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4aaa3-148">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-148">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4aaa3-149">子要素</span><span class="sxs-lookup"><span data-stu-id="4aaa3-149">Child Elements</span></span>  
  
|<span data-ttu-id="4aaa3-150">要素</span><span class="sxs-lookup"><span data-stu-id="4aaa3-150">Element</span></span>|<span data-ttu-id="4aaa3-151">説明</span><span class="sxs-lookup"><span data-stu-id="4aaa3-151">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="4aaa3-152">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-152">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4aaa3-153">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-153">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="4aaa3-154">ピア メッシュ ID を解決してピア メッシュ内のノードのエンドポイント ID アドレスを取得するために、このバインディングによって使用されるピア リゾルバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-154">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="4aaa3-155">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-155">Defines the security settings for the message.</span></span> <span data-ttu-id="4aaa3-156">この要素は <xref:System.ServiceModel.Configuration.PeerSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-156">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4aaa3-157">親要素</span><span class="sxs-lookup"><span data-stu-id="4aaa3-157">Parent Elements</span></span>  
  
|<span data-ttu-id="4aaa3-158">要素</span><span class="sxs-lookup"><span data-stu-id="4aaa3-158">Element</span></span>|<span data-ttu-id="4aaa3-159">説明</span><span class="sxs-lookup"><span data-stu-id="4aaa3-159">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="4aaa3-160">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-160">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aaa3-161">解説</span><span class="sxs-lookup"><span data-stu-id="4aaa3-161">Remarks</span></span>  

 <span data-ttu-id="4aaa3-162">このバインディングは、TCP を介したピア トランスポートを使用するピア ツー ピア アプリケーションまたはマルチパーティ アプリケーションの作成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-162">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="4aaa3-163">各ピア ノードは、この種類のバイディングを使用して定義された複数のピア チャネルをホストできます。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-163">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4aaa3-164">例</span><span class="sxs-lookup"><span data-stu-id="4aaa3-164">Example</span></span>  

 <span data-ttu-id="4aaa3-165">次の例では、ピア チャネルを使用してマルチパーティ通信を実現する、NetPeerTcpBinding バインディングを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-165">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="4aaa3-166">このバインディングを使用する詳細なシナリオについては、「 [Net ピア TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4aaa3-166">For a detailed scenario of using this binding, see [Net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netPeerBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 maxBufferSize="1001"
                 maxConnections="123"
                 maxReceiveMessageSize="1000">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="TransportWithMessageCredential">
            <message clientCredentialType="CardSpace" />
          </security>
        </binding>
      </netPeerBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="4aaa3-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="4aaa3-167">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="4aaa3-168">バインド</span><span class="sxs-lookup"><span data-stu-id="4aaa3-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4aaa3-169">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="4aaa3-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4aaa3-170">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="4aaa3-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="4aaa3-171">[ネット ピア TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4aaa3-171">[Net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="4aaa3-172">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="4aaa3-172">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)

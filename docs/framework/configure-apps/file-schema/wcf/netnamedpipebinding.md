---
description: '詳細情報: <netNamedPipeBinding>'
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: b6ee706337d3dd33c653bfa0d2b91f4eda0fcea5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683945"
---
# \<netNamedPipeBinding>

<span data-ttu-id="31640-102">コンピューター上のプロセス間通信に適した、セキュリティで保護された信頼できる最適バインディングを定義します。</span><span class="sxs-lookup"><span data-stu-id="31640-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="31640-103">既定では、信頼のための WS-ReliableMessaging、転送セキュリティ用トランスポート セキュリティ、メッセージ配信用名前付きパイプ、およびバイナリ メッセージ エンコーディングを持つランタイム通信スタックを生成します。</span><span class="sxs-lookup"><span data-stu-id="31640-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="31640-104">構文</span><span class="sxs-lookup"><span data-stu-id="31640-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31640-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="31640-105">Attributes and Elements</span></span>  

 <span data-ttu-id="31640-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="31640-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31640-107">属性</span><span class="sxs-lookup"><span data-stu-id="31640-107">Attributes</span></span>  
  
|<span data-ttu-id="31640-108">属性</span><span class="sxs-lookup"><span data-stu-id="31640-108">Attribute</span></span>|<span data-ttu-id="31640-109">説明</span><span class="sxs-lookup"><span data-stu-id="31640-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31640-110">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="31640-110">closeTimeout</span></span>|<span data-ttu-id="31640-111">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="31640-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="31640-112">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="31640-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="31640-113">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="31640-113">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="31640-114">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="31640-114">hostNameComparisonMode</span></span>|<span data-ttu-id="31640-115">URI の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="31640-115">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="31640-116">この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="31640-116">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="31640-117">既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="31640-117">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="31640-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="31640-118">maxBufferPoolSize</span></span>|<span data-ttu-id="31640-119">このバインディングに使用するバッファー プール サイズの上限を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="31640-119">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="31640-120">既定は 524,288 バイト (512 \* 1024) です。</span><span class="sxs-lookup"><span data-stu-id="31640-120">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="31640-121">Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="31640-121">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="31640-122">使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="31640-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="31640-123">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="31640-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="31640-124">これで、バッファーの作成と破棄のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="31640-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="31640-125">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="31640-125">maxBufferSize</span></span>|<span data-ttu-id="31640-126">メッセージをメモリに保存するのに使用するバッファーの最大サイズをバイト単位で指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="31640-126">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="31640-127">バッファーがいっぱいになると、超過データは、バッファーに空きが出るまで、基になるソケットに残されます。</span><span class="sxs-lookup"><span data-stu-id="31640-127">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="31640-128">この値が `maxReceivedMessageSize` 属性の値を下回らないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="31640-128">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="31640-129">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="31640-129">The default is 65536.</span></span> <span data-ttu-id="31640-130">詳細については、「<xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31640-130">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="31640-131">maxConnections</span><span class="sxs-lookup"><span data-stu-id="31640-131">maxConnections</span></span>|<span data-ttu-id="31640-132">サービスが作成し受け付ける発信/着信接続数の上限を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="31640-132">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="31640-133">この属性により指定された別個の制限に対して、着信接続および発信接続がカウントされます。</span><span class="sxs-lookup"><span data-stu-id="31640-133">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="31640-134">制限を超える着信接続は、制限内に空きができるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="31640-134">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="31640-135">制限を超える発信接続は、制限内に空きができるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="31640-135">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="31640-136">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="31640-136">The default is 10.</span></span>|  
|<span data-ttu-id="31640-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="31640-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="31640-138">このバインディングで構成されるチャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) をバイト単位で指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="31640-138">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="31640-139">この制限を超えるメッセージの送信者が、SOAP エラーを受信します。</span><span class="sxs-lookup"><span data-stu-id="31640-139">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="31640-140">メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="31640-140">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="31640-141">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="31640-141">The default is 65536.</span></span>|  
|<span data-ttu-id="31640-142">name</span><span class="sxs-lookup"><span data-stu-id="31640-142">name</span></span>|<span data-ttu-id="31640-143">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="31640-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="31640-144">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="31640-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="31640-145">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="31640-145">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="31640-146">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31640-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="31640-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="31640-147">openTimeout</span></span>|<span data-ttu-id="31640-148">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="31640-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="31640-149">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="31640-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="31640-150">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="31640-150">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="31640-151">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="31640-151">receiveTimeout</span></span>|<span data-ttu-id="31640-152">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="31640-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="31640-153">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="31640-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="31640-154">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="31640-154">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="31640-155">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="31640-155">sendTimeout</span></span>|<span data-ttu-id="31640-156">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="31640-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="31640-157">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="31640-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="31640-158">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="31640-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="31640-159">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="31640-159">transactionFlow</span></span>|<span data-ttu-id="31640-160">バインディングが WS-Transactions のフローをサポートするかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="31640-160">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="31640-161">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="31640-161">The default is `false`.</span></span>|  
|<span data-ttu-id="31640-162">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="31640-162">transactionProtocol</span></span>|<span data-ttu-id="31640-163">このバインディングで使用されるトランザクション プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="31640-163">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="31640-164">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="31640-164">Valid values are</span></span><br /><br /> <span data-ttu-id="31640-165">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="31640-165">-   OleTransactions</span></span><br /><span data-ttu-id="31640-166">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="31640-166">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="31640-167">既定値は OleTransactions です。</span><span class="sxs-lookup"><span data-stu-id="31640-167">The default is OleTransactions.</span></span> <span data-ttu-id="31640-168">この属性は <xref:System.ServiceModel.TransactionProtocol> 型です。</span><span class="sxs-lookup"><span data-stu-id="31640-168">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="31640-169">transferMode</span><span class="sxs-lookup"><span data-stu-id="31640-169">transferMode</span></span>|<span data-ttu-id="31640-170">メッセージが要求や応答をバッファーするか、ストリーミングするかを指定する <xref:System.ServiceModel.TransferMode> 値です。</span><span class="sxs-lookup"><span data-stu-id="31640-170">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31640-171">子要素</span><span class="sxs-lookup"><span data-stu-id="31640-171">Child Elements</span></span>  
  
|<span data-ttu-id="31640-172">要素</span><span class="sxs-lookup"><span data-stu-id="31640-172">Element</span></span>|<span data-ttu-id="31640-173">説明</span><span class="sxs-lookup"><span data-stu-id="31640-173">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="31640-174">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="31640-174">Defines the security settings for the binding.</span></span> <span data-ttu-id="31640-175">この要素は <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="31640-175">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="31640-176">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="31640-176">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="31640-177">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="31640-177">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31640-178">親要素</span><span class="sxs-lookup"><span data-stu-id="31640-178">Parent Elements</span></span>  
  
|<span data-ttu-id="31640-179">要素</span><span class="sxs-lookup"><span data-stu-id="31640-179">Element</span></span>|<span data-ttu-id="31640-180">説明</span><span class="sxs-lookup"><span data-stu-id="31640-180">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="31640-181">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="31640-181">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31640-182">解説</span><span class="sxs-lookup"><span data-stu-id="31640-182">Remarks</span></span>  

 <span data-ttu-id="31640-183">`NetNamedPipeBinding` は、トランスポート セキュリティ、メッセージ配信用の名前付きパイプ、およびバイナリ メッセージ エンコーディングを使用するランタイム通信スタックを既定で生成します。</span><span class="sxs-lookup"><span data-stu-id="31640-183">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="31640-184">このバインディングは、コンピューター間通信に適した、WCF (Windows Communication Foundation) システム標準の選択肢です。</span><span class="sxs-lookup"><span data-stu-id="31640-184">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="31640-185">トランザクションもサポートします。</span><span class="sxs-lookup"><span data-stu-id="31640-185">It also supports transactions.</span></span>  
  
 <span data-ttu-id="31640-186">`NetNamedPipeBinding` の既定の構成は、`NetTcpBinding` によって提供される構成に似ていますが、それよりも単純です。この理由は、WCF の実装はコンピューター間での使用のみを目的としているので、公開される機能が少ないためです。</span><span class="sxs-lookup"><span data-stu-id="31640-186">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="31640-187">最も顕著な違いは、`securityMode` 設定に `None` オプションと `Transport` オプションしか用意されていないことです。</span><span class="sxs-lookup"><span data-stu-id="31640-187">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="31640-188">SOAP セキュリティ サポートは、オプションに含まれません。</span><span class="sxs-lookup"><span data-stu-id="31640-188">SOAP security support is not an included option.</span></span> <span data-ttu-id="31640-189">このセキュリティ動作は、省略可能な `securityMode` 属性を使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="31640-189">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31640-190">例</span><span class="sxs-lookup"><span data-stu-id="31640-190">Example</span></span>  

 <span data-ttu-id="31640-191">次の例では、同じコンピューター上でのプロセス間通信を実現する NetNamedPipeBinding バインディングを示します。</span><span class="sxs-lookup"><span data-stu-id="31640-191">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="31640-192">名前付きパイプは、異なるコンピューター間では動作しません。</span><span class="sxs-lookup"><span data-stu-id="31640-192">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="31640-193">バインディングは、クライアントとサービスの構成ファイルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="31640-193">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="31640-194">バインディングの種類は、`binding` 要素の `<endpoint>` 属性に指定します。</span><span class="sxs-lookup"><span data-stu-id="31640-194">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="31640-195">netNamedPipeBinding バインディングを構成してその設定の一部を変更する場合は、バインド構成を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31640-195">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="31640-196">エンドポイントは、バインディング構成を `bindingConfiguration` 属性を使用して名前で参照します。</span><span class="sxs-lookup"><span data-stu-id="31640-196">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="31640-197">この例では、バインディングの構成の名前は Binding1 です。</span><span class="sxs-lookup"><span data-stu-id="31640-197">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="31640-198">関連項目</span><span class="sxs-lookup"><span data-stu-id="31640-198">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="31640-199">バインド</span><span class="sxs-lookup"><span data-stu-id="31640-199">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="31640-200">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="31640-200">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="31640-201">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="31640-201">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)

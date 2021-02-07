---
description: '詳細情報: <ws2007HttpBinding>'
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 1a74fb604054a4215c89c2d772ee4f83e6416a08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682164"
---
# \<ws2007HttpBinding>

<span data-ttu-id="6d0b3-102"><xref:System.ServiceModel.WSHttpBinding.Security%2A>、<xref:System.ServiceModel.ReliableSession>、および <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> の各バインド要素の適切なバージョンをサポートする相互運用可能なバインディングを定義します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="6d0b3-103">構文</span><span class="sxs-lookup"><span data-stu-id="6d0b3-103">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d0b3-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6d0b3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6d0b3-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d0b3-106">属性</span><span class="sxs-lookup"><span data-stu-id="6d0b3-106">Attributes</span></span>  
  
|<span data-ttu-id="6d0b3-107">属性</span><span class="sxs-lookup"><span data-stu-id="6d0b3-107">Attribute</span></span>|<span data-ttu-id="6d0b3-108">説明</span><span class="sxs-lookup"><span data-stu-id="6d0b3-108">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="6d0b3-109">クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-109">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="6d0b3-110">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-110">The default is `false`.</span></span><br /><br /> <span data-ttu-id="6d0b3-111">クッキーを使用する ASMX (ASP.NET Web サービス) と対話する場合に、このプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-111">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="6d0b3-112">これにより、サーバーから返されるクッキーが、このサービスに対するそれ以降のすべてのクライアント要求に自動的にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-112">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="6d0b3-113">ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="6d0b3-114">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="6d0b3-115">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-115">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="6d0b3-116">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6d0b3-117">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-117">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="6d0b3-118">URI (Uniform Resource Identifier) の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-118">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="6d0b3-119">この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="6d0b3-120">既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="6d0b3-121">このバインドに使用するバッファー プールの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="6d0b3-122">既定値は 524,288 バイト (512 × 1,024) です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-122">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="6d0b3-123">Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="6d0b3-124">使用するたびに毎回バッファーを作成および破棄すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-124">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="6d0b3-125">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="6d0b3-126">これで、バッファーの作成と破棄によるオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-126">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="6d0b3-127">このバインディングで構成されたチャネルで受信可能な、ヘッダーを含む最大メッセージ サイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-127">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="6d0b3-128">この制限を超える場合、メッセージの送信者は SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-128">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="6d0b3-129">メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6d0b3-130">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="6d0b3-131">メッセージのエンコードに使用されるエンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="6d0b3-132">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6d0b3-133">-   `Text`: テキストメッセージエンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-133">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="6d0b3-134">-   `Mtom`: メッセージ伝送組織機構 1.0 (MTOM) エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-134">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="6d0b3-135">既定値は、`Text` です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-135">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="6d0b3-136">この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="6d0b3-137">バインドの構成名。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-137">The configuration name of the binding.</span></span> <span data-ttu-id="6d0b3-138">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6d0b3-139">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-139">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6d0b3-140">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="6d0b3-141">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6d0b3-142">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6d0b3-143">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-143">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="6d0b3-144">HTTP プロキシのアドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-144">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="6d0b3-145">`useSystemWebProxy` が `true` の場合、この設定を `null` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-145">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="6d0b3-146">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-146">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="6d0b3-147">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6d0b3-148">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6d0b3-149">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-149">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="6d0b3-150">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6d0b3-151">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6d0b3-152">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-152">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="6d0b3-153">バインディングでメッセージの発行に使用する文字セット エンコーディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-153">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="6d0b3-154">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-154">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6d0b3-155">-   `UnicodeFffeTextEncoding`: Unicode ビッグエンディアンエンコーディング。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-155">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="6d0b3-156">-   `Utf16TextEncoding`:16 ビットエンコード。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-156">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="6d0b3-157">-   `Utf8TextEncoding`: 8 ビットエンコーディング。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-157">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="6d0b3-158">既定値は、`Utf8TextEncoding` です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-158">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="6d0b3-159">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-159">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="6d0b3-160">バインドが WS-Transactions のフローをサポートするかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-160">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="6d0b3-161">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-161">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="6d0b3-162">システムの自動設定 HTTP プロキシを使用するかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-162">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="6d0b3-163">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-163">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d0b3-164">子要素</span><span class="sxs-lookup"><span data-stu-id="6d0b3-164">Child Elements</span></span>  
  
|<span data-ttu-id="6d0b3-165">要素</span><span class="sxs-lookup"><span data-stu-id="6d0b3-165">Element</span></span>|<span data-ttu-id="6d0b3-166">説明</span><span class="sxs-lookup"><span data-stu-id="6d0b3-166">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="6d0b3-167">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-167">Defines the security settings for the binding.</span></span> <span data-ttu-id="6d0b3-168">この要素は <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-168">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="6d0b3-169">このバインディングを使用して設定されるエンドポイントで処理できる、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-169">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="6d0b3-170">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-170">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="6d0b3-171">チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-171">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d0b3-172">親要素</span><span class="sxs-lookup"><span data-stu-id="6d0b3-172">Parent Elements</span></span>  
  
|<span data-ttu-id="6d0b3-173">要素</span><span class="sxs-lookup"><span data-stu-id="6d0b3-173">Element</span></span>|<span data-ttu-id="6d0b3-174">説明</span><span class="sxs-lookup"><span data-stu-id="6d0b3-174">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="6d0b3-175">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-175">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d0b3-176">解説</span><span class="sxs-lookup"><span data-stu-id="6d0b3-176">Remarks</span></span>  

 <span data-ttu-id="6d0b3-177">`WS2007HttpBinding` は、`WSHttpBinding` と同様のシステム標準のバインディングを追加しますが、ReliableSession、Security、および TransactionFlow の各プロトコルの OASIS (Organization for the Advancement of Structured Information Standards) 標準バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-177">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="6d0b3-178">このバインドを使用する場合、オブジェクト モデルも既定の設定も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6d0b3-178">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d0b3-179">例</span><span class="sxs-lookup"><span data-stu-id="6d0b3-179">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="6d0b3-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d0b3-180">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="6d0b3-181">バインド</span><span class="sxs-lookup"><span data-stu-id="6d0b3-181">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6d0b3-182">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="6d0b3-182">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6d0b3-183">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="6d0b3-183">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

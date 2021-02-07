---
description: '詳細情報: <ws2007FederationHttpBinding>'
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 90635805573e5bee64d8adf0f79de827733f178b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682190"
---
# \<ws2007FederationHttpBinding>

<span data-ttu-id="671b9-102">から派生し、フェデレーションセキュリティをサポートする、セキュリティで保護された相互運用可能なバインディング [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="671b9-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="671b9-103">構文</span><span class="sxs-lookup"><span data-stu-id="671b9-103">Syntax</span></span>

```xml
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="671b9-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="671b9-104">Attributes and Elements</span></span>

<span data-ttu-id="671b9-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="671b9-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="671b9-106">属性</span><span class="sxs-lookup"><span data-stu-id="671b9-106">Attributes</span></span>

|<span data-ttu-id="671b9-107">属性</span><span class="sxs-lookup"><span data-stu-id="671b9-107">Attribute</span></span>|<span data-ttu-id="671b9-108">説明</span><span class="sxs-lookup"><span data-stu-id="671b9-108">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="671b9-109">ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="671b9-109">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="671b9-110">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="671b9-110">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="671b9-111">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="671b9-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="671b9-112">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="671b9-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="671b9-113">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="671b9-113">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="671b9-114">URI の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="671b9-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="671b9-115">この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="671b9-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="671b9-116">既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="671b9-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="671b9-117">このバインドに使用するバッファー プールの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="671b9-117">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="671b9-118">既定は 524,288 バイト (512 \* 1024) です。</span><span class="sxs-lookup"><span data-stu-id="671b9-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="671b9-119">Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="671b9-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="671b9-120">使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="671b9-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="671b9-121">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="671b9-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="671b9-122">これで、バッファーの作成と破棄のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="671b9-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="671b9-123">チャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) が、このバインドを使用してバイト単位で設定されました。</span><span class="sxs-lookup"><span data-stu-id="671b9-123">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="671b9-124">この制限を超えるメッセージの送信者が、SOAP エラーを受信します。</span><span class="sxs-lookup"><span data-stu-id="671b9-124">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="671b9-125">メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="671b9-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="671b9-126">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="671b9-126">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="671b9-127">メッセージのエンコードに使用されるエンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="671b9-127">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="671b9-128">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="671b9-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="671b9-129">-Text: テキストメッセージエンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="671b9-129">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="671b9-130">-Mtom: メッセージ伝送組織機構 1.0 (MTOM) エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="671b9-130">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="671b9-131">既定値は Text です。</span><span class="sxs-lookup"><span data-stu-id="671b9-131">The default is Text.</span></span><br /><br /> <span data-ttu-id="671b9-132">この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="671b9-132">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="671b9-133">バインドの構成名。</span><span class="sxs-lookup"><span data-stu-id="671b9-133">The configuration name of the binding.</span></span> <span data-ttu-id="671b9-134">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="671b9-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="671b9-135">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="671b9-135">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="671b9-136">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="671b9-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="671b9-137">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="671b9-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="671b9-138">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="671b9-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="671b9-139">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="671b9-139">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="671b9-140">プライバシーに関する声明の場所を示す URI。</span><span class="sxs-lookup"><span data-stu-id="671b9-140">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="671b9-141">現在のプライバシーに関する声明のバージョン。</span><span class="sxs-lookup"><span data-stu-id="671b9-141">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="671b9-142">HTTP プロキシのアドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="671b9-142">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="671b9-143">`useDefaultWebProxy` が `true` の場合、この設定を `null` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="671b9-143">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="671b9-144">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="671b9-144">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="671b9-145">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="671b9-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="671b9-146">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="671b9-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="671b9-147">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="671b9-147">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="671b9-148">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="671b9-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="671b9-149">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="671b9-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="671b9-150">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="671b9-150">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="671b9-151">バインディングでメッセージの発行に使用される文字セット エンコーディングを設定します。</span><span class="sxs-lookup"><span data-stu-id="671b9-151">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="671b9-152">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="671b9-152">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="671b9-153">-BigEndianUnicode: Unicode ビッグエンディアンエンコーディング。</span><span class="sxs-lookup"><span data-stu-id="671b9-153">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="671b9-154">-Unicode:16 ビットエンコード。</span><span class="sxs-lookup"><span data-stu-id="671b9-154">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="671b9-155">-UTF8: 8 ビットエンコーディング。</span><span class="sxs-lookup"><span data-stu-id="671b9-155">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="671b9-156">既定値は UTF8 です。</span><span class="sxs-lookup"><span data-stu-id="671b9-156">The default is UTF8.</span></span> <span data-ttu-id="671b9-157">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="671b9-157">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="671b9-158">バインドが WS-Transactions のフローをサポートするかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="671b9-158">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="671b9-159">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="671b9-159">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="671b9-160">システムの自動設定 HTTP プロキシを使用するかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="671b9-160">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="671b9-161">この属性が `null` の場合、プロキシ アドレスを `true` (つまり、設定しない) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="671b9-161">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="671b9-162">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="671b9-162">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="671b9-163">子要素</span><span class="sxs-lookup"><span data-stu-id="671b9-163">Child Elements</span></span>

|<span data-ttu-id="671b9-164">要素</span><span class="sxs-lookup"><span data-stu-id="671b9-164">Element</span></span>|<span data-ttu-id="671b9-165">説明</span><span class="sxs-lookup"><span data-stu-id="671b9-165">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="671b9-166">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="671b9-166">Defines the security settings for the message.</span></span> <span data-ttu-id="671b9-167">この要素は <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="671b9-167">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="671b9-168">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="671b9-168">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="671b9-169">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="671b9-169">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="671b9-170">チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="671b9-170">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="671b9-171">親要素</span><span class="sxs-lookup"><span data-stu-id="671b9-171">Parent Elements</span></span>

|<span data-ttu-id="671b9-172">要素</span><span class="sxs-lookup"><span data-stu-id="671b9-172">Element</span></span>|<span data-ttu-id="671b9-173">説明</span><span class="sxs-lookup"><span data-stu-id="671b9-173">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="671b9-174">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="671b9-174">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="671b9-175">解説</span><span class="sxs-lookup"><span data-stu-id="671b9-175">Remarks</span></span>

<span data-ttu-id="671b9-176">フェデレーションは、複数の企業または信頼するドメインで認証と承認用の ID を共有する機能です。</span><span class="sxs-lookup"><span data-stu-id="671b9-176">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="671b9-177">フェデレーションは、WS-Trust プロトコルを使用して、ID 形式を、ある信頼するドメインから別の信頼するドメインにマップします。</span><span class="sxs-lookup"><span data-stu-id="671b9-177">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="671b9-178">フェデレーション HTTP バインドは、SOAP セキュリティと混合モード セキュリティをサポートしますが、トランスポート セキュリティの単独使用はサポートしません。</span><span class="sxs-lookup"><span data-stu-id="671b9-178">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="671b9-179">このバインディングで構成されたサービスは、HTTP トランスポートを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="671b9-179">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="671b9-180">詳細については、「[\<wsFederationHttpBinding>](wsfederationhttpbinding.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="671b9-180">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="671b9-181">例</span><span class="sxs-lookup"><span data-stu-id="671b9-181">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="671b9-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="671b9-182">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [<span data-ttu-id="671b9-183">バインド</span><span class="sxs-lookup"><span data-stu-id="671b9-183">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="671b9-184">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="671b9-184">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="671b9-185">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="671b9-185">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

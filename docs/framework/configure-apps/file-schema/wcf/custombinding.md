---
description: '詳細情報: <customBinding>'
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: a4d297750d107648aa10b349c6febc1a8929a30b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803946"
---
# \<customBinding>

<span data-ttu-id="122a2-102">ユーザーのメッセージ スタックを完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="122a2-102">Provides full control over the messaging stack for the user.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**  

## <a name="syntax"></a><span data-ttu-id="122a2-103">構文</span><span class="sxs-lookup"><span data-stu-id="122a2-103">Syntax</span></span>

```xml
<customBinding>
  <binding name="String"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
    <compositeDuplex clientBaseAddress="Uri" />
    <reliableSession acknowledgementInterval="TimeSpan"
                     advancedFlowControl="Boolean"
                     bufferedMessagesQuota="Integer"
                     inactivityTimeout="TimeSpan"
                     maxPendingChannels="Integer"
                     maxRetryCount="Integer"
                     ordered="Boolean" />
    <pnrpPeerResolver />
    <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
    <sslStreamSecurity requireClientCertificate="Boolean" />
    <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              contextMode="Cookie"
              defaultProtectionLevel="Sign"
              enableKeyDerivation="false"
              keyEntropyMode="ClientEntropy"
              messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"
              securityVersion="WSSecurityXXX2005">
      <localClientSettings cacheCookies="false"
                           detectReplays="false"
                           maxCookieCachingTime="00:07:24" />
      <localServiceSettings replayCacheSize="9"
                            maxClockSkew="00:00:03"
                            replayWindow="00:07:22.2190000" />
    </security>
    <binaryMessageEncoding maxReadPoolSize="Integer"
                           maxWritePoolSize="Integer"
                           maxSessionSize="Integer" />
    <httpsTransport manualAddressing="Boolean"
                    maxMessageSize="Integer"
                    authenticationScheme="Negotiate"
                    bypassProxyOnLocal="Boolean"
                    hostNameComparisonMode="Exact"
                    mapAddressingHeadersToHttpHeaders="Boolean"
                    proxyaddress="Uri"
                    realm="String"
                    requireClientCertificate="Boolean" />
    <peerTransport manualAddressing="false"
                   maxMessageSize="20002"
                   listenIPAddress="202.10.1.9"
                   messageAuthentication="false"
                   peerNodeAuthenticationMode="None"
                   port="1000" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean">
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                            issuedCookieLifeTime="TimeSpan"
                            maxStatefulNegotiations="Integer"
                            replayCacheSize="Integer"
                            maxClockSkew="TimeSpan"
                            negotiationTimeout="TimeSpan"
                            replayWindow="TimeSpan"
                            inactivityTimeout="TimeSpan"
                            sessionKeyRenewalInterval="TimeSpan"
                            sessionKeyRolloverInterval="TimeSpan"
                            reconnectOnTransportFailure="Boolean"
                            maxConcurrentSessions="Integer"
                            timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
    </security>
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean" >
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                           issuedCookieLifeTime="TimeSpan"
                           maxStatefulNegotiations="Integer"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           negotiationTimeout="TimeSpan"
                           replayWindow="TimeSpan"
                           inactivityTimeout="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           maxConcurrentSessions="Integer"
                           timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
      <genericIssuedTokenParameters>
        <localIssuerIssuedTokenParameters keyType="SymmetricKey/PublicKey"
                                          keySize="Integer"
                                          tokenType="String" />
        <issuedTokenParametersEndpointAddress address="URI"
                                              bindingConfiguration="String"
                                              binding="String" />
        <issuedTokenClient localIssuerChannelBehaviors="String"
                           cacheIssuedTokens="Boolean"
                           maxIssuedTokenCachingTime="TimeSpan"
                           keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />
        <issuedTokenClientBehavior issuerAddress="String"
                                   behaviorConfiguration="String" />
        <issuedTokenClientBehavior address="URI"
                                   bindingConfiguration="String"
                                   binding="String" />
      </genericIssuedTokenParameters>
    </security>
  </binding>
</customBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="122a2-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="122a2-104">Attributes and Elements</span></span>

<span data-ttu-id="122a2-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="122a2-105">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="122a2-106">属性</span><span class="sxs-lookup"><span data-stu-id="122a2-106">Attributes</span></span>

|<span data-ttu-id="122a2-107">属性</span><span class="sxs-lookup"><span data-stu-id="122a2-107">Attribute</span></span>|<span data-ttu-id="122a2-108">説明</span><span class="sxs-lookup"><span data-stu-id="122a2-108">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="122a2-109">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="122a2-109">closeTimeout</span></span>|<span data-ttu-id="122a2-110">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="122a2-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="122a2-111">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="122a2-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="122a2-112">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="122a2-112">The default is 00:01:00.</span></span>|
|<span data-ttu-id="122a2-113">name</span><span class="sxs-lookup"><span data-stu-id="122a2-113">name</span></span>|<span data-ttu-id="122a2-114">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="122a2-114">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="122a2-115">この値は、カスタム バインディングの識別文字列として機能するユーザー定義文字列です。</span><span class="sxs-lookup"><span data-stu-id="122a2-115">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="122a2-116">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="122a2-116">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="122a2-117">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="122a2-117">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="122a2-118">openTimeout</span><span class="sxs-lookup"><span data-stu-id="122a2-118">openTimeout</span></span>|<span data-ttu-id="122a2-119">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="122a2-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="122a2-120">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="122a2-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="122a2-121">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="122a2-121">The default is 00:01:00.</span></span>|
|<span data-ttu-id="122a2-122">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="122a2-122">receiveTimeout</span></span>|<span data-ttu-id="122a2-123">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="122a2-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="122a2-124">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="122a2-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="122a2-125">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="122a2-125">The default is 00:01:00.</span></span>|
|<span data-ttu-id="122a2-126">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="122a2-126">sendTimeout</span></span>|<span data-ttu-id="122a2-127">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="122a2-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="122a2-128">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="122a2-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="122a2-129">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="122a2-129">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="122a2-130">子要素</span><span class="sxs-lookup"><span data-stu-id="122a2-130">Child Elements</span></span>

|<span data-ttu-id="122a2-131">要素</span><span class="sxs-lookup"><span data-stu-id="122a2-131">Element</span></span>|<span data-ttu-id="122a2-132">説明</span><span class="sxs-lookup"><span data-stu-id="122a2-132">Description</span></span>|
|-------------|-----------------|
|[\<compositeDuplex>](compositeduplex.md)|<span data-ttu-id="122a2-133">カスタム バインドの双方向のメッセージングを指定します。</span><span class="sxs-lookup"><span data-stu-id="122a2-133">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="122a2-134">たとえば HTTP のように、ネイティブでの二重通信を許可しないトランスポートで使用されます。</span><span class="sxs-lookup"><span data-stu-id="122a2-134">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="122a2-135">これとは対照的に、TCP では、二重通信がネイティブで許可されているので、クライアントにメッセージを返信するためにこのバインディング要素をサービスで使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="122a2-135">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="122a2-136">クライアントは、サービスのアドレスを公開して、アクセスおよび接続の確立ができるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="122a2-136">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="122a2-137">このクライアント アドレスは、`ClientBaseAddress` 属性によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="122a2-137">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="122a2-138">この要素は <xref:System.ServiceModel.Configuration.CompositeDuplexElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="122a2-138">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[\<pnrpPeerResolver>](pnrppeerresolver.md)|<span data-ttu-id="122a2-139">PNRP (Peer Name Resolution Protocol) ピア名リゾルバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="122a2-139">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="122a2-140">この要素は <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="122a2-140">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[\<reliableSession>](reliablesession.md)|<span data-ttu-id="122a2-141">WS-ReliableMessaging の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="122a2-141">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="122a2-142">この要素がカスタム バインディングに追加される場合、その結果となるチャネルにより、正確に 1 回の配信保証をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="122a2-142">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="122a2-143">この要素は <xref:System.ServiceModel.Configuration.ReliableSessionElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="122a2-143">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="122a2-144">カスタム バインドのセキュリティ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="122a2-144">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="122a2-145">この要素は <xref:System.ServiceModel.Configuration.SecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="122a2-145">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[\<sslStreamSecurity>](sslstreamsecurity.md)|<span data-ttu-id="122a2-146">SSL ストリーム バインディングのセキュリティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="122a2-146">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="122a2-147">この要素は <xref:System.ServiceModel.Configuration.SslStreamSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="122a2-147">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[\<transactionFlow>](transactionflow.md)|<span data-ttu-id="122a2-148">バインディングがトランザクション フローをサポートし、プロトコルが `transactionProtocol` 属性によって使用される必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="122a2-148">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="122a2-149">この要素は <xref:System.ServiceModel.Configuration.TransactionFlowElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="122a2-149">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[\<windowsStreamSecurity>](windowsstreamsecurity.md)|<span data-ttu-id="122a2-150">カスタム バインドのストリーミング セキュリティのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="122a2-150">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="122a2-151">この要素は <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="122a2-151">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="122a2-152">親要素</span><span class="sxs-lookup"><span data-stu-id="122a2-152">Parent Elements</span></span>

|<span data-ttu-id="122a2-153">要素</span><span class="sxs-lookup"><span data-stu-id="122a2-153">Element</span></span>|<span data-ttu-id="122a2-154">説明</span><span class="sxs-lookup"><span data-stu-id="122a2-154">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="122a2-155">バインディング</span><span class="sxs-lookup"><span data-stu-id="122a2-155">bindings</span></span>|<span data-ttu-id="122a2-156">Windows Communication Foundation アプリケーションのすべてのバインディングを含みます。</span><span class="sxs-lookup"><span data-stu-id="122a2-156">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="122a2-157">解説</span><span class="sxs-lookup"><span data-stu-id="122a2-157">Remarks</span></span>

<span data-ttu-id="122a2-158">カスタム バインディングを使用すると、WCF メッセージ スタックのフル コントロールが可能になります。</span><span class="sxs-lookup"><span data-stu-id="122a2-158">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="122a2-159">特定のエンティティの構成要素を追加した、特別にカスタマイズされたバインディングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="122a2-159">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="122a2-160">たとえば、ユーザーは `httpsTransport` セクション、`reliableSession` セクション、および `security` セクションを組み合わせて、信頼できるセキュリティで保護された HTTPS ベースのバインディングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="122a2-160">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="122a2-161">個別のバインディングは、メッセージ スタックを、スタック要素の構成要素をスタックに出現する順序で指定することにより定義します。</span><span class="sxs-lookup"><span data-stu-id="122a2-161">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="122a2-162">各要素は、スタック内の 1 つの要素を定義および構成します。</span><span class="sxs-lookup"><span data-stu-id="122a2-162">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="122a2-163">各カスタム バインディング内のトランスポート要素は 1 つだけにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="122a2-163">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="122a2-164">この要素がない場合、メッセージ スタックは不完全です。</span><span class="sxs-lookup"><span data-stu-id="122a2-164">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="122a2-165">要素がスタックに出現する順序は重要です。それは、その順序で操作がメッセージに適用されるためです。</span><span class="sxs-lookup"><span data-stu-id="122a2-165">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="122a2-166">スタック要素で推奨される順序を次に示します。</span><span class="sxs-lookup"><span data-stu-id="122a2-166">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="122a2-167">トランザクション (省略可能)</span><span class="sxs-lookup"><span data-stu-id="122a2-167">Transactions (optional)</span></span>

2. <span data-ttu-id="122a2-168">リライアブル メッセージ機能 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="122a2-168">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="122a2-169">セキュリティ (省略可能)</span><span class="sxs-lookup"><span data-stu-id="122a2-169">Security (optional)</span></span>

4. <span data-ttu-id="122a2-170">トランスポート</span><span class="sxs-lookup"><span data-stu-id="122a2-170">Transport</span></span>

5. <span data-ttu-id="122a2-171">エンコーダー (省略可能)</span><span class="sxs-lookup"><span data-stu-id="122a2-171">Encoder (optional)</span></span>

<span data-ttu-id="122a2-172">システムが提供するバインディングの中にサービスの要件を満たすものがない場合は、カスタム バインドを使用します。</span><span class="sxs-lookup"><span data-stu-id="122a2-172">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="122a2-173">たとえば、カスタム バインドを使用すると、サービス エンドポイントで新しいトランスポートや新しいエンコーダーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="122a2-173">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="122a2-174">カスタム バインドは、特定の順序で "積み重ねられている" バインド要素のコレクションから <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> の 1 つを使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="122a2-174">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="122a2-175">最上位にあるのは、トランザクションのフローを可能にするオプションの <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> です。</span><span class="sxs-lookup"><span data-stu-id="122a2-175">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="122a2-176">その次にあるのは、WS-ReliableMessaging 仕様で定義されているセッションおよび順序指定のメカニズムを提供するオプションの <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> です。</span><span class="sxs-lookup"><span data-stu-id="122a2-176">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="122a2-177">このセッションの概念は、SOAP およびトランスポート中継局を通過できます。</span><span class="sxs-lookup"><span data-stu-id="122a2-177">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="122a2-178">その次にあるのは、承認、認証、保護、機密性などのセキュリティ機能を提供するオプションのセキュリティ バインド要素です。</span><span class="sxs-lookup"><span data-stu-id="122a2-178">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="122a2-179">Windows Communication Foundation (WCF) によって提供されるセキュリティバインド要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="122a2-179">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="122a2-180">その次にあるのは、バインド要素によって指定されるオプションのメッセージ パターンです。</span><span class="sxs-lookup"><span data-stu-id="122a2-180">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="122a2-181">その次にあるのは、オプションのトランスポート アップグレード/ヘルパー バインド要素です。</span><span class="sxs-lookup"><span data-stu-id="122a2-181">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="122a2-182">その次にあるのは、必須のメッセージ エンコード バインド要素です。</span><span class="sxs-lookup"><span data-stu-id="122a2-182">Next is a required message encoding binding element.</span></span> <span data-ttu-id="122a2-183">独自のトランスポートを使用することも、以下のメッセージ エンコード バインドのいずれかを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="122a2-183">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="122a2-184">最下位には、必須のトランスポート要素があります。</span><span class="sxs-lookup"><span data-stu-id="122a2-184">At the bottom is a required transport element.</span></span> <span data-ttu-id="122a2-185">独自のトランスポートを使用することも、Windows Communication Foundation (WCF) によって提供されるトランスポートバインド要素のいずれかを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="122a2-185">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="122a2-186">各層のオプションの概要を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="122a2-186">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="122a2-187">レイヤー</span><span class="sxs-lookup"><span data-stu-id="122a2-187">Layer</span></span>|<span data-ttu-id="122a2-188">Options</span><span class="sxs-lookup"><span data-stu-id="122a2-188">Options</span></span>|<span data-ttu-id="122a2-189">必須</span><span class="sxs-lookup"><span data-stu-id="122a2-189">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="122a2-190">トランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="122a2-190">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="122a2-191">いいえ</span><span class="sxs-lookup"><span data-stu-id="122a2-191">No</span></span>|
|<span data-ttu-id="122a2-192">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="122a2-192">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="122a2-193">いいえ</span><span class="sxs-lookup"><span data-stu-id="122a2-193">No</span></span>|
|<span data-ttu-id="122a2-194">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="122a2-194">Security</span></span>|<span data-ttu-id="122a2-195">同期、非同期、トランスポート レベル</span><span class="sxs-lookup"><span data-stu-id="122a2-195">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="122a2-196">いいえ</span><span class="sxs-lookup"><span data-stu-id="122a2-196">No</span></span>|
|<span data-ttu-id="122a2-197">形状の変更</span><span class="sxs-lookup"><span data-stu-id="122a2-197">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="122a2-198">いいえ</span><span class="sxs-lookup"><span data-stu-id="122a2-198">No</span></span>|
|<span data-ttu-id="122a2-199">トランスポートのアップグレード</span><span class="sxs-lookup"><span data-stu-id="122a2-199">Transport Upgrades</span></span>|<span data-ttu-id="122a2-200">SSL ストリーム、Windows ストリーム、ピア リゾルバー</span><span class="sxs-lookup"><span data-stu-id="122a2-200">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="122a2-201">いいえ</span><span class="sxs-lookup"><span data-stu-id="122a2-201">No</span></span>|
|<span data-ttu-id="122a2-202">エンコード</span><span class="sxs-lookup"><span data-stu-id="122a2-202">Encoding</span></span>|<span data-ttu-id="122a2-203">テキスト、バイナリ、MTOM、カスタム</span><span class="sxs-lookup"><span data-stu-id="122a2-203">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="122a2-204">はい</span><span class="sxs-lookup"><span data-stu-id="122a2-204">Yes</span></span>|
|<span data-ttu-id="122a2-205">トランスポート</span><span class="sxs-lookup"><span data-stu-id="122a2-205">Transport</span></span>|<span data-ttu-id="122a2-206">TCP、名前付きパイプ、HTTP、HTTPS、MSMQ のフレーバー、カスタム</span><span class="sxs-lookup"><span data-stu-id="122a2-206">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="122a2-207">はい</span><span class="sxs-lookup"><span data-stu-id="122a2-207">Yes</span></span>|

<span data-ttu-id="122a2-208">さらに、独自のバインド要素を定義し、それを定義済みの層のいずれかの間に挿入できます。</span><span class="sxs-lookup"><span data-stu-id="122a2-208">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="122a2-209">カスタムバインディングを使用してシステム指定のバインディングを変更する方法の詳細については、「 [方法: System-Provided バインディングをカスタマイズ](../../../wcf/extending/how-to-customize-a-system-provided-binding.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="122a2-209">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="122a2-210">関連項目</span><span class="sxs-lookup"><span data-stu-id="122a2-210">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="122a2-211">バインド</span><span class="sxs-lookup"><span data-stu-id="122a2-211">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="122a2-212">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="122a2-212">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="122a2-213">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="122a2-213">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="122a2-214">customBinding 要素</span><span class="sxs-lookup"><span data-stu-id="122a2-214">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="122a2-215">バインド</span><span class="sxs-lookup"><span data-stu-id="122a2-215">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="122a2-216">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="122a2-216">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="122a2-217">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="122a2-217">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)

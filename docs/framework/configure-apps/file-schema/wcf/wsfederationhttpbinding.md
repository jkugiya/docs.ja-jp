---
description: '詳細情報: <wsFederationHttpBinding>'
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 1217c4e46fe18ea5df478b8a790be4da33590c92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682099"
---
# \<wsFederationHttpBinding>

<span data-ttu-id="75c9c-102">WS-Federation をサポートするバインディングを定義します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-102">Defines a binding that supports WS-Federation.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**  

## <a name="syntax"></a><span data-ttu-id="75c9c-103">構文</span><span class="sxs-lookup"><span data-stu-id="75c9c-103">Syntax</span></span>

```xml
<wsFederationHttpBinding>
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
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
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
</wsFederationBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75c9c-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="75c9c-104">Attributes and Elements</span></span>

<span data-ttu-id="75c9c-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="75c9c-106">属性</span><span class="sxs-lookup"><span data-stu-id="75c9c-106">Attributes</span></span>

|<span data-ttu-id="75c9c-107">属性</span><span class="sxs-lookup"><span data-stu-id="75c9c-107">Attribute</span></span>|<span data-ttu-id="75c9c-108">説明</span><span class="sxs-lookup"><span data-stu-id="75c9c-108">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="75c9c-109">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="75c9c-109">bypassProxyOnLocal</span></span>|<span data-ttu-id="75c9c-110">ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="75c9c-110">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="75c9c-111">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-111">The default is `false`.</span></span>|
|<span data-ttu-id="75c9c-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="75c9c-112">closeTimeout</span></span>|<span data-ttu-id="75c9c-113">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="75c9c-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="75c9c-114">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="75c9c-115">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-115">The default is 00:01:00.</span></span>|
|<span data-ttu-id="75c9c-116">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="75c9c-116">hostnameComparisonMode</span></span>|<span data-ttu-id="75c9c-117">URI の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-117">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="75c9c-118">この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-118">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="75c9c-119">既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-119">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="75c9c-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="75c9c-120">maxBufferPoolSize</span></span>|<span data-ttu-id="75c9c-121">このバインディングに使用するバッファー プール サイズの上限を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="75c9c-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="75c9c-122">既定は 524,288 バイト (512 \* 1024) です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="75c9c-123">Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="75c9c-124">使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="75c9c-125">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="75c9c-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="75c9c-126">これで、バッファーの作成と破棄のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="75c9c-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="75c9c-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="75c9c-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="75c9c-128">このバインディングで構成されるチャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) をバイト単位で指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="75c9c-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="75c9c-129">この制限を超えるメッセージの送信者が、SOAP エラーを受信します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="75c9c-130">メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="75c9c-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="75c9c-131">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-131">The default is 65536.</span></span>|
|<span data-ttu-id="75c9c-132">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="75c9c-132">messageEncoding</span></span>|<span data-ttu-id="75c9c-133">メッセージのエンコードに使用されるエンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-133">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="75c9c-134">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="75c9c-134">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="75c9c-135">-Text: テキストメッセージエンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-135">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="75c9c-136">-Mtom: メッセージ伝送組織機構 1.0 (MTOM) エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-136">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="75c9c-137">既定値は Text です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-137">The default is Text.</span></span><br /><br /> <span data-ttu-id="75c9c-138">この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-138">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="75c9c-139">name</span><span class="sxs-lookup"><span data-stu-id="75c9c-139">name</span></span>|<span data-ttu-id="75c9c-140">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-140">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="75c9c-141">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-141">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="75c9c-142">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="75c9c-142">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="75c9c-143">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75c9c-143">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="75c9c-144">openTimeout</span><span class="sxs-lookup"><span data-stu-id="75c9c-144">openTimeout</span></span>|<span data-ttu-id="75c9c-145">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="75c9c-146">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="75c9c-147">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-147">The default is 00:01:00.</span></span>|
|<span data-ttu-id="75c9c-148">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="75c9c-148">privacyNoticeAt</span></span>|<span data-ttu-id="75c9c-149">プライバシーに関する声明の場所を示す URI を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="75c9c-149">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="75c9c-150">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="75c9c-150">privacyNoticeVersion</span></span>|<span data-ttu-id="75c9c-151">現在のプライバシーに関する声明のバージョンを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="75c9c-151">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="75c9c-152">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="75c9c-152">proxyAddress</span></span>|<span data-ttu-id="75c9c-153">HTTP プロキシのアドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="75c9c-153">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="75c9c-154">`useDefaultWebProxy` が `true` の場合、この設定を `null` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-154">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="75c9c-155">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-155">The default is `null`.</span></span>|
|<span data-ttu-id="75c9c-156">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="75c9c-156">receiveTimeout</span></span>|<span data-ttu-id="75c9c-157">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="75c9c-158">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="75c9c-159">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-159">The default is 00:10:00.</span></span>|
|<span data-ttu-id="75c9c-160">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="75c9c-160">sendTimeout</span></span>|<span data-ttu-id="75c9c-161">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="75c9c-162">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="75c9c-163">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-163">The default is 00:01:00.</span></span>|
|<span data-ttu-id="75c9c-164">textEncoding</span><span class="sxs-lookup"><span data-stu-id="75c9c-164">textEncoding</span></span>|<span data-ttu-id="75c9c-165">バインディングでメッセージの発行に使用される文字セット エンコーディングを設定します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="75c9c-166">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="75c9c-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="75c9c-167">-BigEndianUnicode: Unicode BigEndian エンコード。</span><span class="sxs-lookup"><span data-stu-id="75c9c-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="75c9c-168">-Unicode:16 ビットエンコード。</span><span class="sxs-lookup"><span data-stu-id="75c9c-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="75c9c-169">-UTF8: 8 ビットエンコーディング</span><span class="sxs-lookup"><span data-stu-id="75c9c-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="75c9c-170">既定値は UTF8 です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-170">The default is UTF8.</span></span> <span data-ttu-id="75c9c-171">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-171">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="75c9c-172">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="75c9c-172">transactionFlow</span></span>|<span data-ttu-id="75c9c-173">バインディングが WS-Transactions のフローをサポートするかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-173">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="75c9c-174">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-174">The default is `false`.</span></span>|
|<span data-ttu-id="75c9c-175">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="75c9c-175">useDefaultWebProxy</span></span>|<span data-ttu-id="75c9c-176">システムの自動設定 HTTP プロキシを使用するかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="75c9c-176">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="75c9c-177">この属性が `null` の場合、プロキシ アドレスを `true` (つまり、設定しない) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-177">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="75c9c-178">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-178">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="75c9c-179">子要素</span><span class="sxs-lookup"><span data-stu-id="75c9c-179">Child Elements</span></span>

|<span data-ttu-id="75c9c-180">要素</span><span class="sxs-lookup"><span data-stu-id="75c9c-180">Element</span></span>|<span data-ttu-id="75c9c-181">説明</span><span class="sxs-lookup"><span data-stu-id="75c9c-181">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="75c9c-182">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-182">Defines the security settings for the message.</span></span> <span data-ttu-id="75c9c-183">この要素は <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-183">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="75c9c-184">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="75c9c-185">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="75c9c-186">チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-186">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="75c9c-187">親要素</span><span class="sxs-lookup"><span data-stu-id="75c9c-187">Parent Elements</span></span>

|<span data-ttu-id="75c9c-188">要素</span><span class="sxs-lookup"><span data-stu-id="75c9c-188">Element</span></span>|<span data-ttu-id="75c9c-189">説明</span><span class="sxs-lookup"><span data-stu-id="75c9c-189">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="75c9c-190">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="75c9c-190">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="75c9c-191">解説</span><span class="sxs-lookup"><span data-stu-id="75c9c-191">Remarks</span></span>

<span data-ttu-id="75c9c-192">フェデレーションは、複数のシステム間で認証と承認用の ID を共有する機能です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-192">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="75c9c-193">これらの ID は、ユーザーまたはコンピューターを参照できます。</span><span class="sxs-lookup"><span data-stu-id="75c9c-193">These identities can refer to users or to machines.</span></span> <span data-ttu-id="75c9c-194">フェデレーション HTTP は、SOAP セキュリティと混合モード セキュリティをサポートしますが、トランスポート セキュリティの単独使用はサポートしません。</span><span class="sxs-lookup"><span data-stu-id="75c9c-194">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="75c9c-195">このバインディングは、WS-Federation プロトコルに対して Windows Communication Foundation (WCF) のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="75c9c-195">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="75c9c-196">このバインディングで構成されたサービスは、HTTP トランスポートを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-196">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="75c9c-197">バインドは、バインド要素のスタックで構成されます。</span><span class="sxs-lookup"><span data-stu-id="75c9c-197">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="75c9c-198">内のバインド要素のスタック</span><span class="sxs-lookup"><span data-stu-id="75c9c-198">The stack of binding elements in</span></span>

<span data-ttu-id="75c9c-199">`wsFederationHttpBinding` のバインディング要素のスタックは、`wsHttpBinding` に含まれる</span><span class="sxs-lookup"><span data-stu-id="75c9c-199">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="75c9c-200">[\<security>](security-of-wsfederationhttpbinding.md)がの既定値に設定されている場合 <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> 。</span><span class="sxs-lookup"><span data-stu-id="75c9c-200">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="75c9c-201">は、の `wsFederationHttpBinding` メッセージセキュリティ設定の詳細を制御し [\<message>](message-element-of-wsfederationhttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="75c9c-201">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="75c9c-202">バインディング [\<security>](security-of-wsfederationhttpbinding.md) によって使用されるセキュリティは、バインディングの作成後に変更できないので、要素は get アクセスのみを提供することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="75c9c-202">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="75c9c-203">また、には、プライバシーに関する `wsFederationHttpBinding` 声明が存在する場所の URI を設定および取得するための privacyNoticeAt 属性も用意されています。</span><span class="sxs-lookup"><span data-stu-id="75c9c-203">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="75c9c-204">ポリシーをセキュリティで保護することが、フェデレーション シナリオでは特に重要です。</span><span class="sxs-lookup"><span data-stu-id="75c9c-204">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="75c9c-205">ポリシーを悪意のあるユーザーから保護するには、HTTPS などのセキュリティ形式の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="75c9c-205">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="75c9c-206">フェデレーション シナリオでこのバインディングを使用する場合は、発行済み (SAML) トークンの暗号化に使用するキー、トークンに入れるクレームの種類などの重要情報がサービス ポリシーに含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-206">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="75c9c-207">これが改ざんされると、攻撃者は発行済みトークンのキーを発見してさらに改ざんを行ったり、情報を暴露したりなどの悪意ある行動を取る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-207">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="75c9c-208">このような行為を防ぐには、(HTTPS などを使用して) ポリシーをセキュリティで保護し、サービスから安全に取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75c9c-208">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="75c9c-209">このバインディングの詳細については、「 [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75c9c-209">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="75c9c-210">例</span><span class="sxs-lookup"><span data-stu-id="75c9c-210">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsFederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="saml"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </wsFederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="75c9c-211">関連項目</span><span class="sxs-lookup"><span data-stu-id="75c9c-211">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="75c9c-212">方法: WSFederationHttpBinding を作成する</span><span class="sxs-lookup"><span data-stu-id="75c9c-212">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="75c9c-213">バインド</span><span class="sxs-lookup"><span data-stu-id="75c9c-213">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="75c9c-214">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="75c9c-214">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="75c9c-215">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="75c9c-215">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

---
description: '詳細情報: <udpDiscoveryEndpoint>'
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 9863b4bc768b9c1cca933d001f0db596ce502fa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749234"
---
# \<udpDiscoveryEndpoint>

<span data-ttu-id="66ca1-102">この構成要素は、UDP マルチキャスト バインディングを使用した探索操作用に事前に構成される標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="66ca1-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="66ca1-103">このエンドポイントには固定コントラクトがあり、WS-Discovery プロトコルの 2 つのバージョンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="66ca1-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="66ca1-104">また、WS-Discovery の仕様 (WS-Discovery April 2005 または WS-Discovery V1.1) に規定された固定 UDP バインディングと既定のアドレスも備えています。</span><span class="sxs-lookup"><span data-stu-id="66ca1-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="66ca1-105">構文</span><span class="sxs-lookup"><span data-stu-id="66ca1-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66ca1-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="66ca1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="66ca1-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="66ca1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66ca1-108">属性</span><span class="sxs-lookup"><span data-stu-id="66ca1-108">Attributes</span></span>  
  
|<span data-ttu-id="66ca1-109">属性</span><span class="sxs-lookup"><span data-stu-id="66ca1-109">Attribute</span></span>|<span data-ttu-id="66ca1-110">説明</span><span class="sxs-lookup"><span data-stu-id="66ca1-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66ca1-111">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="66ca1-111">discoveryMode</span></span>|<span data-ttu-id="66ca1-112">探索プロトコルのモードを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="66ca1-112">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="66ca1-113">有効な値は "アドホック" および "マネージ" です。</span><span class="sxs-lookup"><span data-stu-id="66ca1-113">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="66ca1-114">マネージド モードでは、プロトコルは Discoverable サービスのリポジトリとして機能する Discovery Proxy に依存します。</span><span class="sxs-lookup"><span data-stu-id="66ca1-114">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="66ca1-115">アドホック モードでは、プロトコルは UDP マルチキャスト メカニズムを使用して利用可能なサービスを探索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66ca1-115">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="66ca1-116">この値は、<xref:System.ServiceModel.Discovery.ServiceDiscoveryMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="66ca1-116">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="66ca1-117">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="66ca1-117">discoveryVersion</span></span>|<span data-ttu-id="66ca1-118">WS-Discovery プロトコルの 2 つのバージョンのうち、1 つを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="66ca1-118">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="66ca1-119">有効値は WSDiscovery11 と WSDiscoveryApril2005 です。</span><span class="sxs-lookup"><span data-stu-id="66ca1-119">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="66ca1-120">この値は、<xref:System.ServiceModel.Discovery.DiscoveryVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="66ca1-120">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="66ca1-121">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="66ca1-121">maxResponseDelay</span></span>|<span data-ttu-id="66ca1-122">Discovery プロトコルが Probe Match や Resolve Match などのメッセージを送信するまでの待機時間の最大値を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="66ca1-122">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="66ca1-123">すべての ProbeMatch が同時に送信されると、ネットワーク ストームが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="66ca1-123">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="66ca1-124">これを防ぐために、各 ProbeMatch はランダムな時間だけ待機して送信されます。</span><span class="sxs-lookup"><span data-stu-id="66ca1-124">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="66ca1-125">ランダムな待機時間は、0 からこの属性に設定された値の範囲内で設定されます。</span><span class="sxs-lookup"><span data-stu-id="66ca1-125">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="66ca1-126">この属性を 0 に設定すると、ProbeMatch メッセージは待機せずに短いループで送信されます。</span><span class="sxs-lookup"><span data-stu-id="66ca1-126">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="66ca1-127">それ以外の場合は、ProbeMatch メッセージはランダムな時間だけ待機して送信されます。すべての ProbeMatch メッセージの送信にかかる合計時間が maxResponseDelay を超えることはありません。</span><span class="sxs-lookup"><span data-stu-id="66ca1-127">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="66ca1-128">この値はサービスのみに関連するもので、クライアントが使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="66ca1-128">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="66ca1-129">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="66ca1-129">multicastAddress</span></span>|<span data-ttu-id="66ca1-130">探索メッセージの送受信に使用するマルチキャスト アドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="66ca1-130">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="66ca1-131">既定値は、プロトコル仕様に準じたマルチキャスト アドレスです。</span><span class="sxs-lookup"><span data-stu-id="66ca1-131">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="66ca1-132">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="66ca1-132">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="66ca1-133">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="66ca1-133">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66ca1-134">子要素</span><span class="sxs-lookup"><span data-stu-id="66ca1-134">Child Elements</span></span>  
  
|<span data-ttu-id="66ca1-135">要素</span><span class="sxs-lookup"><span data-stu-id="66ca1-135">Element</span></span>|<span data-ttu-id="66ca1-136">説明</span><span class="sxs-lookup"><span data-stu-id="66ca1-136">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="66ca1-137">UDP エンドポイントの UDP トランスポートを構成できる設定のコレクション。</span><span class="sxs-lookup"><span data-stu-id="66ca1-137">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66ca1-138">親要素</span><span class="sxs-lookup"><span data-stu-id="66ca1-138">Parent Elements</span></span>  
  
|<span data-ttu-id="66ca1-139">要素</span><span class="sxs-lookup"><span data-stu-id="66ca1-139">Element</span></span>|<span data-ttu-id="66ca1-140">説明</span><span class="sxs-lookup"><span data-stu-id="66ca1-140">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="66ca1-141">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="66ca1-141">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="66ca1-142">例</span><span class="sxs-lookup"><span data-stu-id="66ca1-142">Example</span></span>  

 <span data-ttu-id="66ca1-143">UDP マルチキャスト トランスポート経由で探索メッセージをリッスンするサービスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="66ca1-143">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="66ca1-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="66ca1-144">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

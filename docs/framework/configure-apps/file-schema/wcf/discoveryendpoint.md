---
description: '詳細情報: <discoveryEndpoint>'
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32be673aac9604d8285d002640f11a29b9545afb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802308"
---
# \<discoveryEndpoint>

<span data-ttu-id="6b206-102">この構成要素は、固定探索コントラクトが含まれた標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="6b206-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="6b206-103">サービスの構成に追加すると、この要素により、探索メッセージをリッスンする場所が指定されます。</span><span class="sxs-lookup"><span data-stu-id="6b206-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="6b206-104">クライアントの構成に追加すると、この要素により、探索クエリの送信先となる場所が指定されます。</span><span class="sxs-lookup"><span data-stu-id="6b206-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="6b206-105">構文</span><span class="sxs-lookup"><span data-stu-id="6b206-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b206-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="6b206-106">Attributes and elements</span></span>

<span data-ttu-id="6b206-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b206-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b206-108">属性</span><span class="sxs-lookup"><span data-stu-id="6b206-108">Attributes</span></span>

| <span data-ttu-id="6b206-109">属性</span><span class="sxs-lookup"><span data-stu-id="6b206-109">Attribute</span></span>        | <span data-ttu-id="6b206-110">説明</span><span class="sxs-lookup"><span data-stu-id="6b206-110">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="6b206-111">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="6b206-111">discoveryMode</span></span>    | <span data-ttu-id="6b206-112">探索プロトコルのモードを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="6b206-112">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="6b206-113">有効な値は "アドホック" および "マネージ" です。</span><span class="sxs-lookup"><span data-stu-id="6b206-113">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="6b206-114">マネージド モードでは、プロトコルは Discoverable サービスのリポジトリとして機能する Discovery Proxy に依存します。</span><span class="sxs-lookup"><span data-stu-id="6b206-114">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="6b206-115">アドホック モードでは、プロトコルは UDP マルチキャスト メカニズムを使用して利用可能なサービスを探索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b206-115">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="6b206-116">プロパティの詳細については、「」を参照してください <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6b206-116">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="6b206-117">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="6b206-117">discoveryVersion</span></span> | <span data-ttu-id="6b206-118">WS-Discovery プロトコルの 2 つのバージョンのうち、1 つを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="6b206-118">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="6b206-119">有効値は WSDiscovery11 と WSDiscoveryApril2005 です。</span><span class="sxs-lookup"><span data-stu-id="6b206-119">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="6b206-120">この値は、<xref:System.ServiceModel.Discovery.DiscoveryVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="6b206-120">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="6b206-121">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="6b206-121">maxResponseDelay</span></span> | <span data-ttu-id="6b206-122">Discovery プロトコルが Probe Match や Resolve Match などのメッセージを送信するまでの待機時間の最大値を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="6b206-122">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="6b206-123">すべての ProbeMatch が同時に送信されると、ネットワーク ストームが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="6b206-123">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="6b206-124">これを防ぐために、各 ProbeMatch はランダムな時間だけ待機して送信されます。</span><span class="sxs-lookup"><span data-stu-id="6b206-124">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="6b206-125">ランダムな待機時間は、0 からこの属性に設定された値の範囲内で設定されます。</span><span class="sxs-lookup"><span data-stu-id="6b206-125">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="6b206-126">この属性を 0 に設定すると、ProbeMatch メッセージは待機せずに短いループで送信されます。</span><span class="sxs-lookup"><span data-stu-id="6b206-126">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="6b206-127">それ以外の場合は、ProbeMatch メッセージはランダムな時間だけ待機して送信されます。すべての ProbeMatch メッセージの送信にかかる合計時間が maxResponseDelay を超えることはありません。</span><span class="sxs-lookup"><span data-stu-id="6b206-127">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="6b206-128">この値はサービスのみに関連するもので、クライアントが使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="6b206-128">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="6b206-129">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="6b206-129">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="6b206-130">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="6b206-130">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="6b206-131">子要素</span><span class="sxs-lookup"><span data-stu-id="6b206-131">Child elements</span></span>

<span data-ttu-id="6b206-132">なし。</span><span class="sxs-lookup"><span data-stu-id="6b206-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b206-133">親要素</span><span class="sxs-lookup"><span data-stu-id="6b206-133">Parent elements</span></span>

| <span data-ttu-id="6b206-134">要素</span><span class="sxs-lookup"><span data-stu-id="6b206-134">Element</span></span> | <span data-ttu-id="6b206-135">説明</span><span class="sxs-lookup"><span data-stu-id="6b206-135">Description</span></span> |  
| ------- | ----------- |  
| [\<standardEndpoints>](standardendpoints.md) | <span data-ttu-id="6b206-136">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="6b206-136">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="6b206-137">例</span><span class="sxs-lookup"><span data-stu-id="6b206-137">Example</span></span>

<span data-ttu-id="6b206-138">ピア ネットワーク マルチキャスト トランスポート経由で探索メッセージをリッスンするサービスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6b206-138">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="6b206-139">この例では、明示的に WS-Discovery April 2005 バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="6b206-139">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="6b206-140">標準エンドポイントの構成はサービスごとに定義します。サービス間で共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="6b206-140">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="6b206-141">別のサービスで同じ探索エンドポイントを使用するには、該当のサービスのセクションに同じ構成を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b206-141">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="6b206-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b206-142">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

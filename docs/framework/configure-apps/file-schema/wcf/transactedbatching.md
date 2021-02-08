---
description: '詳細情報: <transactedBatching>'
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 9a57226c3a2f2b026c69324e37b00e87fd3dd693
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773694"
---
# \<transactedBatching>

<span data-ttu-id="225a6-102">受信操作でトランザクション バッチがサポートされるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="225a6-102">Specifies whether transaction batching is supported for receive operations.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**  

## <a name="syntax"></a><span data-ttu-id="225a6-103">構文</span><span class="sxs-lookup"><span data-stu-id="225a6-103">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="225a6-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="225a6-104">Attributes and Elements</span></span>

<span data-ttu-id="225a6-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="225a6-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="225a6-106">属性</span><span class="sxs-lookup"><span data-stu-id="225a6-106">Attributes</span></span>

|<span data-ttu-id="225a6-107">属性</span><span class="sxs-lookup"><span data-stu-id="225a6-107">Attribute</span></span>|<span data-ttu-id="225a6-108">説明</span><span class="sxs-lookup"><span data-stu-id="225a6-108">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="225a6-109">1 回のトランザクションでまとめてバッチ処理できる受信操作の最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="225a6-109">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="225a6-110">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="225a6-110">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="225a6-111">子要素</span><span class="sxs-lookup"><span data-stu-id="225a6-111">Child Elements</span></span>

<span data-ttu-id="225a6-112">なし。</span><span class="sxs-lookup"><span data-stu-id="225a6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="225a6-113">親要素</span><span class="sxs-lookup"><span data-stu-id="225a6-113">Parent Elements</span></span>

|<span data-ttu-id="225a6-114">要素</span><span class="sxs-lookup"><span data-stu-id="225a6-114">Element</span></span>|<span data-ttu-id="225a6-115">説明</span><span class="sxs-lookup"><span data-stu-id="225a6-115">Description</span></span>|
|-------------|-----------------|
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="225a6-116">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="225a6-116">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="225a6-117">解説</span><span class="sxs-lookup"><span data-stu-id="225a6-117">Remarks</span></span>

<span data-ttu-id="225a6-118">トランザクション バッチで構成されるトランスポートは、複数の受信操作を 1 つのトランザクションにバッチ処理しようとします。</span><span class="sxs-lookup"><span data-stu-id="225a6-118">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="225a6-119">これを実行することにより、受信操作のたびに行うトランザクションの作成とそのコミットの比較的高いコストを回避できます。</span><span class="sxs-lookup"><span data-stu-id="225a6-119">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="225a6-120">例</span><span class="sxs-lookup"><span data-stu-id="225a6-120">Example</span></span>

<span data-ttu-id="225a6-121">構成ファイル内でサービスにトランザクション バッチ動作を追加する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="225a6-121">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

## <a name="see-also"></a><span data-ttu-id="225a6-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="225a6-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>

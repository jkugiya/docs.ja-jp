---
description: '詳細情報: <serviceThrottling>'
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: eb65f6d60a266a367789d87e4e6ea10ebfd2c7a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786682"
---
# \<serviceThrottling>

<span data-ttu-id="dd6a3-102">WCF (Windows Communication Foundation) サービスの調整機構を指定します。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
## <a name="syntax"></a><span data-ttu-id="dd6a3-103">構文</span><span class="sxs-lookup"><span data-stu-id="dd6a3-103">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd6a3-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dd6a3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="dd6a3-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd6a3-106">属性</span><span class="sxs-lookup"><span data-stu-id="dd6a3-106">Attributes</span></span>  
  
|<span data-ttu-id="dd6a3-107">属性</span><span class="sxs-lookup"><span data-stu-id="dd6a3-107">Attribute</span></span>|<span data-ttu-id="dd6a3-108">説明</span><span class="sxs-lookup"><span data-stu-id="dd6a3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd6a3-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="dd6a3-109">maxConcurrentCalls</span></span>|<span data-ttu-id="dd6a3-110"><xref:System.ServiceModel.ServiceHost> で同時に処理できるメッセージ数を制限する正の整数。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-110">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="dd6a3-111">制限を超える呼び出しはキューに格納されます。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-111">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="dd6a3-112">この値を 0 に設定することは、Int32.MaxValue に設定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-112">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="dd6a3-113">既定値は 16 x プロセッサ数です。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-113">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="dd6a3-114">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="dd6a3-114">maxConcurrentInstances</span></span>|<span data-ttu-id="dd6a3-115"><xref:System.ServiceModel.InstanceContext> で同時に実行できる <xref:System.ServiceModel.ServiceHost> オブジェクト数を制限する正の整数。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-115">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="dd6a3-116">追加インスタンスの作成要求は、キューに置かれ、制限下のスロットが利用できるようになったときに完了されます。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-116">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="dd6a3-117">既定値は maxConcurrentSessions と MaxConcurrentCalls の合計です。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-117">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="dd6a3-118">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="dd6a3-118">maxConcurrentSessions</span></span>|<span data-ttu-id="dd6a3-119"><xref:System.ServiceModel.ServiceHost> オブジェクトが受け入れることのできるセッション数を制限する正の整数。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-119">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="dd6a3-120">サービスは制限を超える接続を受け入れますが、制限内のチャネルだけがアクティブです (メッセージがチャネルから読み取られます)。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-120">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="dd6a3-121">この値を 0 に設定することは、Int32.MaxValue に設定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-121">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="dd6a3-122">既定値は 100 x プロセッサ数です。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-122">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd6a3-123">子要素</span><span class="sxs-lookup"><span data-stu-id="dd6a3-123">Child Elements</span></span>  

 <span data-ttu-id="dd6a3-124">なし。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd6a3-125">親要素</span><span class="sxs-lookup"><span data-stu-id="dd6a3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="dd6a3-126">要素</span><span class="sxs-lookup"><span data-stu-id="dd6a3-126">Element</span></span>|<span data-ttu-id="dd6a3-127">説明</span><span class="sxs-lookup"><span data-stu-id="dd6a3-127">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dd6a3-128">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-128">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd6a3-129">解説</span><span class="sxs-lookup"><span data-stu-id="dd6a3-129">Remarks</span></span>  

 <span data-ttu-id="dd6a3-130">調整コントロールは、同時呼び出し、同時インスタンス、または同時セッションの数を制限して、リソースの過剰消費を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-130">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="dd6a3-131">属性の値に到達するたびにトレースが出力されます。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-131">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="dd6a3-132">最初のトレースは警告として出力されます。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-132">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd6a3-133">例</span><span class="sxs-lookup"><span data-stu-id="dd6a3-133">Example</span></span>  

 <span data-ttu-id="dd6a3-134">次の構成例では、サービスで同時呼び出しの最大数を 2 に、同時インスタンスの最大数を 10 に制限することを指定しています。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-134">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="dd6a3-135">この例の実行例の詳細については、「 [調整](../../../wcf/samples/throttling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd6a3-135">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="dd6a3-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd6a3-136">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="dd6a3-137">WCF サービス パフォーマンスを制御するための ServiceThrottlingBehavior の使用</span><span class="sxs-lookup"><span data-stu-id="dd6a3-137">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)

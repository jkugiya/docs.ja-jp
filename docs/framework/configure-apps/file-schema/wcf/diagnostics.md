---
description: '詳細情報: <diagnostics>'
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: d1651d949cdc095e630e9cde0bacbe51a5eb6062
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782157"
---
# \<diagnostics>

<span data-ttu-id="966ef-102">`diagnostics` 要素は、ランタイムの検査と管理を行う管理者が使用できる設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="966ef-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="966ef-103">構文</span><span class="sxs-lookup"><span data-stu-id="966ef-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="966ef-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="966ef-104">Attributes and Elements</span></span>  

 <span data-ttu-id="966ef-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="966ef-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="966ef-106">属性</span><span class="sxs-lookup"><span data-stu-id="966ef-106">Attributes</span></span>  
  
|<span data-ttu-id="966ef-107">属性</span><span class="sxs-lookup"><span data-stu-id="966ef-107">Attribute</span></span>|<span data-ttu-id="966ef-108">説明</span><span class="sxs-lookup"><span data-stu-id="966ef-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="966ef-109">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="966ef-109">etwProviderId</span></span>|<span data-ttu-id="966ef-110">イベントを ETW セッションに書き込むイベント追跡プロバイダーの識別子を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="966ef-110">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="966ef-111">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="966ef-111">performanceCounters</span></span>|<span data-ttu-id="966ef-112">アセンブリのパフォーマンス カウンターが有効であるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="966ef-112">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="966ef-113">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="966ef-113">Valid values are</span></span><br /><br /> <span data-ttu-id="966ef-114">-Off: パフォーマンスカウンターが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="966ef-114">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="966ef-115">-ServiceOnly: このサービスに関連するパフォーマンスカウンターのみが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="966ef-115">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="966ef-116">-All: パフォーマンスカウンターは実行時に表示できます。</span><span class="sxs-lookup"><span data-stu-id="966ef-116">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="966ef-117">-Default: 1 つのパフォーマンスカウンターインスタンス _WCF_Admin が作成されます。</span><span class="sxs-lookup"><span data-stu-id="966ef-117">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="966ef-118">このインスタンスは、インフラストラクチャで使用される SQM データのコレクションを有効にするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="966ef-118">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="966ef-119">このインスタンスのカウンター値は更新されず、0 のままになります。</span><span class="sxs-lookup"><span data-stu-id="966ef-119">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="966ef-120">WCF の構成が存在しない場合は、これが既定値になります。</span><span class="sxs-lookup"><span data-stu-id="966ef-120">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="966ef-121">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="966ef-121">wmiProviderEnabled</span></span>|<span data-ttu-id="966ef-122">アセンブリの WMI プロバイダーが有効であるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="966ef-122">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="966ef-123">ユーザーが Windows Communication Foundation (WCF) の検査および制御機能に対する実行時アクセス権を取得するには、WMI プロバイダーが必要です。</span><span class="sxs-lookup"><span data-stu-id="966ef-123">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="966ef-124">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="966ef-124">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="966ef-125">子要素</span><span class="sxs-lookup"><span data-stu-id="966ef-125">Child Elements</span></span>  
  
|<span data-ttu-id="966ef-126">要素</span><span class="sxs-lookup"><span data-stu-id="966ef-126">Element</span></span>|<span data-ttu-id="966ef-127">説明</span><span class="sxs-lookup"><span data-stu-id="966ef-127">Description</span></span>|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|<span data-ttu-id="966ef-128">サービス アプリケーションの実行中にエンドツーエンドのトレースのさまざまな側面を有効または無効にするための構成要素。</span><span class="sxs-lookup"><span data-stu-id="966ef-128">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[\<messageLogging>](messagelogging.md)|<span data-ttu-id="966ef-129">WCF メッセージ ログの設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="966ef-129">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="966ef-130">親要素</span><span class="sxs-lookup"><span data-stu-id="966ef-130">Parent Elements</span></span>  
  
|<span data-ttu-id="966ef-131">要素</span><span class="sxs-lookup"><span data-stu-id="966ef-131">Element</span></span>|<span data-ttu-id="966ef-132">説明</span><span class="sxs-lookup"><span data-stu-id="966ef-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="966ef-133">serviceModel</span><span class="sxs-lookup"><span data-stu-id="966ef-133">serviceModel</span></span>|<span data-ttu-id="966ef-134">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="966ef-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="966ef-135">解説</span><span class="sxs-lookup"><span data-stu-id="966ef-135">Remarks</span></span>  

 <span data-ttu-id="966ef-136">`diagnostics` セクションは、アセンブリに配置されるすべてのサービスの診断設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="966ef-136">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="966ef-137">アセンブリ内のサービスが 1 つでない限り、サービス レベル別に診断設定を定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="966ef-137">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="966ef-138">属性は、セクションの要件に応じて設定されます。</span><span class="sxs-lookup"><span data-stu-id="966ef-138">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="966ef-139">例</span><span class="sxs-lookup"><span data-stu-id="966ef-139">Example</span></span>  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
                  logMalformedMessages="true"
                  logMessagesAtServiceLevel="true"
                  logMessagesAtTransportLevel="true"
                  maxMessagesToLog="42"
                  maxSizeOfMessageToLog="42">
    <filters>
      <clear />
    </filters>
  </messageLogging>
</diagnostics>
```  
  
## <a name="see-also"></a><span data-ttu-id="966ef-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="966ef-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>

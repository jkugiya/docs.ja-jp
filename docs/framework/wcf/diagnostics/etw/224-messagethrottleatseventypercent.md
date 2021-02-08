---
description: '詳細情報: 224-MessageThrottleAtSeventyPercent'
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: 14c08371c5db7e6f7deb0a5851a1d24dfc94475e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794274"
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="f091b-103">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="f091b-103">224 - MessageThrottleAtSeventyPercent</span></span>

## <a name="properties"></a><span data-ttu-id="f091b-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f091b-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f091b-105">id</span><span class="sxs-lookup"><span data-stu-id="f091b-105">ID</span></span>|<span data-ttu-id="f091b-106">224</span><span class="sxs-lookup"><span data-stu-id="f091b-106">224</span></span>|  
|<span data-ttu-id="f091b-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="f091b-107">Keywords</span></span>|<span data-ttu-id="f091b-108">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f091b-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f091b-109">Level</span><span class="sxs-lookup"><span data-stu-id="f091b-109">Level</span></span>|<span data-ttu-id="f091b-110">警告</span><span class="sxs-lookup"><span data-stu-id="f091b-110">Warning</span></span>|  
|<span data-ttu-id="f091b-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="f091b-111">Channel</span></span>|<span data-ttu-id="f091b-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f091b-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f091b-113">説明</span><span class="sxs-lookup"><span data-stu-id="f091b-113">Description</span></span>  

 <span data-ttu-id="f091b-114">`MessageThrottleExceeded` イベントは、主要なサービス スロットルの 1 つを超過したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="f091b-114">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="f091b-115">アクティビティの急増が緩やかになり、スロットルの現在の値が現在の制限の 70% である場合は、このイベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f091b-115">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="f091b-116">このイベントは、アクティビティが緩やかになったときに一度だけ生成されます。</span><span class="sxs-lookup"><span data-stu-id="f091b-116">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="f091b-117">現在の値が 70% の基準付近を上下している (70、69、70、71、70、69 など) 場合は、最初に 70% に達したときにイベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f091b-117">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="f091b-118">このイベントが生成された後にスロットル制限を超えた場合は、`MessageThrottleExceeded` イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f091b-118">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f091b-119">Message</span><span class="sxs-lookup"><span data-stu-id="f091b-119">Message</span></span>  

 <span data-ttu-id="f091b-120">スロットル '%1' の '%2' の制限は 70%% です。</span><span class="sxs-lookup"><span data-stu-id="f091b-120">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f091b-121">詳細</span><span class="sxs-lookup"><span data-stu-id="f091b-121">Details</span></span>  
  
|<span data-ttu-id="f091b-122">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f091b-122">Data Item Name</span></span>|<span data-ttu-id="f091b-123">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f091b-123">Data Item Type</span></span>|<span data-ttu-id="f091b-124">説明</span><span class="sxs-lookup"><span data-stu-id="f091b-124">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f091b-125">Throttle Name</span><span class="sxs-lookup"><span data-stu-id="f091b-125">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="f091b-126">超過したスロットルの名前。</span><span class="sxs-lookup"><span data-stu-id="f091b-126">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="f091b-127">`MaxConcurrentCalls`、`MaxConcurrentInstances`、または `MaxConcurrentSessions`。</span><span class="sxs-lookup"><span data-stu-id="f091b-127">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="f091b-128">制限</span><span class="sxs-lookup"><span data-stu-id="f091b-128">Limit</span></span>|`xs:long`|<span data-ttu-id="f091b-129">現在構成されている、スロットルの制限。</span><span class="sxs-lookup"><span data-stu-id="f091b-129">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="f091b-130">HostReference</span><span class="sxs-lookup"><span data-stu-id="f091b-130">HostReference</span></span>|`xs:string`|<span data-ttu-id="f091b-131">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="f091b-131">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f091b-132">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="f091b-132">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f091b-133">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="f091b-133">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f091b-134">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f091b-134">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f091b-135">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f091b-135">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

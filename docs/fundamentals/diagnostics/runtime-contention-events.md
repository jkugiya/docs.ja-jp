---
title: モニターのロック競合ランタイム イベント
description: モニターのロック競合に固有の情報を収集する ETW イベントを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594054"
---
# <a name="net-runtime-contention-events"></a><span data-ttu-id="87c47-103">.NET ランタイム競合イベント</span><span class="sxs-lookup"><span data-stu-id="87c47-103">.NET runtime contention events</span></span>

<span data-ttu-id="87c47-104">これらのランタイム イベントは、`Monitor.Enter` または C# の lock キーワードなど、モニターのロック競合に関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="87c47-104">These runtime events capture information about monitor lock contentions such as with `Monitor.Enter` or the C# lock keyword.</span></span> <span data-ttu-id="87c47-105">診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="87c47-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="contentionstart_v1-event"></a><span data-ttu-id="87c47-106">ContentionStart_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="87c47-106">ContentionStart_V1 event</span></span>

<span data-ttu-id="87c47-107">このイベントは、モニターのロック競合の開始時に生成されます。</span><span class="sxs-lookup"><span data-stu-id="87c47-107">This event is emitted at the start of a monitor lock contention.</span></span>

|<span data-ttu-id="87c47-108">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="87c47-108">Keyword for raising the event</span></span>|<span data-ttu-id="87c47-109">Level</span><span class="sxs-lookup"><span data-stu-id="87c47-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="87c47-110">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="87c47-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="87c47-111">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="87c47-111">Informational (4)</span></span>|

 <span data-ttu-id="87c47-112">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="87c47-112">The following table shows event information.</span></span>

|<span data-ttu-id="87c47-113">Event</span><span class="sxs-lookup"><span data-stu-id="87c47-113">Event</span></span>|<span data-ttu-id="87c47-114">イベント ID</span><span class="sxs-lookup"><span data-stu-id="87c47-114">Event ID</span></span>|<span data-ttu-id="87c47-115">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="87c47-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="87c47-116">81</span><span class="sxs-lookup"><span data-stu-id="87c47-116">81</span></span>|<span data-ttu-id="87c47-117">モニターのロック競合が開始します。</span><span class="sxs-lookup"><span data-stu-id="87c47-117">A monitor lock contention starts.</span></span>|

|<span data-ttu-id="87c47-118">フィールド名</span><span class="sxs-lookup"><span data-stu-id="87c47-118">Field name</span></span>|<span data-ttu-id="87c47-119">データ型</span><span class="sxs-lookup"><span data-stu-id="87c47-119">Data type</span></span>|<span data-ttu-id="87c47-120">説明</span><span class="sxs-lookup"><span data-stu-id="87c47-120">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="87c47-121">マネージドの場合は `0`、ネイティブの場合は `1` です。</span><span class="sxs-lookup"><span data-stu-id="87c47-121">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="87c47-122">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="87c47-122">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="contentionstop_v1-event"></a><span data-ttu-id="87c47-123">ContentionStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="87c47-123">ContentionStop_V1 event</span></span>

<span data-ttu-id="87c47-124">このイベントは、モニターのロック競合の終了時に生成されます。</span><span class="sxs-lookup"><span data-stu-id="87c47-124">This event is emitted at the end of a monitor lock contention.</span></span>

|<span data-ttu-id="87c47-125">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="87c47-125">Keyword for raising the event</span></span>|<span data-ttu-id="87c47-126">Level</span><span class="sxs-lookup"><span data-stu-id="87c47-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="87c47-127">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="87c47-127">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="87c47-128">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="87c47-128">Informational (4)</span></span>|

 <span data-ttu-id="87c47-129">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="87c47-129">The following table shows event information.</span></span>

|<span data-ttu-id="87c47-130">Event</span><span class="sxs-lookup"><span data-stu-id="87c47-130">Event</span></span>|<span data-ttu-id="87c47-131">イベント ID</span><span class="sxs-lookup"><span data-stu-id="87c47-131">Event ID</span></span>|<span data-ttu-id="87c47-132">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="87c47-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|<span data-ttu-id="87c47-133">91</span><span class="sxs-lookup"><span data-stu-id="87c47-133">91</span></span>|<span data-ttu-id="87c47-134">モニターのロック競合が終了します。</span><span class="sxs-lookup"><span data-stu-id="87c47-134">A monitor lock contention ends.</span></span>|

|<span data-ttu-id="87c47-135">フィールド名</span><span class="sxs-lookup"><span data-stu-id="87c47-135">Field name</span></span>|<span data-ttu-id="87c47-136">データ型</span><span class="sxs-lookup"><span data-stu-id="87c47-136">Data type</span></span>|<span data-ttu-id="87c47-137">説明</span><span class="sxs-lookup"><span data-stu-id="87c47-137">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="87c47-138">マネージドの場合は `0`、ネイティブの場合は `1` です。</span><span class="sxs-lookup"><span data-stu-id="87c47-138">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="87c47-139">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="87c47-139">Unique ID for the instance of CoreCLR.</span></span>|
|`DurationNs`|`win:Double`|<span data-ttu-id="87c47-140">競合の継続時間 (ナノ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="87c47-140">Duration of the contention in nanoseconds.</span></span>|

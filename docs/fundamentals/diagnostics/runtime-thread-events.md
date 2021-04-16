---
title: ThreadPool ランタイム イベント
description: .NET Core のスレッド プールに関する診断情報を収集する .NET ランタイム スレッド プール イベントを参照してください。 スレッド プール イベントは、ワーカー スレッド プール イベントまたは I/O スレッド プール イベントです。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594121"
---
# <a name="net-runtime-thread-pool-events"></a><span data-ttu-id="4e756-104">.NET ランタイム スレッド プール イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-104">.NET runtime thread pool events</span></span>

<span data-ttu-id="4e756-105">これらのイベントは、スレッドプールのワーカー スレッドと I/O スレッドに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="4e756-105">These events collect information about worker and I/O threads in the threadpool.</span></span> <span data-ttu-id="4e756-106">診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e756-106">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="iothreadcreate_v1-event"></a><span data-ttu-id="4e756-107">IOThreadCreate_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-107">IOThreadCreate_V1 event</span></span>

 <span data-ttu-id="4e756-108">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-108">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-109">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-109">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-110">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-110">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-111">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-111">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-112">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-112">Informational (4)</span></span>|

 <span data-ttu-id="4e756-113">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-113">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-114">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-114">Event</span></span>|<span data-ttu-id="4e756-115">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-115">Event ID</span></span>|<span data-ttu-id="4e756-116">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="4e756-116">Raised when</span></span>|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|<span data-ttu-id="4e756-117">44</span><span class="sxs-lookup"><span data-stu-id="4e756-117">44</span></span>|<span data-ttu-id="4e756-118">I/O スレッドがスレッド プールに作成された。</span><span class="sxs-lookup"><span data-stu-id="4e756-118">An I/O thread is created in the thread pool.</span></span>|

 <span data-ttu-id="4e756-119">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-119">The following table shows the event data.</span></span>

|<span data-ttu-id="4e756-120">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-120">Field name</span></span>|<span data-ttu-id="4e756-121">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-121">Data type</span></span>|<span data-ttu-id="4e756-122">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-122">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="4e756-123">新しく作成されたスレッドを含む、I/O のスレッドの数です。</span><span class="sxs-lookup"><span data-stu-id="4e756-123">Number of I/O threads, including the newly created thread.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="4e756-124">提供終了になったワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-124">Number of retired worker threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-125">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-125">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadterminate_v1-event"></a><span data-ttu-id="4e756-126">IOThreadTerminate_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-126">IOThreadTerminate_V1 event</span></span>

 <span data-ttu-id="4e756-127">次の表に、キーワードとレベルを示します</span><span class="sxs-lookup"><span data-stu-id="4e756-127">The following table shows the keyword and level</span></span>

|<span data-ttu-id="4e756-128">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-128">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-129">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-129">Level</span></span>
|-----------------------------------|-----------
|<span data-ttu-id="4e756-130">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-130">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-131">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-131">Informational (4)</span></span>

 <span data-ttu-id="4e756-132">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-132">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-133">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-133">Event</span></span>|<span data-ttu-id="4e756-134">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-134">Event ID</span></span>|<span data-ttu-id="4e756-135">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="4e756-135">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|<span data-ttu-id="4e756-136">45</span><span class="sxs-lookup"><span data-stu-id="4e756-136">45</span></span>|<span data-ttu-id="4e756-137">スレッド プール内の I/O スレッドが終了した。</span><span class="sxs-lookup"><span data-stu-id="4e756-137">An I/O thread is terminated in the thread pool.</span></span>|

 <span data-ttu-id="4e756-138">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-138">The following table shows the event data.</span></span>

|<span data-ttu-id="4e756-139">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-139">Field name</span></span>|<span data-ttu-id="4e756-140">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-140">Data type</span></span>|<span data-ttu-id="4e756-141">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-141">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="4e756-142">スレッド プールに残っている I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-142">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="4e756-143">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-143">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-144">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadretire_v1-event"></a><span data-ttu-id="4e756-145">IOThreadRetire_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-145">IOThreadRetire_V1 event</span></span>

 <span data-ttu-id="4e756-146">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-146">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-147">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-147">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-148">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-149">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-149">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-150">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-150">Informational (4)</span></span>|

 <span data-ttu-id="4e756-151">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-151">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-152">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-152">Event</span></span>|<span data-ttu-id="4e756-153">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-153">Event ID</span></span>|<span data-ttu-id="4e756-154">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="4e756-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|<span data-ttu-id="4e756-155">46</span><span class="sxs-lookup"><span data-stu-id="4e756-155">46</span></span>|<span data-ttu-id="4e756-156">I/O スレッドが、提供終了の候補になる。</span><span class="sxs-lookup"><span data-stu-id="4e756-156">An I/O thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="4e756-157">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-157">The following table shows the event data.</span></span>

|<span data-ttu-id="4e756-158">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-158">Field name</span></span>|<span data-ttu-id="4e756-159">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-159">Data type</span></span>|<span data-ttu-id="4e756-160">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-160">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="4e756-161">スレッド プールに残っている I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-161">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="4e756-162">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-162">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-163">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadunretire_v1-event"></a><span data-ttu-id="4e756-164">IOThreadUnretire_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-164">IOThreadUnretire_V1 event</span></span>

 <span data-ttu-id="4e756-165">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-165">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-166">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-166">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-167">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-168">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-168">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-169">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-169">Informational (4)</span></span>|

 <span data-ttu-id="4e756-170">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-170">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-171">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-171">Event</span></span>|<span data-ttu-id="4e756-172">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-172">Event ID</span></span>|<span data-ttu-id="4e756-173">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="4e756-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|<span data-ttu-id="4e756-174">47</span><span class="sxs-lookup"><span data-stu-id="4e756-174">47</span></span>|<span data-ttu-id="4e756-175">スレッドが提供終了の候補になってから待機期間内に I/O が到着したため I/O スレッドが提供終了解除された。</span><span class="sxs-lookup"><span data-stu-id="4e756-175">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="4e756-176">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-176">The following table shows the event data.</span></span>

|<span data-ttu-id="4e756-177">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-177">Field name</span></span>|<span data-ttu-id="4e756-178">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-178">Data type</span></span>|<span data-ttu-id="4e756-179">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-179">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="4e756-180">これを含む、スレッド プール内の I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-180">Number of I/O threads in the thread pool, including this one.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="4e756-181">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-181">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`Win:UInt16`|<span data-ttu-id="4e756-182">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-182">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstart-event"></a><span data-ttu-id="4e756-183">ThreadPoolWorkerThreadStart イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-183">ThreadPoolWorkerThreadStart event</span></span>

|<span data-ttu-id="4e756-184">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-184">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-185">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-185">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="4e756-186">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-186">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-187">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-187">Informational (4)</span></span>|

|<span data-ttu-id="4e756-188">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-188">Event</span></span>|<span data-ttu-id="4e756-189">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-189">Event ID</span></span>|<span data-ttu-id="4e756-190">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-190">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="4e756-191">50</span><span class="sxs-lookup"><span data-stu-id="4e756-191">50</span></span>|<span data-ttu-id="4e756-192">ワーカー スレッドが作成された。</span><span class="sxs-lookup"><span data-stu-id="4e756-192">A worker thread is created.</span></span>|

|<span data-ttu-id="4e756-193">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-193">Field name</span></span>|<span data-ttu-id="4e756-194">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-194">Data type</span></span>|<span data-ttu-id="4e756-195">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-195">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-196">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="4e756-196">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-197">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-197">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-198">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-198">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstop-event"></a><span data-ttu-id="4e756-199">ThreadPoolWorkerThreadStop イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-199">ThreadPoolWorkerThreadStop event</span></span>

|<span data-ttu-id="4e756-200">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-200">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-201">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-201">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="4e756-202">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-202">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-203">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-203">Informational (4)</span></span>|

|<span data-ttu-id="4e756-204">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-204">Event</span></span>|<span data-ttu-id="4e756-205">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-205">Event ID</span></span>|<span data-ttu-id="4e756-206">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-206">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="4e756-207">51</span><span class="sxs-lookup"><span data-stu-id="4e756-207">51</span></span>|<span data-ttu-id="4e756-208">ワーカー スレッドが停止された。</span><span class="sxs-lookup"><span data-stu-id="4e756-208">A worker thread is stopped.</span></span>|

|<span data-ttu-id="4e756-209">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-209">Field name</span></span>|<span data-ttu-id="4e756-210">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-210">Data type</span></span>|<span data-ttu-id="4e756-211">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-211">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-212">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="4e756-212">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-213">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-213">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-214">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-214">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadwait-event"></a><span data-ttu-id="4e756-215">ThreadPoolWorkerThreadWait イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-215">ThreadPoolWorkerThreadWait event</span></span>

|<span data-ttu-id="4e756-216">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-216">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-217">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-217">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="4e756-218">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-218">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-219">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-219">Informational (4)</span></span>|

|<span data-ttu-id="4e756-220">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-220">Event</span></span>|<span data-ttu-id="4e756-221">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-221">Event ID</span></span>|<span data-ttu-id="4e756-222">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-222">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|<span data-ttu-id="4e756-223">57</span><span class="sxs-lookup"><span data-stu-id="4e756-223">57</span></span>|<span data-ttu-id="4e756-224">ワーカー スレッドが作業の待機を開始します。</span><span class="sxs-lookup"><span data-stu-id="4e756-224">A worker thread starts waiting for work.</span></span>|

|<span data-ttu-id="4e756-225">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-225">Field name</span></span>|<span data-ttu-id="4e756-226">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-226">Data type</span></span>|<span data-ttu-id="4e756-227">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-227">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-228">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="4e756-228">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-229">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-229">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-230">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-230">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstart-event"></a><span data-ttu-id="4e756-231">ThreadPoolWorkerThreadRetirementStart イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-231">ThreadPoolWorkerThreadRetirementStart event</span></span>

|<span data-ttu-id="4e756-232">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-232">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-233">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-233">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="4e756-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-235">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-235">Informational (4)</span></span>|

|<span data-ttu-id="4e756-236">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-236">Event</span></span>|<span data-ttu-id="4e756-237">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-237">Event ID</span></span>|<span data-ttu-id="4e756-238">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-238">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="4e756-239">52</span><span class="sxs-lookup"><span data-stu-id="4e756-239">52</span></span>|<span data-ttu-id="4e756-240">ワーカー スレッドが無効にされた。</span><span class="sxs-lookup"><span data-stu-id="4e756-240">A worker thread retires.</span></span>|

|<span data-ttu-id="4e756-241">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-241">Field name</span></span>|<span data-ttu-id="4e756-242">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-242">Data type</span></span>|<span data-ttu-id="4e756-243">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-243">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-244">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="4e756-244">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-245">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-245">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-246">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstop-event"></a><span data-ttu-id="4e756-247">ThreadPoolWorkerThreadRetirementStop イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-247">ThreadPoolWorkerThreadRetirementStop event</span></span>

|<span data-ttu-id="4e756-248">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-248">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-249">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-249">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="4e756-250">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-250">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-251">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-251">Informational (4)</span></span>|

|<span data-ttu-id="4e756-252">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-252">Event</span></span>|<span data-ttu-id="4e756-253">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-253">Event ID</span></span>|<span data-ttu-id="4e756-254">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-254">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="4e756-255">53</span><span class="sxs-lookup"><span data-stu-id="4e756-255">53</span></span>|<span data-ttu-id="4e756-256">提供終了になったワーカー スレッドが再びアクティブになった。</span><span class="sxs-lookup"><span data-stu-id="4e756-256">A retired worker thread becomes active again.</span></span>|

|<span data-ttu-id="4e756-257">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-257">Field name</span></span>|<span data-ttu-id="4e756-258">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-258">Data type</span></span>|<span data-ttu-id="4e756-259">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-259">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-260">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="4e756-260">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-261">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-261">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-262">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-262">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a><span data-ttu-id="4e756-263">ThreadPoolWorkerThreadAdjustmentSample イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-263">ThreadPoolWorkerThreadAdjustmentSample event</span></span>

 <span data-ttu-id="4e756-264">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-264">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-265">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-265">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-266">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-266">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-267">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-267">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-268">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-268">Informational (4)</span></span>|

 <span data-ttu-id="4e756-269">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-269">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-270">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-270">Event</span></span>|<span data-ttu-id="4e756-271">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-271">Event ID</span></span>|<span data-ttu-id="4e756-272">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-272">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="4e756-273">54</span><span class="sxs-lookup"><span data-stu-id="4e756-273">54</span></span>|<span data-ttu-id="4e756-274">1 つのサンプルの情報のコレクションを参照します。つまり、特定のコンカレンシー レベルの特定の時刻におけるスループットの測定値です。</span><span class="sxs-lookup"><span data-stu-id="4e756-274">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|

 <span data-ttu-id="4e756-275">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-275">The following table shows the event data.</span></span>

|<span data-ttu-id="4e756-276">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-276">Field name</span></span>|<span data-ttu-id="4e756-277">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-277">Data type</span></span>|<span data-ttu-id="4e756-278">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-278">Description</span></span>|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|<span data-ttu-id="4e756-279">時間の単位あたりの入力候補の数です。</span><span class="sxs-lookup"><span data-stu-id="4e756-279">Number of completions per unit of time.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-280">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a><span data-ttu-id="4e756-281">ThreadPoolWorkerThreadAdjustmentAdjustment イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-281">ThreadPoolWorkerThreadAdjustmentAdjustment event</span></span>

 <span data-ttu-id="4e756-282">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-282">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-283">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-283">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-284">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-284">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-286">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-286">Informational (4)</span></span>|

 <span data-ttu-id="4e756-287">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-287">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-288">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-288">Event</span></span>|<span data-ttu-id="4e756-289">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-289">Event ID</span></span>|<span data-ttu-id="4e756-290">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-290">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="4e756-291">55</span><span class="sxs-lookup"><span data-stu-id="4e756-291">55</span></span>|<span data-ttu-id="4e756-292">スレッドの挿入 (山登り法) アルゴリズムが、コンカレンシー レベルに変更があったと判断した場合に、コントロールの変更を記録します。</span><span class="sxs-lookup"><span data-stu-id="4e756-292">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|

 <span data-ttu-id="4e756-293">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-293">The following table shows the event data.</span></span>

|<span data-ttu-id="4e756-294">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-294">Field name</span></span>|<span data-ttu-id="4e756-295">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-295">Data type</span></span>|<span data-ttu-id="4e756-296">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-296">Description</span></span>|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|<span data-ttu-id="4e756-297">計測のサンプルの平均のスループット。</span><span class="sxs-lookup"><span data-stu-id="4e756-297">Average throughput of a sample of measurements.</span></span>|
|`NewWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="4e756-298">新しいアクティブなワーカー スレッド数。</span><span class="sxs-lookup"><span data-stu-id="4e756-298">New number of active worker threads.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="4e756-299">調整の理由。</span><span class="sxs-lookup"><span data-stu-id="4e756-299">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="4e756-300">`0x0` - ウォームアップ。</span><span class="sxs-lookup"><span data-stu-id="4e756-300">`0x0` - Warmup.</span></span><br /><br /> <span data-ttu-id="4e756-301">`0x1` - 初期化中。</span><span class="sxs-lookup"><span data-stu-id="4e756-301">`0x1` - Initializing.</span></span><br /><br /> <span data-ttu-id="4e756-302">`0x2` - ランダムな移動。</span><span class="sxs-lookup"><span data-stu-id="4e756-302">`0x2` - Random move.</span></span><br /><br /> <span data-ttu-id="4e756-303">`0x3` - 上昇移動。</span><span class="sxs-lookup"><span data-stu-id="4e756-303">`0x3` - Climbing move.</span></span><br /><br /> <span data-ttu-id="4e756-304">`0x4` - 変更点。</span><span class="sxs-lookup"><span data-stu-id="4e756-304">`0x4` - Change point.</span></span><br /><br /> <span data-ttu-id="4e756-305">`0x5` - 安定化。</span><span class="sxs-lookup"><span data-stu-id="4e756-305">`0x5` - Stabilizing.</span></span><br /><br /> <span data-ttu-id="4e756-306">`0x6` - 不足。</span><span class="sxs-lookup"><span data-stu-id="4e756-306">`0x6` - Starvation.</span></span><br /><br /> <span data-ttu-id="4e756-307">`0x7` - スレッドのタイムアウト。</span><span class="sxs-lookup"><span data-stu-id="4e756-307">`0x7` - Thread timed out.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-308">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-308">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a><span data-ttu-id="4e756-309">ThreadPoolWorkerThreadAdjustmentStats イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-309">ThreadPoolWorkerThreadAdjustmentStats event</span></span>

 <span data-ttu-id="4e756-310">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-310">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-311">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-311">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-312">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-312">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-313">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-313">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-314">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="4e756-314">Verbose (5)</span></span>

 <span data-ttu-id="4e756-315">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-315">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-316">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-316">Event</span></span>|<span data-ttu-id="4e756-317">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-317">Event ID</span></span>|<span data-ttu-id="4e756-318">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-318">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="4e756-319">56</span><span class="sxs-lookup"><span data-stu-id="4e756-319">56</span></span>|<span data-ttu-id="4e756-320">スレッド プールに関するデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="4e756-320">Gathers data on the thread pool.</span></span>|

 <span data-ttu-id="4e756-321">次の表に、イベント データを示します</span><span class="sxs-lookup"><span data-stu-id="4e756-321">The following table shows the event data</span></span>

|<span data-ttu-id="4e756-322">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-322">Field name</span></span>|<span data-ttu-id="4e756-323">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-323">Data type</span></span>|<span data-ttu-id="4e756-324">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-324">Description</span></span>|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|<span data-ttu-id="4e756-325">これらの統計情報が収集される時間数 (秒)。</span><span class="sxs-lookup"><span data-stu-id="4e756-325">Amount of time, in seconds, during which these statistics were collected.</span></span>|
|`Throughput`|`win:Double`|<span data-ttu-id="4e756-326">この間隔中の 1 秒あたりの入力候補の平均数。</span><span class="sxs-lookup"><span data-stu-id="4e756-326">Average number of completions per second during this interval.</span></span>|
|`ThreadWave`|`win:Double`|<span data-ttu-id="4e756-327">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-327">Reserved for internal use.</span></span>|
|`ThroughputWave`|`win:Double`|<span data-ttu-id="4e756-328">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-328">Reserved for internal use.</span></span>|
|`ThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="4e756-329">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-329">Reserved for internal use.</span></span>|
|`AverageThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="4e756-330">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-330">Reserved for internal use.</span></span>|
|`ThroughputRatio`|`win:Double`|<span data-ttu-id="4e756-331">この間隔中にアクティブなワーカー スレッドの数の変動によって引き起こされる、スループットの相対的な向上。</span><span class="sxs-lookup"><span data-stu-id="4e756-331">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|
|`Confidence`|`win:Double`|<span data-ttu-id="4e756-332">ThroughputRatio フィールドの有効性の測定結果。</span><span class="sxs-lookup"><span data-stu-id="4e756-332">A measure of the validity of the ThroughputRatio field.</span></span>|
|`NewcontrolSetting`|`win:Double`|<span data-ttu-id="4e756-333">アクティブなスレッド数の将来のバリエーションのベースラインとして使用するアクティブなワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="4e756-333">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|
|`NewThreadWaveMagnitude`|`win:UInt16`|<span data-ttu-id="4e756-334">アクティブなスレッド数の、将来のバリエーションの大きさを指定します。</span><span class="sxs-lookup"><span data-stu-id="4e756-334">The magnitude of future variations in active thread count.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-335">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-335">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolenqueue-event"></a><span data-ttu-id="4e756-336">ThreadPoolEnqueue イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-336">ThreadPoolEnqueue event</span></span>

 <span data-ttu-id="4e756-337">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-337">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-338">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-338">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-339">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-339">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-340">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-340">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-341">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="4e756-341">Verbose (5)</span></span>

 <span data-ttu-id="4e756-342">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-342">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-343">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-343">Event</span></span>|<span data-ttu-id="4e756-344">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-344">Event ID</span></span>|<span data-ttu-id="4e756-345">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-345">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|<span data-ttu-id="4e756-346">61</span><span class="sxs-lookup"><span data-stu-id="4e756-346">61</span></span>|<span data-ttu-id="4e756-347">作業項目がスレッド プールキューにエンキューされました。</span><span class="sxs-lookup"><span data-stu-id="4e756-347">A work item was enqueued in the thread pool queue.</span></span>|

 <span data-ttu-id="4e756-348">次の表に、イベント データを示します</span><span class="sxs-lookup"><span data-stu-id="4e756-348">The following table shows the event data</span></span>

|<span data-ttu-id="4e756-349">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-349">Field name</span></span>|<span data-ttu-id="4e756-350">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-350">Data type</span></span>|<span data-ttu-id="4e756-351">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-351">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="4e756-352">作業要求へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4e756-352">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-353">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-353">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooldequeue-event"></a><span data-ttu-id="4e756-354">ThreadPoolDequeue イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-354">ThreadPoolDequeue event</span></span>

 <span data-ttu-id="4e756-355">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-355">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-356">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-356">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-357">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-357">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-358">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-358">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-359">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="4e756-359">Verbose (5)</span></span>

 <span data-ttu-id="4e756-360">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-360">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-361">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-361">Event</span></span>|<span data-ttu-id="4e756-362">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-362">Event ID</span></span>|<span data-ttu-id="4e756-363">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-363">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|<span data-ttu-id="4e756-364">62</span><span class="sxs-lookup"><span data-stu-id="4e756-364">62</span></span>|<span data-ttu-id="4e756-365">作業項目がスレッド プール キューからデキューされました。</span><span class="sxs-lookup"><span data-stu-id="4e756-365">A work item was dequeued from the thread pool queue.</span></span>|

 <span data-ttu-id="4e756-366">次の表に、イベント データを示します</span><span class="sxs-lookup"><span data-stu-id="4e756-366">The following table shows the event data</span></span>

|<span data-ttu-id="4e756-367">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-367">Field name</span></span>|<span data-ttu-id="4e756-368">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-368">Data type</span></span>|<span data-ttu-id="4e756-369">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-369">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="4e756-370">作業要求へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4e756-370">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-371">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-371">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpoolioenqueue-event"></a><span data-ttu-id="4e756-372">ThreadPoolIOEnqueue イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-372">ThreadPoolIOEnqueue event</span></span>

 <span data-ttu-id="4e756-373">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-373">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-374">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-374">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-375">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-376">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-376">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-377">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="4e756-377">Verbose (5)</span></span>

 <span data-ttu-id="4e756-378">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-378">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-379">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-379">Event</span></span>|<span data-ttu-id="4e756-380">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-380">Event ID</span></span>|<span data-ttu-id="4e756-381">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-381">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|<span data-ttu-id="4e756-382">63</span><span class="sxs-lookup"><span data-stu-id="4e756-382">63</span></span>|<span data-ttu-id="4e756-383">スレッドが非同期 IO 発生後に IO 完了通知をエンキューします。</span><span class="sxs-lookup"><span data-stu-id="4e756-383">A thread enqueues an IO completion notification after an async IO completion occurs.</span></span>|

 <span data-ttu-id="4e756-384">次の表に、イベント データを示します</span><span class="sxs-lookup"><span data-stu-id="4e756-384">The following table shows the event data</span></span>

|<span data-ttu-id="4e756-385">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-385">Field name</span></span>|<span data-ttu-id="4e756-386">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-386">Data type</span></span>|<span data-ttu-id="4e756-387">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-387">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="4e756-388">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-388">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="4e756-389">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-389">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="4e756-390">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-390">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-391">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-391">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliodequeue-event"></a><span data-ttu-id="4e756-392">ThreadPoolIODequeue イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-392">ThreadPoolIODequeue event</span></span>

 <span data-ttu-id="4e756-393">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-393">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-394">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-394">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-395">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-395">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-396">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-396">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-397">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="4e756-397">Verbose (5)</span></span>

 <span data-ttu-id="4e756-398">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-398">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-399">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-399">Event</span></span>|<span data-ttu-id="4e756-400">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-400">Event ID</span></span>|<span data-ttu-id="4e756-401">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-401">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|<span data-ttu-id="4e756-402">64</span><span class="sxs-lookup"><span data-stu-id="4e756-402">64</span></span>|<span data-ttu-id="4e756-403">スレッドが IO 完了通知をデキューします。</span><span class="sxs-lookup"><span data-stu-id="4e756-403">A thread dequeues the IO completion notification.</span></span>|

 <span data-ttu-id="4e756-404">次の表に、イベント データを示します</span><span class="sxs-lookup"><span data-stu-id="4e756-404">The following table shows the event data</span></span>

|<span data-ttu-id="4e756-405">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-405">Field name</span></span>|<span data-ttu-id="4e756-406">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-406">Data type</span></span>|<span data-ttu-id="4e756-407">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-407">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="4e756-408">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-408">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="4e756-409">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-409">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="4e756-410">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-410">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-411">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-411">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliopack-event"></a><span data-ttu-id="4e756-412">ThreadPoolIOPack イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-412">ThreadPoolIOPack event</span></span>

 <span data-ttu-id="4e756-413">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-413">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="4e756-414">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-414">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-415">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-415">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-416">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-416">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-417">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="4e756-417">Verbose (5)</span></span>|

 <span data-ttu-id="4e756-418">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-418">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-419">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-419">Event</span></span>|<span data-ttu-id="4e756-420">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-420">Event ID</span></span>|<span data-ttu-id="4e756-421">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-421">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|<span data-ttu-id="4e756-422">65</span><span class="sxs-lookup"><span data-stu-id="4e756-422">65</span></span>|<span data-ttu-id="4e756-423">ThreadPool の重複 IO パックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4e756-423">ThreadPool overlapped IO pack is called.</span></span>|

 <span data-ttu-id="4e756-424">次の表に、イベント データを示します</span><span class="sxs-lookup"><span data-stu-id="4e756-424">The following table shows the event data</span></span>

|<span data-ttu-id="4e756-425">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-425">Field name</span></span>|<span data-ttu-id="4e756-426">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-426">Data type</span></span>|<span data-ttu-id="4e756-427">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-427">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="4e756-428">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-428">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="4e756-429">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e756-429">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-430">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-430">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadcreating-event"></a><span data-ttu-id="4e756-431">ThreadCreating イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-431">ThreadCreating event</span></span>

 <span data-ttu-id="4e756-432">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-432">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="4e756-433">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-433">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-434">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-435">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-435">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-436">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-436">Informational (4)</span></span>|

 <span data-ttu-id="4e756-437">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-437">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-438">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-438">Event</span></span>|<span data-ttu-id="4e756-439">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-439">Event ID</span></span>|<span data-ttu-id="4e756-440">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-440">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadCreating`|<span data-ttu-id="4e756-441">70</span><span class="sxs-lookup"><span data-stu-id="4e756-441">70</span></span>|<span data-ttu-id="4e756-442">スレッドが作成されました。</span><span class="sxs-lookup"><span data-stu-id="4e756-442">Thread has been created.</span></span>|

 <span data-ttu-id="4e756-443">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-443">The following table shows the event data.</span></span>

|<span data-ttu-id="4e756-444">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-444">Field name</span></span>|<span data-ttu-id="4e756-445">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-445">Data type</span></span>|<span data-ttu-id="4e756-446">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-446">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="4e756-447">スレッド ID</span><span class="sxs-lookup"><span data-stu-id="4e756-447">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-448">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-448">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadrunning-event"></a><span data-ttu-id="4e756-449">ThreadRunning イベント</span><span class="sxs-lookup"><span data-stu-id="4e756-449">ThreadRunning event</span></span>

 <span data-ttu-id="4e756-450">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-450">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="4e756-451">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4e756-451">Keyword for raising the event</span></span>|<span data-ttu-id="4e756-452">Level</span><span class="sxs-lookup"><span data-stu-id="4e756-452">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4e756-453">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4e756-453">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4e756-454">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="4e756-454">Informational (4)</span></span>|

 <span data-ttu-id="4e756-455">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-455">The following table shows the event information.</span></span>

|<span data-ttu-id="4e756-456">Event</span><span class="sxs-lookup"><span data-stu-id="4e756-456">Event</span></span>|<span data-ttu-id="4e756-457">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4e756-457">Event ID</span></span>|<span data-ttu-id="4e756-458">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-458">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadRunning`|<span data-ttu-id="4e756-459">71</span><span class="sxs-lookup"><span data-stu-id="4e756-459">71</span></span>|<span data-ttu-id="4e756-460">スレッドが実行を開始しました。</span><span class="sxs-lookup"><span data-stu-id="4e756-460">Thread has started running.</span></span>|

 <span data-ttu-id="4e756-461">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="4e756-461">The following table shows the event data.</span></span>

|<span data-ttu-id="4e756-462">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4e756-462">Field name</span></span>|<span data-ttu-id="4e756-463">データ型</span><span class="sxs-lookup"><span data-stu-id="4e756-463">Data type</span></span>|<span data-ttu-id="4e756-464">説明</span><span class="sxs-lookup"><span data-stu-id="4e756-464">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="4e756-465">スレッド ID</span><span class="sxs-lookup"><span data-stu-id="4e756-465">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="4e756-466">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="4e756-466">Unique ID for the instance of CoreCLR.</span></span>|

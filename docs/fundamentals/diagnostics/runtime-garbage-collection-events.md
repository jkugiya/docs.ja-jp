---
title: ガベージ コレクション ラインタイム イベント
description: .NET ガベージ コレクターに固有の診断情報を収集する .NET ランタイム イベントに関するページを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- GC events
- garbage collection events (CoreCLR)
- ETW, EventPipe, LTTng garbage collection events (CoreCLR)
ms.openlocfilehash: 2799a93f351baf23ec7a359b0b4b2be5c216dc4d
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594055"
---
# <a name="net-runtime-garbage-collection-events"></a><span data-ttu-id="2ddff-103">.NET ランタイム ガベージ コレクション イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-103">.NET runtime garbage collection events</span></span>

<span data-ttu-id="2ddff-104">これらのイベントは、ガベージ コレクションに関連する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-104">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="2ddff-105">ガベージ コレクションが実行された回数、ガベージ コレクション中に解放されたメモリの量などの診断やデバッグに役立ちます。診断のためにこれらのイベントを使用する方法の詳細については、「[.NET Core のログとトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ddff-105">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc. For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="gcstart_v2-event"></a><span data-ttu-id="2ddff-106">GCStart_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-106">GCStart_V2 Event</span></span>

<span data-ttu-id="2ddff-107">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-107">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-108">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-108">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-109">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-110">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-110">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-111">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-111">Informational (4)</span></span>|

<span data-ttu-id="2ddff-112">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-112">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-113">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-113">Event</span></span>|<span data-ttu-id="2ddff-114">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-114">Event ID</span></span>|<span data-ttu-id="2ddff-115">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="2ddff-116">1</span><span class="sxs-lookup"><span data-stu-id="2ddff-116">1</span></span>|<span data-ttu-id="2ddff-117">ガベージ コレクションが開始されました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-117">A garbage collection has started.</span></span>|

<span data-ttu-id="2ddff-118">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-118">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-119">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-119">Field name</span></span>|<span data-ttu-id="2ddff-120">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-120">Data type</span></span>|<span data-ttu-id="2ddff-121">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-121">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="2ddff-122">*n* 回めのガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="2ddff-122">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="2ddff-123">収集されるジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="2ddff-123">The generation that is being collected.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="2ddff-124">ガベージ コレクションが発生した理由:</span><span class="sxs-lookup"><span data-stu-id="2ddff-124">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="2ddff-125">`0x0` - 小さなオブジェクト ヒープの割り当て。</span><span class="sxs-lookup"><span data-stu-id="2ddff-125">`0x0` - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="2ddff-126">`0x1` - 強制実行。</span><span class="sxs-lookup"><span data-stu-id="2ddff-126">`0x1` - Induced.</span></span><br /><br /> <span data-ttu-id="2ddff-127">`0x2` - メモリ不足。</span><span class="sxs-lookup"><span data-stu-id="2ddff-127">`0x2` - Low memory.</span></span><br /><br /> <span data-ttu-id="2ddff-128">`0x3` - 空。</span><span class="sxs-lookup"><span data-stu-id="2ddff-128">`0x3` - Empty.</span></span><br /><br /> <span data-ttu-id="2ddff-129">`0x4` - 大きなオブジェクト ヒープの割り当て。</span><span class="sxs-lookup"><span data-stu-id="2ddff-129">`0x4` - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="2ddff-130">`0x5` - 領域不足 (小さなオブジェクト ヒープ対象)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-130">`0x5` - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="2ddff-131">`0x6` - 領域不足 (大きなオブジェクト ヒープ対象)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-131">`0x6` - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="2ddff-132">`0x7` - 強制実行されるが、ブロッキングとして強制されない。</span><span class="sxs-lookup"><span data-stu-id="2ddff-132">`0x7` - Induced but not forced as blocking.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="2ddff-133">`0x0` - バックグラウンド ガベージ コレクションの外部で発生するブロッキング ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="2ddff-133">`0x0` - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="2ddff-134">`0x1` - バックグラウンド ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="2ddff-134">`0x1` - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="2ddff-135">`0x2` - バックグラウンド ガベージ コレクションの実行中に発生するブロッキング ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="2ddff-135">`0x2` - Blocking garbage collection occurred during background garbage collection.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="2ddff-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2ddff-136">win:UInt16</span></span>|<span data-ttu-id="2ddff-137">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-137">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="2ddff-138">GCEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-138">GCEnd_V1 Event</span></span>

<span data-ttu-id="2ddff-139">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-139">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-140">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-140">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-141">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-141">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-142">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-142">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-143">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-143">Informational (4)</span></span>|

<span data-ttu-id="2ddff-144">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-144">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-145">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-145">Event</span></span>|<span data-ttu-id="2ddff-146">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-146">Event ID</span></span>|<span data-ttu-id="2ddff-147">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-147">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="2ddff-148">2</span><span class="sxs-lookup"><span data-stu-id="2ddff-148">2</span></span>|<span data-ttu-id="2ddff-149">ガベージ コレクションが終了しました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-149">The garbage collection has ended.</span></span>|

<span data-ttu-id="2ddff-150">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-150">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-151">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-151">Field name</span></span>|<span data-ttu-id="2ddff-152">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-152">Data type</span></span>|<span data-ttu-id="2ddff-153">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-153">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="2ddff-154">*n* 回めのガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="2ddff-154">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="2ddff-155">収集されたジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="2ddff-155">The generation that was collected.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="2ddff-156">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2ddff-156">win:UInt16</span></span>|<span data-ttu-id="2ddff-157">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-157">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcheapstats_v2-event"></a><span data-ttu-id="2ddff-158">GCHeapStats_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-158">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="2ddff-159">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-159">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-160">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-160">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-161">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-161">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-162">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-162">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-163">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-163">Informational (4)</span></span>|

<span data-ttu-id="2ddff-164">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-164">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-165">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-165">Event</span></span>|<span data-ttu-id="2ddff-166">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-166">Event ID</span></span>|<span data-ttu-id="2ddff-167">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-167">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="2ddff-168">4</span><span class="sxs-lookup"><span data-stu-id="2ddff-168">4</span></span>|<span data-ttu-id="2ddff-169">各ガベージ コレクション終了時のヒープの統計情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-169">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="2ddff-170">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-170">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-171">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-171">Field name</span></span>|<span data-ttu-id="2ddff-172">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-172">Data type</span></span>|<span data-ttu-id="2ddff-173">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-173">Description</span></span>|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|<span data-ttu-id="2ddff-174">ジェネレーション 0 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-174">The size, in bytes, of generation 0 memory.</span></span>|
|`TotalPromotedSize0`|`win:UInt64`|<span data-ttu-id="2ddff-175">ジェネレーション 0 からジェネレーション 1 に移されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-175">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|`GenerationSize1`|`win:UInt64`|<span data-ttu-id="2ddff-176">ジェネレーション 1 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-176">The size, in bytes, of generation 1 memory.</span></span>|
|`TotalPromotedSize1`|`win:UInt64`|<span data-ttu-id="2ddff-177">ジェネレーション 1 からジェネレーション 2 に移されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-177">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|`GenerationSize2`|`win:UInt64`|<span data-ttu-id="2ddff-178">ジェネレーション 2 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-178">The size, in bytes, of generation 2 memory.</span></span>|
|`TotalPromotedSize2`|`win:UInt64`|<span data-ttu-id="2ddff-179">最後のガベージ コレクションの後にジェネレーション 2 に残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-179">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|`GenerationSize3`|`win:UInt64`|<span data-ttu-id="2ddff-180">大きなオブジェクト ヒープのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-180">The size, in bytes, of the large object heap.</span></span>|
|`TotalPromotedSize3`|`win:UInt64`|<span data-ttu-id="2ddff-181">最後のガベージ コレクションの後に大きなオブジェクト ヒープに残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-181">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|`FinalizationPromotedSize`|`win:UInt64`|<span data-ttu-id="2ddff-182">終了準備が完了しているオブジェクトの合計サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-182">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|`FinalizationPromotedCount`|`win:UInt64`|<span data-ttu-id="2ddff-183">終了準備が完了しているオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-183">The number of objects that are ready for finalization.</span></span>|
|`PinnedObjectCount`|`win:UInt32`|<span data-ttu-id="2ddff-184">ピン止めオブジェクト (移動できないオブジェクト) の数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-184">The number of pinned (unmovable) objects.</span></span>|
|`SinkBlockCount`|`win:UInt32`|<span data-ttu-id="2ddff-185">使用中の同期ブロックの数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-185">The number of synchronization blocks in use.</span></span>|
|`GCHandleCount`|`win:UInt32`|<span data-ttu-id="2ddff-186">使用中のガベージ コレクション ハンドルの数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-186">The number of garbage collection handles in use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2ddff-187">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-187">Unique ID for the instance of CoreCLR.</span></span>|
|`GenerationSize4`|`win:UInt64`|<span data-ttu-id="2ddff-188">固定オブジェクト ヒープのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-188">The size, in bytes, of the pinned object heap.</span></span>|
|`TotalPromotedSize4`|`win:UInt64`|<span data-ttu-id="2ddff-189">最後のガベージ コレクションの後に固定オブジェクト ヒープに残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-189">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|

## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="2ddff-190">GCCreateSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-190">GCCreateSegment_V1 event</span></span>

<span data-ttu-id="2ddff-191">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-191">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-192">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-192">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-193">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-193">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-194">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-194">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-195">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-195">Informational (4)</span></span>|

<span data-ttu-id="2ddff-196">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-196">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-197">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-197">Event</span></span>|<span data-ttu-id="2ddff-198">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-198">Event ID</span></span>|<span data-ttu-id="2ddff-199">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-199">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="2ddff-200">5</span><span class="sxs-lookup"><span data-stu-id="2ddff-200">5</span></span>|<span data-ttu-id="2ddff-201">新しいガベージ コレクション セグメントが作成されました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-201">A new garbage collection segment has been created.</span></span> <span data-ttu-id="2ddff-202">既に実行されているプロセスでトレースを有効にした場合は、このイベントが各既存セグメントについて発生します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-202">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="2ddff-203">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-203">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-204">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-204">Field name</span></span>|<span data-ttu-id="2ddff-205">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-205">Data type</span></span>|<span data-ttu-id="2ddff-206">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-206">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="2ddff-207">セグメントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="2ddff-207">The address of the segment.</span></span>|
|`Size`|`win:UInt64`|<span data-ttu-id="2ddff-208">セグメントのサイズ。</span><span class="sxs-lookup"><span data-stu-id="2ddff-208">The size of the segment.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="2ddff-209">0x0 - 小さなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="2ddff-209">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="2ddff-210">0x1 - 大きなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="2ddff-210">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="2ddff-211">0x2 - 読み取り専用ヒープ。</span><span class="sxs-lookup"><span data-stu-id="2ddff-211">0x2 - Read-only heap.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2ddff-212">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-212">Unique ID for the instance of CoreCLR.</span></span>|

<span data-ttu-id="2ddff-213">ガベージ コレクターによって割り当てられるセグメントのサイズは実装に固有であり、定期的な更新プログラムによる場合を含め、いつでも変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2ddff-213">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="2ddff-214">アプリでは、セグメント サイズを推測することや、特定のセグメント サイズに依存することを絶対に避けてください。また、セグメントの割り当てに使用可能なメモリの量を構成しようとしてもなりません。</span><span class="sxs-lookup"><span data-stu-id="2ddff-214">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="2ddff-215">GCFreeSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-215">GCFreeSegment_V1 event</span></span>

<span data-ttu-id="2ddff-216">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-216">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-217">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-217">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-218">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-218">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-219">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-219">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-220">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-220">Informational (4)</span></span>|

<span data-ttu-id="2ddff-221">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-221">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-222">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-222">Event</span></span>|<span data-ttu-id="2ddff-223">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-223">Event ID</span></span>|<span data-ttu-id="2ddff-224">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-224">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="2ddff-225">6</span><span class="sxs-lookup"><span data-stu-id="2ddff-225">6</span></span>|<span data-ttu-id="2ddff-226">ガベージ コレクション セグメントが解放されました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-226">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="2ddff-227">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-227">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-228">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-228">Field name</span></span>|<span data-ttu-id="2ddff-229">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-229">Data type</span></span>|<span data-ttu-id="2ddff-230">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-230">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="2ddff-231">セグメントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="2ddff-231">The address of the segment.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2ddff-232">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-232">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="2ddff-233">GCRestartEEBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-233">GCRestartEEBegin_V1 event</span></span>

<span data-ttu-id="2ddff-234">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-234">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-235">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-235">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-236">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-236">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-237">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-237">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-238">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-238">Informational (4)</span></span>|

<span data-ttu-id="2ddff-239">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-239">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-240">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-240">Event</span></span>|<span data-ttu-id="2ddff-241">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-241">Event ID</span></span>|<span data-ttu-id="2ddff-242">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-242">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="2ddff-243">7</span><span class="sxs-lookup"><span data-stu-id="2ddff-243">7</span></span>|<span data-ttu-id="2ddff-244">共通言語ランタイムの中断からの再開が開始されました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-244">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="2ddff-245">このイベントには、イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="2ddff-245">This event does not have any event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="2ddff-246">GCRestartEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-246">GCRestartEEEnd_V1 event</span></span>

<span data-ttu-id="2ddff-247">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-247">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-248">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-248">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-249">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-249">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-250">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-250">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-251">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-251">Informational (4)</span></span>|

<span data-ttu-id="2ddff-252">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-252">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-253">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-253">Event</span></span>|<span data-ttu-id="2ddff-254">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-254">Event Id</span></span>|<span data-ttu-id="2ddff-255">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-255">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="2ddff-256">3</span><span class="sxs-lookup"><span data-stu-id="2ddff-256">3</span></span>|<span data-ttu-id="2ddff-257">共通言語ランタイムの中断からの再開が終了しました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-257">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="2ddff-258">このイベントには、イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="2ddff-258">This event does not have any event data.</span></span>

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="2ddff-259">GCSuspendEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-259">GCSuspendEEEnd_V1 event</span></span>

<span data-ttu-id="2ddff-260">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-260">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-261">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-261">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-262">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-262">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-263">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-263">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-264">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-264">Informational (4)</span></span>|

<span data-ttu-id="2ddff-265">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-265">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-266">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-266">Event</span></span>|<span data-ttu-id="2ddff-267">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-267">Event ID</span></span>|<span data-ttu-id="2ddff-268">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-268">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="2ddff-269">8</span><span class="sxs-lookup"><span data-stu-id="2ddff-269">8</span></span>|<span data-ttu-id="2ddff-270">ガベージ コレクションのための実行エンジンの中断の終了。</span><span class="sxs-lookup"><span data-stu-id="2ddff-270">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="2ddff-271">このイベントには、イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="2ddff-271">This event does not have any event data.</span></span>

## <a name="gcsuspendeebegin_v1-event"></a><span data-ttu-id="2ddff-272">GCSuspendEEBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-272">GCSuspendEEBegin_V1 event</span></span>

<span data-ttu-id="2ddff-273">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-273">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-274">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-274">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-275">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-275">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-276">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-276">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-277">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-277">Informational (4)</span></span>|

<span data-ttu-id="2ddff-278">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-278">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-279">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-279">Event</span></span>|<span data-ttu-id="2ddff-280">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-280">Event ID</span></span>|<span data-ttu-id="2ddff-281">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-281">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|<span data-ttu-id="2ddff-282">8</span><span class="sxs-lookup"><span data-stu-id="2ddff-282">8</span></span>|<span data-ttu-id="2ddff-283">ガベージ コレクションのための実行エンジンの中断の開始。</span><span class="sxs-lookup"><span data-stu-id="2ddff-283">Start of suspension of the execution engine for garbage collection.</span></span>|

|<span data-ttu-id="2ddff-284">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-284">Field name</span></span>|<span data-ttu-id="2ddff-285">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-285">Data type</span></span>|<span data-ttu-id="2ddff-286">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-286">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="2ddff-287">*n* 回めのガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="2ddff-287">The *n* th garbage collection.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="2ddff-288">EE の中断の理由。</span><span class="sxs-lookup"><span data-stu-id="2ddff-288">Reason for EE suspension.</span></span><br/><br/><span data-ttu-id="2ddff-289">`0x0`: その他の中断</span><span class="sxs-lookup"><span data-stu-id="2ddff-289">`0x0`: Suspend for Other</span></span><br/><br/><span data-ttu-id="2ddff-290">`0x1`: GC による中断。</span><span class="sxs-lookup"><span data-stu-id="2ddff-290">`0x1`: Suspend for GC.</span></span><br/><br/><span data-ttu-id="2ddff-291">`0x2`: AppDomain のシャットダウンによる中断。</span><span class="sxs-lookup"><span data-stu-id="2ddff-291">`0x2`: Suspend for AppDomain shutdown.</span></span><br/><br/><span data-ttu-id="2ddff-292">`0x3`: コード ピッチによる中断。</span><span class="sxs-lookup"><span data-stu-id="2ddff-292">`0x3`: Suspend for code pitching.</span></span><br/><br/><span data-ttu-id="2ddff-293">`0x4`: シャットダウンによる中断。</span><span class="sxs-lookup"><span data-stu-id="2ddff-293">`0x4`: Suspend for shutdown.</span></span><br/><br/><span data-ttu-id="2ddff-294">`0x5`: デバッガーによる中断。</span><span class="sxs-lookup"><span data-stu-id="2ddff-294">`0x5`: Suspend for debugger.</span></span><br/><br/><span data-ttu-id="2ddff-295">`0x6`: GC 準備による中断。</span><span class="sxs-lookup"><span data-stu-id="2ddff-295">`0x6`: Suspend for GC Prep.</span></span><br/><br/><span data-ttu-id="2ddff-296">`0x7`: デバッガー スイープによる中断</span><span class="sxs-lookup"><span data-stu-id="2ddff-296">`0x7`: Suspend for debugger sweep</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="2ddff-297">GCAllocationTick_V3 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-297">GCAllocationTick_V3 event</span></span>

<span data-ttu-id="2ddff-298">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-298">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-299">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-299">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-300">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-300">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-301">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-301">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-302">詳細 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-302">Verbose (4)</span></span>|

<span data-ttu-id="2ddff-303">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-303">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-304">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-304">Event</span></span>|<span data-ttu-id="2ddff-305">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-305">Event ID</span></span>|<span data-ttu-id="2ddff-306">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-306">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="2ddff-307">10</span><span class="sxs-lookup"><span data-stu-id="2ddff-307">10</span></span>|<span data-ttu-id="2ddff-308">約 100 KB が割り当てられるたび。</span><span class="sxs-lookup"><span data-stu-id="2ddff-308">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="2ddff-309">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-309">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-310">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-310">Field name</span></span>|<span data-ttu-id="2ddff-311">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-311">Data type</span></span>|<span data-ttu-id="2ddff-312">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-312">Description</span></span>|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|<span data-ttu-id="2ddff-313">割り当てサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-313">The allocation size, in bytes.</span></span> <span data-ttu-id="2ddff-314">この値は、ULONG (4,294,967,295 バイト) の長さより短い割り当ての場合に正確です。</span><span class="sxs-lookup"><span data-stu-id="2ddff-314">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="2ddff-315">割り当てがこれを超える場合、このフィールドには切り捨てられた値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2ddff-315">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="2ddff-316">非常に大きな割り当てには `AllocationAmount64` を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-316">Use `AllocationAmount64` for very large allocations.</span></span>|
|`AllocationKind`|`win:UInt32`|<span data-ttu-id="2ddff-317">`0x0` - 小さなオブジェクトの割り当て (小さなオブジェクト ヒープへの割り当て)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-317">`0x0` - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="2ddff-318">`0x1` - 大きなオブジェクトの割り当て (大きなオブジェクト ヒープへの割り当て)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-318">`0x1` - Large object allocation (allocation is in large object heap).</span></span>|
|`AllocationAmount64`|`win:UInt64`|<span data-ttu-id="2ddff-319">割り当てサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2ddff-319">The allocation size, in bytes.</span></span> <span data-ttu-id="2ddff-320">この値は非常に大きな割り当ての場合に正確です。</span><span class="sxs-lookup"><span data-stu-id="2ddff-320">This value is accurate for very large allocations.</span></span>|
|`TypeId`|`win:Pointer`|<span data-ttu-id="2ddff-321">MethodTable のアドレス。</span><span class="sxs-lookup"><span data-stu-id="2ddff-321">The address of the MethodTable.</span></span> <span data-ttu-id="2ddff-322">このイベント中に複数の型のオブジェクトが割り当てられた場合、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) に対応する MethodTable のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="2ddff-322">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="2ddff-323">割り当てられた型の名前。</span><span class="sxs-lookup"><span data-stu-id="2ddff-323">The name of the type that was allocated.</span></span> <span data-ttu-id="2ddff-324">このイベント中に複数の型のオブジェクトが割り当てられた場合は、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) の型です。</span><span class="sxs-lookup"><span data-stu-id="2ddff-324">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`HeapIndex`|`win:UInt32`|<span data-ttu-id="2ddff-325">オブジェクトが割り当てられたヒープ。</span><span class="sxs-lookup"><span data-stu-id="2ddff-325">The heap where the object was allocated.</span></span> <span data-ttu-id="2ddff-326">ワークステーションのガベージ コレクションと共に実行する場合、この値は 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="2ddff-326">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|`Address`|`win:Pointer`|<span data-ttu-id="2ddff-327">最後に割り当てられたオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="2ddff-327">The address of the last allocated object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2ddff-328">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-328">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="2ddff-329">GCCreateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-329">GCCreateConcurrentThread_V1 event</span></span>

<span data-ttu-id="2ddff-330">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-330">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-331">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-331">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-332">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-332">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-333">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-333">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-334">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-334">Informational (4)</span></span>|
|<span data-ttu-id="2ddff-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="2ddff-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="2ddff-336">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-336">Informational (4)</span></span>|

<span data-ttu-id="2ddff-337">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-337">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-338">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-338">Event</span></span>|<span data-ttu-id="2ddff-339">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-339">Event ID</span></span>|<span data-ttu-id="2ddff-340">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-340">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="2ddff-341">11</span><span class="sxs-lookup"><span data-stu-id="2ddff-341">11</span></span>|<span data-ttu-id="2ddff-342">同時実行ガベージ コレクション スレッドが作成されました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-342">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="2ddff-343">このイベントには、イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="2ddff-343">This event does not have any event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="2ddff-344">GCTerminateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-344">GCTerminateConcurrentThread_V1 event</span></span>

<span data-ttu-id="2ddff-345">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-345">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-346">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-346">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-347">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-347">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-348">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-348">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-349">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-349">Informational (4)</span></span>|
|<span data-ttu-id="2ddff-350">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="2ddff-350">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="2ddff-351">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-351">Informational (4)</span></span>|

<span data-ttu-id="2ddff-352">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-352">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-353">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-353">Event</span></span>|<span data-ttu-id="2ddff-354">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-354">Event ID</span></span>|<span data-ttu-id="2ddff-355">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="2ddff-356">12</span><span class="sxs-lookup"><span data-stu-id="2ddff-356">12</span></span>|<span data-ttu-id="2ddff-357">同時実行ガベージ コレクションスレッドが終了しました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-357">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="2ddff-358">このイベントには、イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="2ddff-358">This event does not have any event data.</span></span>

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="2ddff-359">GCFinalizersBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-359">GCFinalizersBegin_V1 event</span></span>

<span data-ttu-id="2ddff-360">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-360">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-361">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-361">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-362">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-362">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-363">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-363">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-364">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-364">Informational (4)</span></span>|

<span data-ttu-id="2ddff-365">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-365">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-366">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-366">Event</span></span>|<span data-ttu-id="2ddff-367">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-367">Event ID</span></span>|<span data-ttu-id="2ddff-368">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-368">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="2ddff-369">14</span><span class="sxs-lookup"><span data-stu-id="2ddff-369">14</span></span>|<span data-ttu-id="2ddff-370">ファイナライザーの実行の開始。</span><span class="sxs-lookup"><span data-stu-id="2ddff-370">The start of running finalizers.</span></span>|

<span data-ttu-id="2ddff-371">このイベントには、イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="2ddff-371">This event does not have any event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="2ddff-372">GCFinalizersEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-372">GCFinalizersEnd_V1 event</span></span>

<span data-ttu-id="2ddff-373">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-373">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-374">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-374">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-375">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-376">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-376">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-377">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-377">Informational (4)</span></span>|

<span data-ttu-id="2ddff-378">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-378">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-379">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-379">Event</span></span>|<span data-ttu-id="2ddff-380">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-380">Event ID</span></span>|<span data-ttu-id="2ddff-381">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-381">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="2ddff-382">13</span><span class="sxs-lookup"><span data-stu-id="2ddff-382">13</span></span>|<span data-ttu-id="2ddff-383">ファイナライザーの実行の終了。</span><span class="sxs-lookup"><span data-stu-id="2ddff-383">The end of running finalizers.</span></span>|

<span data-ttu-id="2ddff-384">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-384">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-385">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-385">Field name</span></span>|<span data-ttu-id="2ddff-386">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-386">Data type</span></span>|<span data-ttu-id="2ddff-387">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-387">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="2ddff-388">実行されたファイナライザーの数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-388">The number of finalizers that were run.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="2ddff-389">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2ddff-389">win:UInt16</span></span>|<span data-ttu-id="2ddff-390">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-390">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="setgchandle-event"></a><span data-ttu-id="2ddff-391">SetGCHandle イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-391">SetGCHandle event</span></span>

<span data-ttu-id="2ddff-392">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-392">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-393">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-393">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-394">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-394">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-395">`GCHandleKeyword` (0x2)</span><span class="sxs-lookup"><span data-stu-id="2ddff-395">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="2ddff-396">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-396">Informational (4)</span></span>|

<span data-ttu-id="2ddff-397">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-397">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-398">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-398">Event</span></span>|<span data-ttu-id="2ddff-399">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-399">Event ID</span></span>|<span data-ttu-id="2ddff-400">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-400">Raised when</span></span>|
|-----------|--------------|-----------------|
|`SetGCHandle`|<span data-ttu-id="2ddff-401">30</span><span class="sxs-lookup"><span data-stu-id="2ddff-401">30</span></span>|<span data-ttu-id="2ddff-402">GC ハンドルが設定されました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-402">A GC Handle has been set.</span></span>|

<span data-ttu-id="2ddff-403">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-403">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-404">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-404">Field name</span></span>|<span data-ttu-id="2ddff-405">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-405">Data type</span></span>|<span data-ttu-id="2ddff-406">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-406">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="2ddff-407">割り当てられたハンドルのアドレス。</span><span class="sxs-lookup"><span data-stu-id="2ddff-407">The address of the allocated handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="2ddff-408">ハンドルが作成されたオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="2ddff-408">The address of the object whose handle was created.</span></span>|
|`Kind`|`win:UInt32`|<span data-ttu-id="2ddff-409">設定された GC ハンドルの型。</span><span class="sxs-lookup"><span data-stu-id="2ddff-409">The type of GC handle that was set.</span></span> <br /><br /><span data-ttu-id="2ddff-410">`0x0`: WeakShort</span><span class="sxs-lookup"><span data-stu-id="2ddff-410">`0x0`: WeakShort</span></span> <br/><br/><span data-ttu-id="2ddff-411">`0x1`: WeakLong</span><span class="sxs-lookup"><span data-stu-id="2ddff-411">`0x1`: WeakLong</span></span> <br /><br /><span data-ttu-id="2ddff-412">`0x2`: Strong</span><span class="sxs-lookup"><span data-stu-id="2ddff-412">`0x2`: Strong</span></span> <br /><br /><span data-ttu-id="2ddff-413">`0x3`: Pinned</span><span class="sxs-lookup"><span data-stu-id="2ddff-413">`0x3`: Pinned</span></span> <br /><br /><span data-ttu-id="2ddff-414">`0x4`: Variable</span><span class="sxs-lookup"><span data-stu-id="2ddff-414">`0x4`: Variable</span></span><br /><br /><span data-ttu-id="2ddff-415">`0x5`: RefCounted</span><span class="sxs-lookup"><span data-stu-id="2ddff-415">`0x5`: RefCounted</span></span> <br /><br /><span data-ttu-id="2ddff-416">`0x6`: Dependent</span><span class="sxs-lookup"><span data-stu-id="2ddff-416">`0x6`: Dependent</span></span><br /><br /><span data-ttu-id="2ddff-417">`0x7`: AsyncPinned</span><span class="sxs-lookup"><span data-stu-id="2ddff-417">`0x7`: AsyncPinned</span></span><br /><br /><span data-ttu-id="2ddff-418">`0x8`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="2ddff-418">`0x8`: SizedRef</span></span>|
|`Generation`|`win:UInt32`|<span data-ttu-id="2ddff-419">ハンドルが作成されたオブジェクトの世代。</span><span class="sxs-lookup"><span data-stu-id="2ddff-419">The generation of the object whose handle was created.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="2ddff-420">AppDomain ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-420">The AppDomain ID.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2ddff-421">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-421">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="destroygchandle-event"></a><span data-ttu-id="2ddff-422">DestroyGCHandle イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-422">DestroyGCHandle event</span></span>

<span data-ttu-id="2ddff-423">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-423">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-424">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-424">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-425">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-425">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-426">`GCHandleKeyword` (0x2)</span><span class="sxs-lookup"><span data-stu-id="2ddff-426">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="2ddff-427">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-427">Informational (4)</span></span>|

<span data-ttu-id="2ddff-428">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-428">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-429">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-429">Event</span></span>|<span data-ttu-id="2ddff-430">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-430">Event ID</span></span>|<span data-ttu-id="2ddff-431">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-431">Raised when</span></span>|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|<span data-ttu-id="2ddff-432">31</span><span class="sxs-lookup"><span data-stu-id="2ddff-432">31</span></span>|<span data-ttu-id="2ddff-433">GC ハンドルが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="2ddff-433">A GC Handle is destroyed.</span></span>|

<span data-ttu-id="2ddff-434">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-434">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-435">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-435">Field name</span></span>|<span data-ttu-id="2ddff-436">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-436">Data type</span></span>|<span data-ttu-id="2ddff-437">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-437">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="2ddff-438">破棄されたハンドルのアドレス。</span><span class="sxs-lookup"><span data-stu-id="2ddff-438">The address of the destroyed handle.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="2ddff-439">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2ddff-439">win:UInt16</span></span>|<span data-ttu-id="2ddff-440">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-440">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="pinobjectatgctime-event"></a><span data-ttu-id="2ddff-441">PinObjectAtGCTime イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-441">PinObjectAtGCTime event</span></span>

<span data-ttu-id="2ddff-442">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-442">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-443">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-443">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-444">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-444">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-445">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-445">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-446">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="2ddff-446">Verbose (5)</span></span>|

<span data-ttu-id="2ddff-447">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-447">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-448">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-448">Event</span></span>|<span data-ttu-id="2ddff-449">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-449">Event ID</span></span>|<span data-ttu-id="2ddff-450">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-450">Raised when</span></span>|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|<span data-ttu-id="2ddff-451">33</span><span class="sxs-lookup"><span data-stu-id="2ddff-451">33</span></span>|<span data-ttu-id="2ddff-452">オブジェクトが GC 中に固定されました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-452">An object was pinned during a GC.</span></span>|

<span data-ttu-id="2ddff-453">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-453">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-454">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-454">Field name</span></span>|<span data-ttu-id="2ddff-455">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-455">Data type</span></span>|<span data-ttu-id="2ddff-456">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-456">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="2ddff-457">ハンドルのアドレス。</span><span class="sxs-lookup"><span data-stu-id="2ddff-457">The address of the handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="2ddff-458">固定オブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="2ddff-458">The address of the pinned object.</span></span>|
|`ObjectSize`|`win:UInt64`|<span data-ttu-id="2ddff-459">固定オブジェクトのサイズ。</span><span class="sxs-lookup"><span data-stu-id="2ddff-459">The size of the pinned object.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="2ddff-460">固定オブジェクトの型の名前。</span><span class="sxs-lookup"><span data-stu-id="2ddff-460">The name of the type of the pinned object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2ddff-461">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-461">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gctriggered-event"></a><span data-ttu-id="2ddff-462">GCTriggered イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-462">GCTriggered event</span></span>

<span data-ttu-id="2ddff-463">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-463">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-464">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-464">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-465">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-465">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-466">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-466">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-467">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="2ddff-467">Verbose (5)</span></span>|

<span data-ttu-id="2ddff-468">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-468">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-469">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-469">Event</span></span>|<span data-ttu-id="2ddff-470">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-470">Event ID</span></span>|<span data-ttu-id="2ddff-471">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-471">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTriggered`|<span data-ttu-id="2ddff-472">33</span><span class="sxs-lookup"><span data-stu-id="2ddff-472">33</span></span>|<span data-ttu-id="2ddff-473">GC がトリガーされました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-473">A GC has been triggered.</span></span>|

<span data-ttu-id="2ddff-474">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-474">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-475">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-475">Field name</span></span>|<span data-ttu-id="2ddff-476">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-476">Data type</span></span>|<span data-ttu-id="2ddff-477">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-477">Description</span></span>|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|<span data-ttu-id="2ddff-478">GC がトリガーされた理由。</span><span class="sxs-lookup"><span data-stu-id="2ddff-478">The reason a GC was triggered.</span></span><br/><br/><span data-ttu-id="2ddff-479">`0x0`: AllocSmall</span><span class="sxs-lookup"><span data-stu-id="2ddff-479">`0x0`: AllocSmall</span></span><br/><br/><span data-ttu-id="2ddff-480">`0x1`: Induced</span><span class="sxs-lookup"><span data-stu-id="2ddff-480">`0x1`: Induced</span></span> <br/><br/><span data-ttu-id="2ddff-481">`0x2`: LowMemory</span><span class="sxs-lookup"><span data-stu-id="2ddff-481">`0x2`: LowMemory</span></span> <br/><br/><span data-ttu-id="2ddff-482">`0x3`: Empty</span><span class="sxs-lookup"><span data-stu-id="2ddff-482">`0x3`: Empty</span></span> <br/><br/><span data-ttu-id="2ddff-483">`0x4`: AllocLarge</span><span class="sxs-lookup"><span data-stu-id="2ddff-483">`0x4`: AllocLarge</span></span> <br/><br/><span data-ttu-id="2ddff-484">`0x5`: OutOfSpaceSmallObjectHeap</span><span class="sxs-lookup"><span data-stu-id="2ddff-484">`0x5`: OutOfSpaceSmallObjectHeap</span></span> <br/><br/><span data-ttu-id="2ddff-485">`0x6`: OutOfSpaceLargeObjectHeap</span><span class="sxs-lookup"><span data-stu-id="2ddff-485">`0x6`: OutOfSpaceLargeObjectHeap</span></span> <br/><br/><span data-ttu-id="2ddff-486">`0x7`: InducedNoForce</span><span class="sxs-lookup"><span data-stu-id="2ddff-486">`0x7`:InducedNoForce</span></span> <br/><br/><span data-ttu-id="2ddff-487">`0x8`: Stress</span><span class="sxs-lookup"><span data-stu-id="2ddff-487">`0x8`: Stress</span></span> <br/><br/><span data-ttu-id="2ddff-488">`0x9`: InducedLowMemory</span><span class="sxs-lookup"><span data-stu-id="2ddff-488">`0x9`: InducedLowMemory</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2ddff-489">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-489">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="increasememorypressure-event"></a><span data-ttu-id="2ddff-490">IncreaseMemoryPressure イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-490">IncreaseMemoryPressure event</span></span>

<span data-ttu-id="2ddff-491">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-491">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-492">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-492">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-493">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-493">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-494">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-494">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-495">情報 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-495">Information (4)</span></span>|

<span data-ttu-id="2ddff-496">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-496">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-497">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-497">Event</span></span>|<span data-ttu-id="2ddff-498">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-498">Event ID</span></span>|<span data-ttu-id="2ddff-499">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-499">Raised when</span></span>|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|<span data-ttu-id="2ddff-500">200</span><span class="sxs-lookup"><span data-stu-id="2ddff-500">200</span></span>|<span data-ttu-id="2ddff-501">メモリの負荷が増加しました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-501">Memory pressure was increased.</span></span>|

<span data-ttu-id="2ddff-502">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-502">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-503">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-503">Field Name</span></span>|<span data-ttu-id="2ddff-504">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-504">Data type</span></span>|<span data-ttu-id="2ddff-505">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-505">Description</span></span>|
|----------------|---------------|-----------------|
|`ClrInstanceID`|<span data-ttu-id="2ddff-506">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2ddff-506">win:UInt16</span></span>|<span data-ttu-id="2ddff-507">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-507">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="decreasememorypressure-event"></a><span data-ttu-id="2ddff-508">DecreaseMemoryPressure イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-508">DecreaseMemoryPressure event</span></span>

<span data-ttu-id="2ddff-509">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-509">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-510">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-510">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-511">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-511">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-512">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-512">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-513">情報 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-513">Information (4)</span></span>|

<span data-ttu-id="2ddff-514">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-514">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-515">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-515">Event</span></span>|<span data-ttu-id="2ddff-516">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-516">Event ID</span></span>|<span data-ttu-id="2ddff-517">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-517">Raised when</span></span>|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|<span data-ttu-id="2ddff-518">201</span><span class="sxs-lookup"><span data-stu-id="2ddff-518">201</span></span>|<span data-ttu-id="2ddff-519">メモリの負荷が減少しました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-519">Memory pressure was decreased.</span></span>|

<span data-ttu-id="2ddff-520">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-520">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-521">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-521">Field Name</span></span>|<span data-ttu-id="2ddff-522">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-522">Data type</span></span>|<span data-ttu-id="2ddff-523">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-523">Description</span></span>|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|<span data-ttu-id="2ddff-524">解放されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-524">Bytes freed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2ddff-525">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-525">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcmarkwithtype-event"></a><span data-ttu-id="2ddff-526">GCMarkWithType イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-526">GCMarkWithType event</span></span>

<span data-ttu-id="2ddff-527">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-527">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-528">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-528">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-529">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-529">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-530">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-530">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-531">情報 (4)</span><span class="sxs-lookup"><span data-stu-id="2ddff-531">Information (4)</span></span>|

<span data-ttu-id="2ddff-532">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-532">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-533">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-533">Event</span></span>|<span data-ttu-id="2ddff-534">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-534">Event ID</span></span>|<span data-ttu-id="2ddff-535">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-535">Raised when</span></span>|
|----------------|---------------|-----------------|
|`GCMarkWithType`|<span data-ttu-id="2ddff-536">202</span><span class="sxs-lookup"><span data-stu-id="2ddff-536">202</span></span>|<span data-ttu-id="2ddff-537">GC マーク フェーズ中に GC ルートがマークされました。</span><span class="sxs-lookup"><span data-stu-id="2ddff-537">A GC root has been marked during GC mark phase.</span></span>|

<span data-ttu-id="2ddff-538">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-538">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-539">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-539">Field Name</span></span>|<span data-ttu-id="2ddff-540">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-540">Data type</span></span>|<span data-ttu-id="2ddff-541">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-541">Description</span></span>|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|<span data-ttu-id="2ddff-542">ヒープ番号。</span><span class="sxs-lookup"><span data-stu-id="2ddff-542">The heap number.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="2ddff-543">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2ddff-543">win:UInt16</span></span>|<span data-ttu-id="2ddff-544">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-544">Unique ID for the instance of CoreCLR.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="2ddff-545">GC ルート型。</span><span class="sxs-lookup"><span data-stu-id="2ddff-545">The GC root type.</span></span><br/><br/><span data-ttu-id="2ddff-546">`0x0`: Stack</span><span class="sxs-lookup"><span data-stu-id="2ddff-546">`0x0`: Stack</span></span><br/><br/><span data-ttu-id="2ddff-547">`0x1`: Finalizer</span><span class="sxs-lookup"><span data-stu-id="2ddff-547">`0x1`: Finalizer</span></span><br/><br/><span data-ttu-id="2ddff-548">`0x2`: Handle</span><span class="sxs-lookup"><span data-stu-id="2ddff-548">`0x2`: Handle</span></span><br/><br/><span data-ttu-id="2ddff-549">`0x3`: Older</span><span class="sxs-lookup"><span data-stu-id="2ddff-549">`0x3`: Older</span></span><br/><br/><span data-ttu-id="2ddff-550">`0x4`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="2ddff-550">`0x4`: SizedRef</span></span><br/><br/><span data-ttu-id="2ddff-551">`0x5`: Overflow</span><span class="sxs-lookup"><span data-stu-id="2ddff-551">`0x5`: Overflow</span></span><br/><br/>|
|`Bytes`|`win:UInt64`|<span data-ttu-id="2ddff-552">マークされたバイト数。</span><span class="sxs-lookup"><span data-stu-id="2ddff-552">The number of bytes marked.</span></span>|

## <a name="gcjoin_v2-event"></a><span data-ttu-id="2ddff-553">GCJoin_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="2ddff-553">GCJoin_V2 event</span></span>

<span data-ttu-id="2ddff-554">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-554">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2ddff-555">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2ddff-555">Keyword for raising the event</span></span>|<span data-ttu-id="2ddff-556">Level</span><span class="sxs-lookup"><span data-stu-id="2ddff-556">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2ddff-557">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="2ddff-557">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2ddff-558">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="2ddff-558">Verbose (5)</span></span>|

<span data-ttu-id="2ddff-559">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-559">The following table shows the event information:</span></span>

|<span data-ttu-id="2ddff-560">Event</span><span class="sxs-lookup"><span data-stu-id="2ddff-560">Event</span></span>|<span data-ttu-id="2ddff-561">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ddff-561">Event ID</span></span>|<span data-ttu-id="2ddff-562">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2ddff-562">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCJoin_V2`|<span data-ttu-id="2ddff-563">203</span><span class="sxs-lookup"><span data-stu-id="2ddff-563">203</span></span>|<span data-ttu-id="2ddff-564">結合した GC スレッド。</span><span class="sxs-lookup"><span data-stu-id="2ddff-564">A GC thread joined.</span></span>|

<span data-ttu-id="2ddff-565">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2ddff-565">The following table shows the event data:</span></span>

|<span data-ttu-id="2ddff-566">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2ddff-566">Field name</span></span>|<span data-ttu-id="2ddff-567">データ型</span><span class="sxs-lookup"><span data-stu-id="2ddff-567">Data type</span></span>|<span data-ttu-id="2ddff-568">説明</span><span class="sxs-lookup"><span data-stu-id="2ddff-568">Description</span></span>|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|<span data-ttu-id="2ddff-569">ヒープ番号</span><span class="sxs-lookup"><span data-stu-id="2ddff-569">The heap number</span></span>|
|`JoinTime`|`win:UInt32`|<span data-ttu-id="2ddff-570">このイベントが結合の開始時に発生したか、または結合の終了時に発生したかを示す (`0x0` は結合の開始、`0x1` は結合の終了)</span><span class="sxs-lookup"><span data-stu-id="2ddff-570">Indicates whether this event is fired at the start of a join or end of a join (`0x0` for join start, `0x1` for join end)</span></span>|
|`JoinType`|`win:UInt32`|<span data-ttu-id="2ddff-571">結合の種類。</span><span class="sxs-lookup"><span data-stu-id="2ddff-571">The join type.</span></span> <br/><br/><span data-ttu-id="2ddff-572">`0x0`: 最後の結合</span><span class="sxs-lookup"><span data-stu-id="2ddff-572">`0x0`: Last Join</span></span><br/><br/><span data-ttu-id="2ddff-573">`0x1`: 結合</span><span class="sxs-lookup"><span data-stu-id="2ddff-573">`0x1`: Join</span></span> <br/><br/><span data-ttu-id="2ddff-574">`0x2`: 再起動</span><span class="sxs-lookup"><span data-stu-id="2ddff-574">`0x2`: Restart</span></span> <br/><br/><span data-ttu-id="2ddff-575">`0x3`: 最初の逆結合</span><span class="sxs-lookup"><span data-stu-id="2ddff-575">`0x3`: First Reverse Join</span></span><br/><br/><span data-ttu-id="2ddff-576">`0x4`: 逆結合</span><span class="sxs-lookup"><span data-stu-id="2ddff-576">`0x4`: Reverse Join</span></span><br/><br/>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2ddff-577">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2ddff-577">Unique ID for the instance of CoreCLR.</span></span>|

---
title: メソッド ランタイム イベント
description: CLR メソッド イベント、CLR メソッド マーカー、CLR メソッドの詳細なイベント、MethodJittingStarted など、メソッドに固有の診断情報を収集する .NET ランタイム イベントを参照してください。
ms.date: 11/13/2020
helpviewer_keywords:
- Method events (CoreCLR)
- ETW, EventPipe, LTTng method events (CoreCLR)
ms.openlocfilehash: f9d08efa420670cf7a8c863f115ff270998f2dca
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594042"
---
# <a name="net-runtime-method-events"></a><span data-ttu-id="2eea6-103">.NET ランタイム メソッド イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-103">.NET runtime method events</span></span>

<span data-ttu-id="2eea6-104">これらのイベントは、メソッド固有の情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-104">These events collect information that is specific to methods.</span></span> <span data-ttu-id="2eea6-105">これらのイベントのペイロードは、シンボルの解決に必要です。</span><span class="sxs-lookup"><span data-stu-id="2eea6-105">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="2eea6-106">また、これらのイベントは、読み込まれたメソッドやアンロードされたメソッドなどの有用な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-106">In addition, these events provide helpful information such as methods that are loaded and unloaded.</span></span> <span data-ttu-id="2eea6-107">診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2eea6-107">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

<span data-ttu-id="2eea6-108">すべてのメソッド イベントのレベルは「情報提供 (4)」です。</span><span class="sxs-lookup"><span data-stu-id="2eea6-108">All method events have a level of "Informational (4)".</span></span> <span data-ttu-id="2eea6-109">すべてのメソッド詳細イベントのレベルは「詳細 (5)」です。</span><span class="sxs-lookup"><span data-stu-id="2eea6-109">All method verbose events have a level of "Verbose (5)".</span></span>

<span data-ttu-id="2eea6-110">すべてのメソッド イベントは、ランタイム プロバイダーのもとでは `JITKeyword` (0x10) キーワードまたは `NGenKeyword` (0x20) キーワードが発生させ、ランダウン プロバイダーのもとでは `JitRundownKeyword` (0x10) または `NGENRundownKeyword` (0x20) が発生させます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-110">All method events are raised by the `JITKeyword` (0x10) keyword or the `NGenKeyword` (0x20) keyword under the runtime provider, or `JitRundownKeyword` (0x10) or `NGENRundownKeyword` (0x20) under the rundown provider.</span></span>

<span data-ttu-id="2eea6-111">これらのイベントの V2 バージョンには ReJITID が含まれますが、V1 バージョンには含まれません。</span><span class="sxs-lookup"><span data-stu-id="2eea6-111">The V2 versions of these events include the ReJITID, the V1 versions do not.</span></span>

## <a name="methodload_v1-event"></a><span data-ttu-id="2eea6-112">MethodLoad_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-112">MethodLoad_V1 event</span></span>

<span data-ttu-id="2eea6-113">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-113">The following table shows the event information:</span></span>

|<span data-ttu-id="2eea6-114">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-114">Event</span></span>|<span data-ttu-id="2eea6-115">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-115">Event ID</span></span>|<span data-ttu-id="2eea6-116">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-116">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|<span data-ttu-id="2eea6-117">141</span><span class="sxs-lookup"><span data-stu-id="2eea6-117">141</span></span>|<span data-ttu-id="2eea6-118">メソッドが Just-In-Time 読み込み (JIT 読み込み) される時点、または NGEN イメージが読み込まれる時点で発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-118">Raised when a method is just-in-time loaded (JIT-loaded) or an NGEN image is loaded.</span></span> <span data-ttu-id="2eea6-119">動的メソッドとジェネリック メソッドは、メソッドの読み込みにこのバージョンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="2eea6-119">Dynamic and generic methods do not use this version for method loads.</span></span> <span data-ttu-id="2eea6-120">JIT ヘルパーがこのバージョンを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="2eea6-120">JIT helpers never use this version.</span></span>|

|<span data-ttu-id="2eea6-121">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-121">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-122">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-122">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-123">`JITKeyword` (0x10) ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="2eea6-123">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="2eea6-124">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-124">Informational (4)</span></span>|
|<span data-ttu-id="2eea6-125">`NGenKeyword` (0x20) ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="2eea6-125">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="2eea6-126">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-126">Informational (4)</span></span>|

|<span data-ttu-id="2eea6-127">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-127">Field name</span></span>|<span data-ttu-id="2eea6-128">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-128">Data type</span></span>|<span data-ttu-id="2eea6-129">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-129">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-130">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-130">Unique identifier of a method.</span></span> <span data-ttu-id="2eea6-131">JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-131">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="2eea6-132">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-132">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="2eea6-133">メソッドの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2eea6-133">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="2eea6-134">メソッドのサイズ。</span><span class="sxs-lookup"><span data-stu-id="2eea6-134">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="2eea6-135">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="2eea6-135">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="2eea6-136">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-136">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="2eea6-137">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-137">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="2eea6-138">0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-138">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="2eea6-139">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-139">0x8: Helper method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-140">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-140">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodload_v2-event"></a><span data-ttu-id="2eea6-141">MethodLoad_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-141">MethodLoad_V2 event</span></span>

|<span data-ttu-id="2eea6-142">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-142">Event</span></span>|<span data-ttu-id="2eea6-143">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-143">Event ID</span></span>|<span data-ttu-id="2eea6-144">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-144">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodLoad_V2`|<span data-ttu-id="2eea6-145">141</span><span class="sxs-lookup"><span data-stu-id="2eea6-145">141</span></span>|<span data-ttu-id="2eea6-146">メソッドが Just-In-Time 読み込み (JIT 読み込み) される時点、または NGEN イメージが読み込まれる時点で発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-146">Raised when a method is just-in-time loaded (JIT-loaded) or an NGEN image is loaded.</span></span> <span data-ttu-id="2eea6-147">動的メソッドとジェネリック メソッドは、メソッドの読み込みにこのバージョンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="2eea6-147">Dynamic and generic methods do not use this version for method loads.</span></span> <span data-ttu-id="2eea6-148">JIT ヘルパーがこのバージョンを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="2eea6-148">JIT helpers never use this version.</span></span>|

|<span data-ttu-id="2eea6-149">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-149">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-150">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-150">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-151">`JITKeyword` (0x10) ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="2eea6-151">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="2eea6-152">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-152">Informational (4)</span></span>|
|<span data-ttu-id="2eea6-153">`NGenKeyword` (0x20) ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="2eea6-153">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="2eea6-154">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-154">Informational (4)</span></span>|

|<span data-ttu-id="2eea6-155">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-155">Field name</span></span>|<span data-ttu-id="2eea6-156">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-156">Data type</span></span>|<span data-ttu-id="2eea6-157">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-157">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-158">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-158">Unique identifier of a method.</span></span> <span data-ttu-id="2eea6-159">JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-159">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="2eea6-160">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-160">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="2eea6-161">メソッドの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2eea6-161">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="2eea6-162">メソッドのサイズ。</span><span class="sxs-lookup"><span data-stu-id="2eea6-162">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="2eea6-163">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="2eea6-163">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="2eea6-164">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-164">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="2eea6-165">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-165">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="2eea6-166">0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-166">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="2eea6-167">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-167">0x8: Helper method.</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="2eea6-168">メソッドの ReJIT ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-168">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-169">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-169">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunload_v1-event"></a><span data-ttu-id="2eea6-170">MethodUnLoad_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-170">MethodUnLoad_V1 event</span></span>

|<span data-ttu-id="2eea6-171">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-171">Event</span></span>|<span data-ttu-id="2eea6-172">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-172">Event ID</span></span>|<span data-ttu-id="2eea6-173">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-173">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodUnLoad_V1`|<span data-ttu-id="2eea6-174">142</span><span class="sxs-lookup"><span data-stu-id="2eea6-174">142</span></span>|<span data-ttu-id="2eea6-175">モジュールがアンロードされるとき、またはアプリケーション ドメインが破棄されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-175">Raised when a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="2eea6-176">動的メソッドがメソッドのアンロードにこのバージョンを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="2eea6-176">Dynamic methods never use this version for method unloads.</span></span>|

|<span data-ttu-id="2eea6-177">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-177">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-178">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-178">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-179">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="2eea6-179">`JITKeyword` (0x10)</span></span>|<span data-ttu-id="2eea6-180">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-180">Informational (4)</span></span>|
|<span data-ttu-id="2eea6-181">`NGenKeyword` (0x20)</span><span class="sxs-lookup"><span data-stu-id="2eea6-181">`NGenKeyword` (0x20)</span></span>|<span data-ttu-id="2eea6-182">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-182">Informational (4)</span></span>|

|<span data-ttu-id="2eea6-183">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-183">Field name</span></span>|<span data-ttu-id="2eea6-184">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-184">Data type</span></span>|<span data-ttu-id="2eea6-185">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-185">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-186">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-186">Unique identifier of a method.</span></span> <span data-ttu-id="2eea6-187">JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-187">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="2eea6-188">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-188">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="2eea6-189">メソッドの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2eea6-189">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="2eea6-190">メソッドのサイズ。</span><span class="sxs-lookup"><span data-stu-id="2eea6-190">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="2eea6-191">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="2eea6-191">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="2eea6-192">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-192">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="2eea6-193">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-193">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="2eea6-194">0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-194">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="2eea6-195">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-195">0x8: Helper method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-196">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-196">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunload_v2-event"></a><span data-ttu-id="2eea6-197">MethodUnLoad_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-197">MethodUnLoad_V2 event</span></span>

|<span data-ttu-id="2eea6-198">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-198">Event</span></span>|<span data-ttu-id="2eea6-199">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-199">Event ID</span></span>|<span data-ttu-id="2eea6-200">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-200">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodUnLoad_V2`|<span data-ttu-id="2eea6-201">142</span><span class="sxs-lookup"><span data-stu-id="2eea6-201">142</span></span>|<span data-ttu-id="2eea6-202">モジュールがアンロードされるとき、またはアプリケーション ドメインが破棄されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-202">Raised when a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="2eea6-203">動的メソッドがメソッドのアンロードにこのバージョンを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="2eea6-203">Dynamic methods never use this version for method unloads.</span></span>|

|<span data-ttu-id="2eea6-204">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-204">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-205">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-205">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-206">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="2eea6-206">`JITKeyword` (0x10)</span></span>|<span data-ttu-id="2eea6-207">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-207">Informational (4)</span></span>|
|<span data-ttu-id="2eea6-208">`NGenKeyword` (0x20)</span><span class="sxs-lookup"><span data-stu-id="2eea6-208">`NGenKeyword` (0x20)</span></span>|<span data-ttu-id="2eea6-209">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-209">Informational (4)</span></span>|

|<span data-ttu-id="2eea6-210">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-210">Field name</span></span>|<span data-ttu-id="2eea6-211">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-211">Data type</span></span>|<span data-ttu-id="2eea6-212">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-212">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-213">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-213">Unique identifier of a method.</span></span> <span data-ttu-id="2eea6-214">JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-214">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="2eea6-215">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-215">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="2eea6-216">メソッドの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2eea6-216">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="2eea6-217">メソッドのサイズ。</span><span class="sxs-lookup"><span data-stu-id="2eea6-217">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="2eea6-218">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="2eea6-218">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="2eea6-219">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-219">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="2eea6-220">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-220">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="2eea6-221">0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-221">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="2eea6-222">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-222">0x8: Helper method.</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="2eea6-223">メソッドの ReJIT ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-223">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-224">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-224">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="r2rgetentrypoint-event"></a><span data-ttu-id="2eea6-225">R2RGetEntryPoint イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-225">R2RGetEntryPoint event</span></span>

|<span data-ttu-id="2eea6-226">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-226">Event</span></span>|<span data-ttu-id="2eea6-227">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-227">Event ID</span></span>|<span data-ttu-id="2eea6-228">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-228">Description</span></span>|
|----------------|---------------|-----------------|
|`R2RGetEntryPoint`|<span data-ttu-id="2eea6-229">159</span><span class="sxs-lookup"><span data-stu-id="2eea6-229">159</span></span>|<span data-ttu-id="2eea6-230">R2R エントリ ポイント参照が終了したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-230">Raised when an R2R entry point lookup ends.</span></span>|

|<span data-ttu-id="2eea6-231">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-231">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-232">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-232">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-233">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="2eea6-233">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="2eea6-234">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-234">Informational (4)</span></span>|
|<span data-ttu-id="2eea6-235">`NGenKeyword` (0x20)</span><span class="sxs-lookup"><span data-stu-id="2eea6-235">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="2eea6-236">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-236">Informational (4)</span></span>|

|<span data-ttu-id="2eea6-237">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-237">Field name</span></span>|<span data-ttu-id="2eea6-238">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-238">Data type</span></span>|<span data-ttu-id="2eea6-239">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-239">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-240">R2R メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-240">Unique identifier of a R2R method.</span></span>|
|`MethodNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-241">検索するメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-241">The namespace of method being looked up.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="2eea6-242">検索するメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-242">The name of the method being looked up.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-243">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-243">Signature of the method (comma-separated list of type names).</span></span>|
|`EntryPoint`|`win:UInt64`|<span data-ttu-id="2eea6-244">R2R メソッドのエントリ ポイントへのポインター</span><span class="sxs-lookup"><span data-stu-id="2eea6-244">The pointer to the entry point of the R2R method</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-245">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-245">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="r2rgetentrypointstart-event"></a><span data-ttu-id="2eea6-246">R2RGetEntryPointStart イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-246">R2RGetEntryPointStart event</span></span>

|<span data-ttu-id="2eea6-247">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-247">Event</span></span>|<span data-ttu-id="2eea6-248">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-248">Event ID</span></span>|<span data-ttu-id="2eea6-249">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-249">Description</span></span>|
|----------------|---------------|-----------------|
|`R2RGetEntryPointStart`|<span data-ttu-id="2eea6-250">160</span><span class="sxs-lookup"><span data-stu-id="2eea6-250">160</span></span>|<span data-ttu-id="2eea6-251">R2R エントリ ポイント参照が開始したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-251">Raised when an R2R entry point lookup starts.</span></span>|

|<span data-ttu-id="2eea6-252">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-252">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-253">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-253">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-254">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="2eea6-254">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="2eea6-255">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-255">Informational (4)</span></span>|
|<span data-ttu-id="2eea6-256">`NGenKeyword` (0x20)</span><span class="sxs-lookup"><span data-stu-id="2eea6-256">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="2eea6-257">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-257">Informational (4)</span></span>|

|<span data-ttu-id="2eea6-258">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-258">Field name</span></span>|<span data-ttu-id="2eea6-259">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-259">Data type</span></span>|<span data-ttu-id="2eea6-260">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-260">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-261">R2R メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-261">Unique identifier of a R2R method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-262">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-262">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodloadverbose_v1-event"></a><span data-ttu-id="2eea6-263">MethodLoadVerbose_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-263">MethodLoadVerbose_V1 event</span></span>

|<span data-ttu-id="2eea6-264">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-264">Event</span></span>|<span data-ttu-id="2eea6-265">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-265">Event ID</span></span>|<span data-ttu-id="2eea6-266">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-266">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|<span data-ttu-id="2eea6-267">143</span><span class="sxs-lookup"><span data-stu-id="2eea6-267">143</span></span>|<span data-ttu-id="2eea6-268">メソッドが JIT 読み込みされるとき、または NGEN イメージが読み込まれるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-268">Raised when a method is JIT-loaded or an NGEN image is loaded.</span></span> <span data-ttu-id="2eea6-269">動的メソッドとジェネリック メソッドは、メソッドの読み込みに常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-269">Dynamic and generic methods always use this version for method loads.</span></span> <span data-ttu-id="2eea6-270">JIT ヘルパーは常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-270">JIT helpers always use this version.</span></span>|

|<span data-ttu-id="2eea6-271">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-271">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-272">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-272">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-273">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="2eea6-273">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="2eea6-274">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-274">Informational (4)</span></span>|
|<span data-ttu-id="2eea6-275">`NGenKeyword` (0x20)</span><span class="sxs-lookup"><span data-stu-id="2eea6-275">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="2eea6-276">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-276">Informational (4)</span></span>|

|<span data-ttu-id="2eea6-277">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-277">Field name</span></span>|<span data-ttu-id="2eea6-278">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-278">Data type</span></span>|<span data-ttu-id="2eea6-279">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-279">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-280">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-280">Unique identifier of the method.</span></span> <span data-ttu-id="2eea6-281">JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-281">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="2eea6-282">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-282">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="2eea6-283">開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2eea6-283">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="2eea6-284">メソッドの長さ。</span><span class="sxs-lookup"><span data-stu-id="2eea6-284">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="2eea6-285">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="2eea6-285">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="2eea6-286">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-286">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="2eea6-287">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-287">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="2eea6-288">0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)</span><span class="sxs-lookup"><span data-stu-id="2eea6-288">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="2eea6-289">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-289">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="2eea6-290">メソッドに関連付けられた完全な名前空間名。</span><span class="sxs-lookup"><span data-stu-id="2eea6-290">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="2eea6-291">メソッドに関連付けられた完全クラス名。</span><span class="sxs-lookup"><span data-stu-id="2eea6-291">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-292">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-292">Signature of the method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-293">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-293">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodloadverbose_v2-event"></a><span data-ttu-id="2eea6-294">MethodLoadVerbose_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-294">MethodLoadVerbose_V2 event</span></span>

|<span data-ttu-id="2eea6-295">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-295">Event</span></span>|<span data-ttu-id="2eea6-296">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-296">Event ID</span></span>|<span data-ttu-id="2eea6-297">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-297">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|<span data-ttu-id="2eea6-298">143</span><span class="sxs-lookup"><span data-stu-id="2eea6-298">143</span></span>|<span data-ttu-id="2eea6-299">メソッドが JIT 読み込みされるとき、または NGEN イメージが読み込まれるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-299">Raised when a method is JIT-loaded or an NGEN image is loaded.</span></span> <span data-ttu-id="2eea6-300">動的メソッドとジェネリック メソッドは、メソッドの読み込みに常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-300">Dynamic and generic methods always use this version for method loads.</span></span> <span data-ttu-id="2eea6-301">JIT ヘルパーは常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-301">JIT helpers always use this version.</span></span>|

|<span data-ttu-id="2eea6-302">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-302">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-303">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-304">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="2eea6-304">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="2eea6-305">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-305">Informational (4)</span></span>|
|<span data-ttu-id="2eea6-306">`NGenKeyword` (0x20)</span><span class="sxs-lookup"><span data-stu-id="2eea6-306">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="2eea6-307">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-307">Informational (4)</span></span>|

|<span data-ttu-id="2eea6-308">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-308">Field name</span></span>|<span data-ttu-id="2eea6-309">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-309">Data type</span></span>|<span data-ttu-id="2eea6-310">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-310">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-311">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-311">Unique identifier of the method.</span></span> <span data-ttu-id="2eea6-312">JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-312">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="2eea6-313">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-313">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="2eea6-314">開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2eea6-314">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="2eea6-315">メソッドの長さ。</span><span class="sxs-lookup"><span data-stu-id="2eea6-315">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="2eea6-316">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="2eea6-316">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="2eea6-317">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-317">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="2eea6-318">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-318">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="2eea6-319">0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)</span><span class="sxs-lookup"><span data-stu-id="2eea6-319">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="2eea6-320">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-320">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="2eea6-321">メソッドに関連付けられた完全な名前空間名。</span><span class="sxs-lookup"><span data-stu-id="2eea6-321">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="2eea6-322">メソッドに関連付けられた完全クラス名。</span><span class="sxs-lookup"><span data-stu-id="2eea6-322">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-323">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-323">Signature of the method (comma-separated list of type names).</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="2eea6-324">メソッドの ReJIT ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-324">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-325">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-325">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunloadverbose_v1-event"></a><span data-ttu-id="2eea6-326">MethodUnLoadVerbose_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-326">MethodUnLoadVerbose_V1 event</span></span>

|<span data-ttu-id="2eea6-327">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-327">Event</span></span>|<span data-ttu-id="2eea6-328">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-328">Event ID</span></span>|<span data-ttu-id="2eea6-329">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-329">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V1`|<span data-ttu-id="2eea6-330">144</span><span class="sxs-lookup"><span data-stu-id="2eea6-330">144</span></span>|<span data-ttu-id="2eea6-331">動的メソッドが破棄されるとき、またはモジュールがアンロードされるとき、あるいはアプリケーション ドメインが破棄されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-331">Raised when a dynamic method is destroyed, a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="2eea6-332">動的メソッドは、メソッドのアンロードに常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-332">Dynamic methods always use this version for method unloads.</span></span>|

|<span data-ttu-id="2eea6-333">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-333">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-334">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-334">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-335">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="2eea6-335">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="2eea6-336">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-336">Informational (4)</span></span>|
|<span data-ttu-id="2eea6-337">`NGenKeyword` (0x20)</span><span class="sxs-lookup"><span data-stu-id="2eea6-337">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="2eea6-338">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-338">Informational (4)</span></span>|

|<span data-ttu-id="2eea6-339">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-339">Field name</span></span>|<span data-ttu-id="2eea6-340">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-340">Data type</span></span>|<span data-ttu-id="2eea6-341">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-341">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-342">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-342">Unique identifier of the method.</span></span> <span data-ttu-id="2eea6-343">JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-343">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="2eea6-344">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-344">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="2eea6-345">開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2eea6-345">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="2eea6-346">メソッドの長さ。</span><span class="sxs-lookup"><span data-stu-id="2eea6-346">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="2eea6-347">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="2eea6-347">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="2eea6-348">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-348">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="2eea6-349">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-349">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="2eea6-350">0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)</span><span class="sxs-lookup"><span data-stu-id="2eea6-350">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="2eea6-351">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-351">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="2eea6-352">メソッドに関連付けられた完全な名前空間名。</span><span class="sxs-lookup"><span data-stu-id="2eea6-352">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="2eea6-353">メソッドに関連付けられた完全クラス名。</span><span class="sxs-lookup"><span data-stu-id="2eea6-353">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-354">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-354">Signature of the method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-355">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-355">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunloadverbose_v2-event"></a><span data-ttu-id="2eea6-356">MethodUnLoadVerbose_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-356">MethodUnLoadVerbose_V2 event</span></span>

|<span data-ttu-id="2eea6-357">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-357">Event</span></span>|<span data-ttu-id="2eea6-358">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-358">Event ID</span></span>|<span data-ttu-id="2eea6-359">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-359">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V2`|<span data-ttu-id="2eea6-360">144</span><span class="sxs-lookup"><span data-stu-id="2eea6-360">144</span></span>|<span data-ttu-id="2eea6-361">動的メソッドが破棄されるとき、またはモジュールがアンロードされるとき、あるいはアプリケーション ドメインが破棄されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-361">Raised when a dynamic method is destroyed, a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="2eea6-362">動的メソッドは、メソッドのアンロードに常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-362">Dynamic methods always use this version for method unloads.</span></span>|

|<span data-ttu-id="2eea6-363">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-363">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-364">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-364">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-365">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="2eea6-365">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="2eea6-366">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-366">Informational (4)</span></span>|
|<span data-ttu-id="2eea6-367">`NGenKeyword` (0x20)</span><span class="sxs-lookup"><span data-stu-id="2eea6-367">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="2eea6-368">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2eea6-368">Informational (4)</span></span>|

|<span data-ttu-id="2eea6-369">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-369">Field name</span></span>|<span data-ttu-id="2eea6-370">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-370">Data type</span></span>|<span data-ttu-id="2eea6-371">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-371">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-372">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-372">Unique identifier of the method.</span></span> <span data-ttu-id="2eea6-373">JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-373">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="2eea6-374">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-374">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="2eea6-375">開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2eea6-375">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="2eea6-376">メソッドの長さ。</span><span class="sxs-lookup"><span data-stu-id="2eea6-376">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="2eea6-377">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="2eea6-377">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="2eea6-378">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-378">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="2eea6-379">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-379">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="2eea6-380">0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)</span><span class="sxs-lookup"><span data-stu-id="2eea6-380">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="2eea6-381">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="2eea6-381">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="2eea6-382">メソッドに関連付けられた完全な名前空間名。</span><span class="sxs-lookup"><span data-stu-id="2eea6-382">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="2eea6-383">メソッドに関連付けられた完全クラス名。</span><span class="sxs-lookup"><span data-stu-id="2eea6-383">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-384">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-384">Signature of the method (comma-separated list of type names).</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="2eea6-385">メソッドの ReJIT ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-385">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-386">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-386">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjittingstarted_v1-event"></a><span data-ttu-id="2eea6-387">MethodJittingStarted_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-387">MethodJittingStarted_V1 event</span></span>

<span data-ttu-id="2eea6-388">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-388">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2eea6-389">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-389">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-390">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-390">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-391">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="2eea6-391">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="2eea6-392">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="2eea6-392">Verbose (5)</span></span>|
|<span data-ttu-id="2eea6-393">`NGenKeyword` (0x20)</span><span class="sxs-lookup"><span data-stu-id="2eea6-393">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="2eea6-394">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="2eea6-394">Verbose (5)</span></span>|

|<span data-ttu-id="2eea6-395">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-395">Event</span></span>|<span data-ttu-id="2eea6-396">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-396">Event ID</span></span>|<span data-ttu-id="2eea6-397">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-397">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJittingStarted_V1`|<span data-ttu-id="2eea6-398">145</span><span class="sxs-lookup"><span data-stu-id="2eea6-398">145</span></span>|<span data-ttu-id="2eea6-399">メソッドが JIT コンパイルされているときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-399">Raised when a method is being JIT-compiled.</span></span>|

|<span data-ttu-id="2eea6-400">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-400">Field name</span></span>|<span data-ttu-id="2eea6-401">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-401">Data type</span></span>|<span data-ttu-id="2eea6-402">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-402">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-403">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-403">Unique identifier of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="2eea6-404">このメソッドが属するモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-404">Identifier of the module to which this method belongs.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="2eea6-405">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="2eea6-405">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodILSize`|`win:UInt32`|<span data-ttu-id="2eea6-406">JIT コンパイルされているメソッドの Common Intermediate Language (CIL) のサイズ。</span><span class="sxs-lookup"><span data-stu-id="2eea6-406">The size of the Common Intermediate Language (CIL) for the method that is being JIT-compiled.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="2eea6-407">メソッドに関連付けられた完全クラス名。</span><span class="sxs-lookup"><span data-stu-id="2eea6-407">Full class name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="2eea6-408">メソッドの名前です。</span><span class="sxs-lookup"><span data-stu-id="2eea6-408">Name of the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-409">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-409">Signature of the method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-410">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-410">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjitinliningsucceeded-event"></a><span data-ttu-id="2eea6-411">MethodJitInliningSucceeded イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-411">MethodJitInliningSucceeded event</span></span>

|<span data-ttu-id="2eea6-412">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-412">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-413">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-413">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-414">`JITTracingKeyword` (0x1000)</span><span class="sxs-lookup"><span data-stu-id="2eea6-414">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="2eea6-415">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="2eea6-415">Verbose (5)</span></span>|

|<span data-ttu-id="2eea6-416">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-416">Event</span></span>|<span data-ttu-id="2eea6-417">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-417">Event ID</span></span>|<span data-ttu-id="2eea6-418">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-418">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitInliningSucceeded`|<span data-ttu-id="2eea6-419">185</span><span class="sxs-lookup"><span data-stu-id="2eea6-419">185</span></span>|<span data-ttu-id="2eea6-420">JIT コンパイラによってメソッドが正常にインライン展開された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-420">Raised when a method is successfully inlined by the JIT compiler.</span></span>|

|<span data-ttu-id="2eea6-421">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-421">Field name</span></span>|<span data-ttu-id="2eea6-422">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-422">Data type</span></span>|<span data-ttu-id="2eea6-423">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-423">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-424">コンパイルされるメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-424">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="2eea6-425">コンパイルされるメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-425">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-426">コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-426">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`InlinerNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-427">インライナ ("parent") メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-427">The namespace of inliner ("parent") method.</span></span>|
|`InlinerName`|`win:UnicodeString`|<span data-ttu-id="2eea6-428">インライナ ("parent") メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-428">Name of the inliner ("parent") method.</span></span>|
|`InlinerNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-429">インライナ ("parent") メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-429">Signature of the inliner ("parent") method (comma-separated list of type names).</span></span>|
|`InlineeNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-430">インライン展開先 ("child") メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-430">The namespace of inlinee ("child") method.</span></span>|
|`InlineeName`|`win:UnicodeString`|<span data-ttu-id="2eea6-431">インライン展開先 ("child") メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-431">Name of the inlinee ("child") method.</span></span>|
|`InlineeNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-432">インライン展開先 ("child") メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-432">Signature of the inlinee ("child") method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-433">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-433">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjitinliningfailed-event"></a><span data-ttu-id="2eea6-434">MethodJitInliningFailed イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-434">MethodJitInliningFailed event</span></span>

|<span data-ttu-id="2eea6-435">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-435">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-436">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-436">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-437">`JITTracingKeyword` (0x1000)</span><span class="sxs-lookup"><span data-stu-id="2eea6-437">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="2eea6-438">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="2eea6-438">Verbose (5)</span></span>|

|<span data-ttu-id="2eea6-439">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-439">Event</span></span>|<span data-ttu-id="2eea6-440">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-440">Event ID</span></span>|<span data-ttu-id="2eea6-441">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-441">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitInliningFailed`|<span data-ttu-id="2eea6-442">192</span><span class="sxs-lookup"><span data-stu-id="2eea6-442">192</span></span>|<span data-ttu-id="2eea6-443">JIT コンパイラによるメソッドのインライン展開が失敗した場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="2eea6-443">Raised when a method was failed to be inlined by the JIT compiler.</span></span>|

|<span data-ttu-id="2eea6-444">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-444">Field name</span></span>|<span data-ttu-id="2eea6-445">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-445">Data type</span></span>|<span data-ttu-id="2eea6-446">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-446">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-447">コンパイルされるメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-447">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="2eea6-448">コンパイルされるメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-448">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-449">コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-449">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`InlinerNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-450">インライナ ("parent") メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-450">The namespace of inliner ("parent") method.</span></span>|
|`InlinerName`|`win:UnicodeString`|<span data-ttu-id="2eea6-451">インライナ ("parent") メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-451">Name of the inliner ("parent") method.</span></span>|
|`InlinerNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-452">インライナ ("parent") メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-452">Signature of the inliner ("parent") method (comma-separated list of type names).</span></span>|
|`InlineeNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-453">インライン展開先 ("child") メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-453">The namespace of inlinee ("child") method.</span></span>|
|`InlineeName`|`win:UnicodeString`|<span data-ttu-id="2eea6-454">インライン展開先 ("child") メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-454">Name of the inlinee ("child") method.</span></span>|
|`InlineeNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-455">インライン展開先 ("child") メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-455">Signature of the inlinee ("child") method (comma-separated list of type names).</span></span>|
|`FailAlways`|`win:Boolean`|<span data-ttu-id="2eea6-456">メソッドがインライン展開不可能としてマークされているかどうか。</span><span class="sxs-lookup"><span data-stu-id="2eea6-456">Whether the method is marked as not inlinable.</span></span>|
|`FailReason`|`win:UnicodeString`|<span data-ttu-id="2eea6-457">インライン展開が失敗した理由。</span><span class="sxs-lookup"><span data-stu-id="2eea6-457">Reason inlining failed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-458">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-458">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjittailcallsucceeded-event"></a><span data-ttu-id="2eea6-459">MethodJitTailCallSucceeded イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-459">MethodJitTailCallSucceeded event</span></span>

|<span data-ttu-id="2eea6-460">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-460">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-461">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-461">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-462">`JITTracingKeyword` (0x1000)</span><span class="sxs-lookup"><span data-stu-id="2eea6-462">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="2eea6-463">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="2eea6-463">Verbose (5)</span></span>|

|<span data-ttu-id="2eea6-464">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-464">Event</span></span>|<span data-ttu-id="2eea6-465">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-465">Event ID</span></span>|<span data-ttu-id="2eea6-466">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-466">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitTailCallSucceeded`|<span data-ttu-id="2eea6-467">192</span><span class="sxs-lookup"><span data-stu-id="2eea6-467">192</span></span>|<span data-ttu-id="2eea6-468">メソッドの末尾呼び出しが成功する可能性がある場合に JIT コンパイラが発生させます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-468">Raised by the JIT compiler when a method can be successfully tail called.</span></span>|

|<span data-ttu-id="2eea6-469">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-469">Field name</span></span>|<span data-ttu-id="2eea6-470">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-470">Data type</span></span>|<span data-ttu-id="2eea6-471">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-471">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-472">コンパイルされるメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-472">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="2eea6-473">コンパイルされるメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-473">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-474">コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-474">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`CallerNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-475">呼び出し元メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-475">Namespace of the caller method.</span></span>|
|`CallerName`|`win:UnicodeString`|<span data-ttu-id="2eea6-476">呼び出し元メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-476">Name of the caller method.</span></span>|
|`CallerNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-477">呼び出し元メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-477">Signature of the caller method (Comma-separated list of type names).</span></span>|
|`CalleeNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-478">呼び出し先メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-478">Namespace of the callee method.</span></span>|
|`CalleeName`|`win:UnicodeString`|<span data-ttu-id="2eea6-479">呼び出し先メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-479">Name of the callee method.</span></span>|
|`CalleeNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-480">呼び出し先メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-480">Signature of the callee method (Comma-separated list of type names).</span></span>|
|`TailPrefix`|`win:Boolean`|<span data-ttu-id="2eea6-481">末尾プレフィックス命令であるかどうか。</span><span class="sxs-lookup"><span data-stu-id="2eea6-481">Whether it is a tail prefix instruction.</span></span>|
|`TailCallType`|`win:UInt32`|<span data-ttu-id="2eea6-482">末尾呼び出しの種類。</span><span class="sxs-lookup"><span data-stu-id="2eea6-482">The type of tail call.</span></span><br/><br/><span data-ttu-id="2eea6-483">0: 最適化された末尾呼び出し (epilog + jmp)</span><span class="sxs-lookup"><span data-stu-id="2eea6-483">0: Optimized tail call (epilog + jmp)</span></span><br/><br/><span data-ttu-id="2eea6-484">1: 再帰的な末尾呼び出し (メソッドの末尾呼び出し自体)</span><span class="sxs-lookup"><span data-stu-id="2eea6-484">1: Recursive tail call (method tail calls itself)</span></span><br/><br/><span data-ttu-id="2eea6-485">2: ヘルパーによる末尾呼び出し</span><span class="sxs-lookup"><span data-stu-id="2eea6-485">2: Helper assisted tail call</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-486">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-486">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjittailcallfailed-event"></a><span data-ttu-id="2eea6-487">MethodJitTailCallFailed イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-487">MethodJitTailCallFailed event</span></span>

|<span data-ttu-id="2eea6-488">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-488">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-489">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-489">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-490">`JITTracingKeyword` (0x1000)</span><span class="sxs-lookup"><span data-stu-id="2eea6-490">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="2eea6-491">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="2eea6-491">Verbose (5)</span></span>|

|<span data-ttu-id="2eea6-492">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-492">Event</span></span>|<span data-ttu-id="2eea6-493">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-493">Event ID</span></span>|<span data-ttu-id="2eea6-494">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-494">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitTailCallFailed`|<span data-ttu-id="2eea6-495">191</span><span class="sxs-lookup"><span data-stu-id="2eea6-495">191</span></span>|<span data-ttu-id="2eea6-496">メソッドの末尾呼び出しが失敗した場合に JIT コンパイラが発生させます。</span><span class="sxs-lookup"><span data-stu-id="2eea6-496">Raised by the JIT compiler when a method was failed to be tail called.</span></span>|

|<span data-ttu-id="2eea6-497">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-497">Field name</span></span>|<span data-ttu-id="2eea6-498">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-498">Data type</span></span>|<span data-ttu-id="2eea6-499">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-499">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-500">コンパイルされるメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-500">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="2eea6-501">コンパイルされるメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-501">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-502">コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-502">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`CallerNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-503">呼び出し元メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-503">Namespace of the caller method.</span></span>|
|<span data-ttu-id="2eea6-504">`CallerNam`e</span><span class="sxs-lookup"><span data-stu-id="2eea6-504">`CallerNam`e</span></span>|`win:UnicodeString`|<span data-ttu-id="2eea6-505">呼び出し元メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-505">Name of the caller method.</span></span>|
|`CallerNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-506">呼び出し元メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-506">Signature of the caller method (Comma-separated list of type names).</span></span>|
|`CalleeNamespace`|`win:UnicodeString`|<span data-ttu-id="2eea6-507">呼び出し先メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="2eea6-507">Namespace of the callee method.</span></span>|
|`CalleeName`|`win:UnicodeString`|<span data-ttu-id="2eea6-508">呼び出し先メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2eea6-508">Name of the callee method.</span></span>|
|`CalleeNameSignature`|`win:UnicodeString`|<span data-ttu-id="2eea6-509">呼び出し先メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="2eea6-509">Signature of the callee method (Comma-separated list of type names).</span></span>|
|`TailPrefix`|`win:Boolean`|<span data-ttu-id="2eea6-510">末尾プレフィックス命令であるかどうか。</span><span class="sxs-lookup"><span data-stu-id="2eea6-510">Whether it is a tail prefix instruction.</span></span>|
|`FailReason`|`win:UnicodeString`|<span data-ttu-id="2eea6-511">末尾の呼び出しが失敗した理由。</span><span class="sxs-lookup"><span data-stu-id="2eea6-511">Reason tail call failed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-512">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-512">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodiltonativemap-event"></a><span data-ttu-id="2eea6-513">MethodILToNativeMap イベント</span><span class="sxs-lookup"><span data-stu-id="2eea6-513">MethodILToNativeMap event</span></span>

|<span data-ttu-id="2eea6-514">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2eea6-514">Keyword for raising the event</span></span>|<span data-ttu-id="2eea6-515">Level</span><span class="sxs-lookup"><span data-stu-id="2eea6-515">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2eea6-516">`JittedMethodILToNativeMapKeyword` (0x20000)</span><span class="sxs-lookup"><span data-stu-id="2eea6-516">`JittedMethodILToNativeMapKeyword` (0x20000)</span></span> |<span data-ttu-id="2eea6-517">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="2eea6-517">Verbose (5)</span></span>|

|<span data-ttu-id="2eea6-518">Event</span><span class="sxs-lookup"><span data-stu-id="2eea6-518">Event</span></span>|<span data-ttu-id="2eea6-519">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2eea6-519">Event ID</span></span>|<span data-ttu-id="2eea6-520">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-520">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodILToNativeMap`|<span data-ttu-id="2eea6-521">190</span><span class="sxs-lookup"><span data-stu-id="2eea6-521">190</span></span>|<span data-ttu-id="2eea6-522">JIT コンパイル済みメソッドの IL からネイティブへのマップ イベントをマップします。</span><span class="sxs-lookup"><span data-stu-id="2eea6-522">Maps the IL-to-native map event for JIT-compiled methods.</span></span>|

|<span data-ttu-id="2eea6-523">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2eea6-523">Field name</span></span>|<span data-ttu-id="2eea6-524">データ型</span><span class="sxs-lookup"><span data-stu-id="2eea6-524">Data type</span></span>|<span data-ttu-id="2eea6-525">説明</span><span class="sxs-lookup"><span data-stu-id="2eea6-525">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="2eea6-526">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2eea6-526">Unique identifier of a method.</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="2eea6-527">メソッドの ReJIT ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-527">The ReJIT ID of the method.</span></span>|
|`MethodExtent`|`win:UInt8`|<span data-ttu-id="2eea6-528">JIT コンパイルされるメソッドの範囲。</span><span class="sxs-lookup"><span data-stu-id="2eea6-528">The extent for the jitted method.</span></span>|
|`CountOfMapEntries`|`win:UInt8`|<span data-ttu-id="2eea6-529">マップ エントリの数</span><span class="sxs-lookup"><span data-stu-id="2eea6-529">Number of map entries</span></span>|
|`ILOffsets`|`win:UInt32`|<span data-ttu-id="2eea6-530">オフセット IL。</span><span class="sxs-lookup"><span data-stu-id="2eea6-530">The IL offset.</span></span>|
|`NativeOffsets`|`win:UInt32`|<span data-ttu-id="2eea6-531">ネイティブ コード オフセット。</span><span class="sxs-lookup"><span data-stu-id="2eea6-531">The native code offset.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2eea6-532">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2eea6-532">Unique ID for the instance of CoreCLR.</span></span>|

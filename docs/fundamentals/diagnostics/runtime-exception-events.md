---
title: 例外ランタイム イベント
description: 例外と例外処理に固有の診断情報を収集する .NET ランタイム イベントを確認します。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594103"
---
# <a name="net-runtime-exception-events"></a><span data-ttu-id="bc446-103">.NET ランタイム例外イベント</span><span class="sxs-lookup"><span data-stu-id="bc446-103">.NET runtime exception events</span></span>

<span data-ttu-id="bc446-104">これらのランタイム イベントは、スローされる例外に関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="bc446-104">These runtime events capture information about exceptions that are thrown.</span></span> <span data-ttu-id="bc446-105">診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc446-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="exceptionthrown_v1-event"></a><span data-ttu-id="bc446-106">ExceptionThrown_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="bc446-106">ExceptionThrown_V1 event</span></span>

|<span data-ttu-id="bc446-107">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="bc446-107">Keyword for raising the event</span></span>|<span data-ttu-id="bc446-108">Level</span><span class="sxs-lookup"><span data-stu-id="bc446-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="bc446-109">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="bc446-109">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="bc446-110">エラー (1)</span><span class="sxs-lookup"><span data-stu-id="bc446-110">Error (1)</span></span>|

 <span data-ttu-id="bc446-111">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="bc446-111">The following table shows event information.</span></span>

|<span data-ttu-id="bc446-112">Event</span><span class="sxs-lookup"><span data-stu-id="bc446-112">Event</span></span>|<span data-ttu-id="bc446-113">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bc446-113">Event ID</span></span>|<span data-ttu-id="bc446-114">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="bc446-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|<span data-ttu-id="bc446-115">80</span><span class="sxs-lookup"><span data-stu-id="bc446-115">80</span></span>|<span data-ttu-id="bc446-116">マネージド例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bc446-116">A managed exception is thrown.</span></span>|

|<span data-ttu-id="bc446-117">フィールド名</span><span class="sxs-lookup"><span data-stu-id="bc446-117">Field name</span></span>|<span data-ttu-id="bc446-118">データ型</span><span class="sxs-lookup"><span data-stu-id="bc446-118">Data type</span></span>|<span data-ttu-id="bc446-119">説明</span><span class="sxs-lookup"><span data-stu-id="bc446-119">Description</span></span>|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|<span data-ttu-id="bc446-120">例外の種類 (`System.NullReferenceException` など)。</span><span class="sxs-lookup"><span data-stu-id="bc446-120">Type of the exception; for example, `System.NullReferenceException`.</span></span>|
|`ExceptionMessage`|`win:UnicodeString`|<span data-ttu-id="bc446-121">実際の例外メッセージ。</span><span class="sxs-lookup"><span data-stu-id="bc446-121">Actual exception message.</span></span>|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="bc446-122">例外が発生した命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="bc446-122">Instruction pointer where exception occurred.</span></span>|
|`ExceptionHR`|`win:UInt32`|<span data-ttu-id="bc446-123">例外 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。</span><span class="sxs-lookup"><span data-stu-id="bc446-123">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|
|`ExceptionFlags`|`win:UInt16`|<span data-ttu-id="bc446-124">`0x01`: HasInnerException。</span><span class="sxs-lookup"><span data-stu-id="bc446-124">`0x01`: HasInnerException.</span></span><br /><br /> <span data-ttu-id="bc446-125">`0x02`: IsNestedException。</span><span class="sxs-lookup"><span data-stu-id="bc446-125">`0x02`: IsNestedException.</span></span><br /><br /> <span data-ttu-id="bc446-126">`0x04`: IsRethrownException。</span><span class="sxs-lookup"><span data-stu-id="bc446-126">`0x04`: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="bc446-127">`0x08`: IsCorruptedStateException (プロセスの状態が破損していることを示す。「[破損状態例外を処理する](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="bc446-127">`0x08`: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="bc446-128">`0x10`: IsCLSCompliant (<xref:System.Exception> から派生した例外は CLS 準拠で、それ以外は CLS 非準拠)。</span><span class="sxs-lookup"><span data-stu-id="bc446-128">`0x10`: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="bc446-129">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="bc446-129">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstart-event"></a><span data-ttu-id="bc446-130">ExceptionCatchStart イベント</span><span class="sxs-lookup"><span data-stu-id="bc446-130">ExceptionCatchStart event</span></span>

<span data-ttu-id="bc446-131">このイベントは、マネージ例外の catch ハンドラーが開始したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc446-131">This event is emitted when a managed exception catch handler begins.</span></span>

|<span data-ttu-id="bc446-132">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="bc446-132">Keyword for raising the event</span></span>|<span data-ttu-id="bc446-133">Level</span><span class="sxs-lookup"><span data-stu-id="bc446-133">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="bc446-134">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="bc446-134">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="bc446-135">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="bc446-135">Informational (4)</span></span>|

 <span data-ttu-id="bc446-136">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="bc446-136">The following table shows event information.</span></span>

|<span data-ttu-id="bc446-137">Event</span><span class="sxs-lookup"><span data-stu-id="bc446-137">Event</span></span>|<span data-ttu-id="bc446-138">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bc446-138">Event ID</span></span>|<span data-ttu-id="bc446-139">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="bc446-139">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|<span data-ttu-id="bc446-140">250</span><span class="sxs-lookup"><span data-stu-id="bc446-140">250</span></span>|<span data-ttu-id="bc446-141">マネージ例外は、ランタイムによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="bc446-141">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="bc446-142">フィールド名</span><span class="sxs-lookup"><span data-stu-id="bc446-142">Field name</span></span>|<span data-ttu-id="bc446-143">データ型</span><span class="sxs-lookup"><span data-stu-id="bc446-143">Data type</span></span>|<span data-ttu-id="bc446-144">説明</span><span class="sxs-lookup"><span data-stu-id="bc446-144">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="bc446-145">例外が発生した命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="bc446-145">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="bc446-146">例外が発生したメソッドのメソッド記述子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="bc446-146">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="bc446-147">例外が発生したメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="bc446-147">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="bc446-148">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="bc446-148">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstop-event"></a><span data-ttu-id="bc446-149">ExceptionCatchStop イベント</span><span class="sxs-lookup"><span data-stu-id="bc446-149">ExceptionCatchStop event</span></span>

<span data-ttu-id="bc446-150">このイベントは、マネージ例外の catch ハンドラーが終了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc446-150">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="bc446-151">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="bc446-151">Keyword for raising the event</span></span>|<span data-ttu-id="bc446-152">Level</span><span class="sxs-lookup"><span data-stu-id="bc446-152">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="bc446-153">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="bc446-153">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="bc446-154">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="bc446-154">Informational (4)</span></span>|

 <span data-ttu-id="bc446-155">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="bc446-155">The following table shows event information.</span></span>

|<span data-ttu-id="bc446-156">Event</span><span class="sxs-lookup"><span data-stu-id="bc446-156">Event</span></span>|<span data-ttu-id="bc446-157">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bc446-157">Event ID</span></span>|<span data-ttu-id="bc446-158">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="bc446-158">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|<span data-ttu-id="bc446-159">251</span><span class="sxs-lookup"><span data-stu-id="bc446-159">251</span></span>|<span data-ttu-id="bc446-160">マネージ例外の catch ハンドラーが完了したとき。</span><span class="sxs-lookup"><span data-stu-id="bc446-160">A managed exception catch handler is done.</span></span>|

## <a name="exceptionfinallystart-event"></a><span data-ttu-id="bc446-161">ExceptionFinallyStart イベント</span><span class="sxs-lookup"><span data-stu-id="bc446-161">ExceptionFinallyStart event</span></span>

<span data-ttu-id="bc446-162">このイベントは、マネージ例外の finally ハンドラーが開始したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc446-162">This event is emitted when a managed exception finally handler begins.</span></span>

|<span data-ttu-id="bc446-163">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="bc446-163">Keyword for raising the event</span></span>|<span data-ttu-id="bc446-164">Level</span><span class="sxs-lookup"><span data-stu-id="bc446-164">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="bc446-165">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="bc446-165">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="bc446-166">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="bc446-166">Informational (4)</span></span>|

 <span data-ttu-id="bc446-167">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="bc446-167">The following table shows event information.</span></span>

|<span data-ttu-id="bc446-168">Event</span><span class="sxs-lookup"><span data-stu-id="bc446-168">Event</span></span>|<span data-ttu-id="bc446-169">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bc446-169">Event ID</span></span>|<span data-ttu-id="bc446-170">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="bc446-170">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|<span data-ttu-id="bc446-171">252</span><span class="sxs-lookup"><span data-stu-id="bc446-171">252</span></span>|<span data-ttu-id="bc446-172">マネージ例外は、ランタイムによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="bc446-172">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="bc446-173">フィールド名</span><span class="sxs-lookup"><span data-stu-id="bc446-173">Field name</span></span>|<span data-ttu-id="bc446-174">データ型</span><span class="sxs-lookup"><span data-stu-id="bc446-174">Data type</span></span>|<span data-ttu-id="bc446-175">説明</span><span class="sxs-lookup"><span data-stu-id="bc446-175">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="bc446-176">例外が発生した命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="bc446-176">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="bc446-177">例外が発生したメソッドのメソッド記述子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="bc446-177">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="bc446-178">例外が発生したメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="bc446-178">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="bc446-179">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="bc446-179">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptionfinallystop-event"></a><span data-ttu-id="bc446-180">ExceptionFinallyStop イベント</span><span class="sxs-lookup"><span data-stu-id="bc446-180">ExceptionFinallyStop event</span></span>

<span data-ttu-id="bc446-181">このイベントは、マネージ例外の catch ハンドラーが終了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc446-181">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="bc446-182">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="bc446-182">Keyword for raising the event</span></span>|<span data-ttu-id="bc446-183">Level</span><span class="sxs-lookup"><span data-stu-id="bc446-183">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="bc446-184">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="bc446-184">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="bc446-185">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="bc446-185">Informational (4)</span></span>|

 <span data-ttu-id="bc446-186">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="bc446-186">The following table shows event information.</span></span>

|<span data-ttu-id="bc446-187">Event</span><span class="sxs-lookup"><span data-stu-id="bc446-187">Event</span></span>|<span data-ttu-id="bc446-188">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bc446-188">Event ID</span></span>|<span data-ttu-id="bc446-189">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="bc446-189">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|<span data-ttu-id="bc446-190">253</span><span class="sxs-lookup"><span data-stu-id="bc446-190">253</span></span>|<span data-ttu-id="bc446-191">マネージ例外の finally ハンドラーが完了したとき。</span><span class="sxs-lookup"><span data-stu-id="bc446-191">A managed exception finally handler is done.</span></span>|

## <a name="exceptionfilterstart-event"></a><span data-ttu-id="bc446-192">ExceptionFilterStart イベント</span><span class="sxs-lookup"><span data-stu-id="bc446-192">ExceptionFilterStart event</span></span>

<span data-ttu-id="bc446-193">このイベントは、マネージ例外のフィルター処理が開始したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc446-193">This event is emitted when a managed exception filtering begins.</span></span>

|<span data-ttu-id="bc446-194">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="bc446-194">Keyword for raising the event</span></span>|<span data-ttu-id="bc446-195">Level</span><span class="sxs-lookup"><span data-stu-id="bc446-195">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="bc446-196">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="bc446-196">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="bc446-197">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="bc446-197">Informational (4)</span></span>|

 <span data-ttu-id="bc446-198">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="bc446-198">The following table shows event information.</span></span>

|<span data-ttu-id="bc446-199">Event</span><span class="sxs-lookup"><span data-stu-id="bc446-199">Event</span></span>|<span data-ttu-id="bc446-200">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bc446-200">Event ID</span></span>|<span data-ttu-id="bc446-201">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="bc446-201">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|<span data-ttu-id="bc446-202">254</span><span class="sxs-lookup"><span data-stu-id="bc446-202">254</span></span>|<span data-ttu-id="bc446-203">マネージ例外のフィルター処理が開始したとき。</span><span class="sxs-lookup"><span data-stu-id="bc446-203">A managed exception filtering begins.</span></span>|

|<span data-ttu-id="bc446-204">フィールド名</span><span class="sxs-lookup"><span data-stu-id="bc446-204">Field name</span></span>|<span data-ttu-id="bc446-205">データ型</span><span class="sxs-lookup"><span data-stu-id="bc446-205">Data type</span></span>|<span data-ttu-id="bc446-206">説明</span><span class="sxs-lookup"><span data-stu-id="bc446-206">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="bc446-207">例外が発生した命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="bc446-207">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="bc446-208">例外が発生したメソッドのメソッド記述子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="bc446-208">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="bc446-209">例外が発生したメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="bc446-209">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="bc446-210">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="bc446-210">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="exceptionfilterstop-event"></a><span data-ttu-id="bc446-211">ExceptionFilterStop イベント</span><span class="sxs-lookup"><span data-stu-id="bc446-211">ExceptionFilterStop event</span></span>

<span data-ttu-id="bc446-212">このイベントは、マネージ例外のフィルター処理が終了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc446-212">This event is emitted when a managed exception filtering ends.</span></span>

|<span data-ttu-id="bc446-213">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="bc446-213">Keyword for raising the event</span></span>|<span data-ttu-id="bc446-214">Level</span><span class="sxs-lookup"><span data-stu-id="bc446-214">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="bc446-215">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="bc446-215">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="bc446-216">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="bc446-216">Informational (4)</span></span>|

 <span data-ttu-id="bc446-217">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="bc446-217">The following table shows event information.</span></span>

|<span data-ttu-id="bc446-218">Event</span><span class="sxs-lookup"><span data-stu-id="bc446-218">Event</span></span>|<span data-ttu-id="bc446-219">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bc446-219">Event ID</span></span>|<span data-ttu-id="bc446-220">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="bc446-220">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|<span data-ttu-id="bc446-221">255</span><span class="sxs-lookup"><span data-stu-id="bc446-221">255</span></span>|<span data-ttu-id="bc446-222">マネージ例外のフィルター処理が終了したとき。</span><span class="sxs-lookup"><span data-stu-id="bc446-222">A managed exception filtering ends.</span></span>|

## <a name="exceptionthrownstop-event"></a><span data-ttu-id="bc446-223">ExceptionThrownStop イベント</span><span class="sxs-lookup"><span data-stu-id="bc446-223">ExceptionThrownStop event</span></span>

<span data-ttu-id="bc446-224">このイベントは、スローされたマネージ例外の処理がランタイムによって完了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc446-224">This event is emitted when the runtime is done handling a managed exception that was thrown.</span></span>

|<span data-ttu-id="bc446-225">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="bc446-225">Keyword for raising the event</span></span>|<span data-ttu-id="bc446-226">Level</span><span class="sxs-lookup"><span data-stu-id="bc446-226">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="bc446-227">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="bc446-227">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="bc446-228">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="bc446-228">Informational (4)</span></span>|
  
 <span data-ttu-id="bc446-229">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="bc446-229">The following table shows event information.</span></span>

|<span data-ttu-id="bc446-230">Event</span><span class="sxs-lookup"><span data-stu-id="bc446-230">Event</span></span>|<span data-ttu-id="bc446-231">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bc446-231">Event ID</span></span>|<span data-ttu-id="bc446-232">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="bc446-232">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|<span data-ttu-id="bc446-233">256</span><span class="sxs-lookup"><span data-stu-id="bc446-233">256</span></span>|<span data-ttu-id="bc446-234">マネージ例外のフィルター処理が終了したとき。</span><span class="sxs-lookup"><span data-stu-id="bc446-234">A managed exception filtering ends.</span></span>|

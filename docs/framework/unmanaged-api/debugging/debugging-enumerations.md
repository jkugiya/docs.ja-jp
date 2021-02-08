---
description: 詳細については、「列挙型のデバッグ」をご覧ください。
title: 列挙体のデバッグ
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 4a1d2fc9061fec7f5384418e4893c357f5d340ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801424"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="fdb97-103">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="fdb97-103">Debugging Enumerations</span></span>

<span data-ttu-id="fdb97-104">このセクションでは、デバッグ API が使用するアンマネージ列挙体について説明します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-104">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fdb97-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fdb97-105">In This Section</span></span>  

 [<span data-ttu-id="fdb97-106">CLR_DEBUGGING_PROCESS_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="fdb97-106">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="fdb97-107">[ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md)メソッドによって使用される値を提供します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-107">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="fdb97-108">CLRDataEnumMemoryFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-108">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="fdb97-109">[ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md)メソッドへの呼び出しに含まれるメモリ領域を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-109">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="fdb97-110">COR_PUB_ENUMPROCESS 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-110">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="fdb97-111">列挙するプロセスの型を識別します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-111">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="fdb97-112">CorDebugBlockingReason 列挙体</span><span class="sxs-lookup"><span data-stu-id="fdb97-112">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="fdb97-113">指定されたオブジェクト上でスレッドがブロックされる理由を指定します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-113">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="fdb97-114">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="fdb97-114">CorDebugChainReason</span></span>  
 <span data-ttu-id="fdb97-115">呼び出しチェーンが開始する理由を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-115">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="fdb97-116">CorDebugCodeInvokeKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="fdb97-116">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="fdb97-117">エクスポートされた関数がマネージド コードを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-117">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="fdb97-118">CorDebugCodeInvokePurpose 列挙体</span><span class="sxs-lookup"><span data-stu-id="fdb97-118">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="fdb97-119">エクスポートされた関数がマネージド コードを呼び出す理由を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-119">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="fdb97-120">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="fdb97-120">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="fdb97-121">[ICorDebug:: CreateProcess](icordebug-createprocess-method.md)メソッドの呼び出しで使用できる追加のデバッグオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-121">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="fdb97-122">CorDebugDebugEventKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="fdb97-122">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="fdb97-123">[DecodeEvent](icordebugprocess6-decodeevent-method.md)メソッドによって情報がデコードされるイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-123">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="fdb97-124">CorDebugDecodeEventFlagsWindows 列挙体</span><span class="sxs-lookup"><span data-stu-id="fdb97-124">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="fdb97-125">Windows プラットフォームのデバッグ イベントに関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-125">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="fdb97-126">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="fdb97-126">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="fdb97-127">[ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)イベントから作成されたコールバックの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-127">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="fdb97-128">CorDebugExceptionFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-128">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="fdb97-129">例外に関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-129">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="fdb97-130">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="fdb97-130">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="fdb97-131">アンワインド フェーズ中にコールバックによって通知されるイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-131">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="fdb97-132">CorDebugGCType 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-132">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="fdb97-133">ガベージ コレクターがワークステーションまたはサーバーのどちらで実行されているかを示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-133">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="fdb97-134">CorDebugGenerationTypes 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-134">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="fdb97-135">マネージド ヒープ上のメモリ領域の生成を指定します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-135">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="fdb97-136">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="fdb97-136">CorDebugHandleType</span></span>  
 <span data-ttu-id="fdb97-137">ハンドル型を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-137">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="fdb97-138">CorDebugIlToNativeMappingTypes 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-138">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="fdb97-139">ネイティブ命令の特定の範囲が特別なコード領域に対応するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-139">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="fdb97-140">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="fdb97-140">CorDebugIntercept</span></span>  
 <span data-ttu-id="fdb97-141">ステップ インできるコードの型を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-141">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="fdb97-142">CorDebugInterfaceVersion 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-142">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="fdb97-143">.NET Framework のバージョン、またはインターフェイスが導入された .NET Framework のバージョンのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-143">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="fdb97-144">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="fdb97-144">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="fdb97-145">スタック フレームの型を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-145">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="fdb97-146">CorDebugJITCompilerFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-146">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="fdb97-147">マネージド Just-In-Time (JIT) コンパイラの動作に影響を与える値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fdb97-147">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="fdb97-148">CorDebugJITCompilerFlagsDeprecated 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-148">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="fdb97-149">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="fdb97-149">Obsolete.</span></span> <span data-ttu-id="fdb97-150">代わりに、 `CORDEBUG_JIT_DEFAULT` [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列挙体のメンバーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="fdb97-150">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="fdb97-151">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="fdb97-151">CorDebugMappingResult</span></span>  
 <span data-ttu-id="fdb97-152">命令ポインター (IP) の値が得られた方法の詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-152">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="fdb97-153">CorDebugMDAFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-153">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="fdb97-154">マネージド デバッグ アシスタント (MDA) が生成されるスレッドのステータスを指定します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-154">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="fdb97-155">CorDebugNGenPolicy 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-155">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="fdb97-156">デバッガーがネイティブ イメージ キャッシュからネイティブ (NGen) イメージを読み込むかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-156">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="fdb97-157">CorDebugPlatform 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-157">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="fdb97-158">は [、のターゲットプラットフォームの値](icordebugdatatarget-getplatform-method.md) を提供しています。</span><span class="sxs-lookup"><span data-stu-id="fdb97-158">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="fdb97-159">CorDebugRecordFormat 列挙体</span><span class="sxs-lookup"><span data-stu-id="fdb97-159">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="fdb97-160">ネイティブ例外デバッグ イベントに関する情報を格納するバイト配列内のデータの形式を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-160">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="fdb97-161">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="fdb97-161">CorDebugRegister</span></span>  
 <span data-ttu-id="fdb97-162">指定されたプロセッサ アーキテクチャに関連付けられたレジスタを指定します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-162">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="fdb97-163">CorDebugSetContextFlag 列挙体</span><span class="sxs-lookup"><span data-stu-id="fdb97-163">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="fdb97-164">スタック上のアクティブ (またはリーフ) フレーム上からのコンテキストなのか、別のフレームからのアンワインドにより計算されたコンテキストなのかを示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-164">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="fdb97-165">CorDebugStateChange 列挙体</span><span class="sxs-lookup"><span data-stu-id="fdb97-165">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="fdb97-166">プロセスへの変更に基づいて破棄が必要となった、キャッシュされたデータの量を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-166">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="fdb97-167">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="fdb97-167">CorDebugStepReason</span></span>  
 <span data-ttu-id="fdb97-168">個々のステップの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-168">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="fdb97-169">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="fdb97-169">CorDebugThreadState</span></span>  
 <span data-ttu-id="fdb97-170">デバッグのスレッドの状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-170">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="fdb97-171">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="fdb97-171">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="fdb97-172">ステッパによるコード実行の停止をトリガーする可能性のあるマップ解除したコードの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-172">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="fdb97-173">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="fdb97-173">CorDebugUserState</span></span>  
 <span data-ttu-id="fdb97-174">スレッドのユーザーの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-174">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="fdb97-175">CorGCReferenceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-175">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="fdb97-176">ガベージ コレクトされる必要のあるオブジェクトのソースを識別します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-176">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="fdb97-177">ILCodeKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-177">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="fdb97-178">デバッガーがローカル変数またはプロファイラー ReJIT インストルメンテーションに追加されたコードにアクセスできるかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-178">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="fdb97-179">LoggingLevelEnum 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-179">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="fdb97-180">マネージド スレッドがイベントを記録する際にイベント ログに書き込まれる説明メッセージの重大度レベルを示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-180">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="fdb97-181">LogSwitchCallReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-181">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="fdb97-182">デバッグとトレースの切り替えで実行された操作を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-182">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="fdb97-183">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-183">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="fdb97-184">変数のネイティブな場所の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-184">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="fdb97-185">WriteableMetadataUpdateMode 列挙型</span><span class="sxs-lookup"><span data-stu-id="fdb97-185">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="fdb97-186">メモリ内のメタデータ更新をデバッガーに対して可視にするかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-186">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>

 <span data-ttu-id="fdb97-187">[ClrDataSourceType 列挙型](clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP 構造体によって使用される値を提供します。</span><span class="sxs-lookup"><span data-stu-id="fdb97-187">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="fdb97-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdb97-188">Related Sections</span></span>  

 [<span data-ttu-id="fdb97-189">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="fdb97-189">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="fdb97-190">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fdb97-190">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="fdb97-191">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="fdb97-191">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="fdb97-192">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="fdb97-192">Debugging Structures</span></span>](debugging-structures.md)

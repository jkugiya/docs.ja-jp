---
description: 詳細については、StackSnapshotCallback 関数
title: StackSnapshotCallback 関数
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
ms.openlocfilehash: a49588bc3277956acad612afd0fcab3fa7edffbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736857"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="0fd20-103">StackSnapshotCallback 関数</span><span class="sxs-lookup"><span data-stu-id="0fd20-103">StackSnapshotCallback Function</span></span>

<span data-ttu-id="0fd20-104">[ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md)メソッドによって開始されるスタックウォーク中に、各マネージフレームおよびスタック上のアンマネージフレームの各実行に関する情報をプロファイラーに提供します。</span><span class="sxs-lookup"><span data-stu-id="0fd20-104">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd20-105">構文</span><span class="sxs-lookup"><span data-stu-id="0fd20-105">Syntax</span></span>  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fd20-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0fd20-106">Parameters</span></span>  

 `funcId`  
 <span data-ttu-id="0fd20-107">からこの値が0の場合、このコールバックはアンマネージフレームの実行用です。それ以外の場合は、マネージ関数の識別子であり、このコールバックはマネージフレーム用です。</span><span class="sxs-lookup"><span data-stu-id="0fd20-107">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="0fd20-108">からフレーム内のネイティブコード命令ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="0fd20-108">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="0fd20-109">から `COR_PRF_FRAME_INFO` スタックフレームに関する情報を参照する値。</span><span class="sxs-lookup"><span data-stu-id="0fd20-109">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="0fd20-110">この値は、このコールバック中にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0fd20-110">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="0fd20-111">から `CONTEXT` パラメーターによって参照される構造体のサイズ `context` 。</span><span class="sxs-lookup"><span data-stu-id="0fd20-111">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="0fd20-112">から `CONTEXT` このフレームの CPU の状態を表す Win32 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0fd20-112">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="0fd20-113">`context`パラメーターは、COR_PRF_SNAPSHOT_CONTEXT フラグが渡された場合にのみ有効です `ICorProfilerInfo2::DoStackSnapshot` 。</span><span class="sxs-lookup"><span data-stu-id="0fd20-113">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="0fd20-114">からから直接渡されるクライアントデータへのポインター `ICorProfilerInfo2::DoStackSnapshot` 。</span><span class="sxs-lookup"><span data-stu-id="0fd20-114">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fd20-115">解説</span><span class="sxs-lookup"><span data-stu-id="0fd20-115">Remarks</span></span>  

 <span data-ttu-id="0fd20-116">関数は、 `StackSnapshotCallback` プロファイラーライターによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="0fd20-116">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="0fd20-117">で実行される作業の複雑さを制限する必要があり `StackSnapshotCallback` ます。</span><span class="sxs-lookup"><span data-stu-id="0fd20-117">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="0fd20-118">たとえば、を非同期方式で使用する場合、 `ICorProfilerInfo2::DoStackSnapshot` ターゲットスレッドはロックを保持している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0fd20-118">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="0fd20-119">内のコードで `StackSnapshotCallback` 同じロックが要求された場合、デッドロックが議論れる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0fd20-119">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="0fd20-120">メソッドは、 `ICorProfilerInfo2::DoStackSnapshot` マネージフレームごとに1回、 `StackSnapshotCallback` またはアンマネージフレームの実行ごとに1回関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0fd20-120">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="0fd20-121">`StackSnapshotCallback`アンマネージフレームの実行に対してが呼び出された場合、プロファイラーは、(パラメーターによって参照される) レジスタコンテキストを使用して、 `context` 独自のアンマネージスタックウォークを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0fd20-121">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="0fd20-122">この場合、Win32 `CONTEXT` 構造体は、アンマネージフレームの実行中に最後にプッシュされたフレームの CPU 状態を表します。</span><span class="sxs-lookup"><span data-stu-id="0fd20-122">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="0fd20-123">Win32 `CONTEXT` 構造体にはすべてのレジスタの値が含まれていますが、スタックポインターレジスタ、フレームポインターレジスタ、命令ポインターレジスタ、および不揮発性 (つまり保持されている) 整数レジスタの値のみに依存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fd20-123">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fd20-124">要件</span><span class="sxs-lookup"><span data-stu-id="0fd20-124">Requirements</span></span>  

 <span data-ttu-id="0fd20-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fd20-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fd20-126">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="0fd20-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0fd20-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fd20-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fd20-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fd20-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd20-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fd20-129">See also</span></span>

- [<span data-ttu-id="0fd20-130">DoStackSnapshot メソッド</span><span class="sxs-lookup"><span data-stu-id="0fd20-130">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="0fd20-131">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="0fd20-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)

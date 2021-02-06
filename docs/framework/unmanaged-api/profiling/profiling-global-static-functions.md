---
description: 詳細については、「グローバル静的関数のプロファイリング」を参照してください。
title: グローバル静的関数のプロファイル
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 86e4b6bda73b0783f5f95e4e7dbc24f1ccccb130
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646375"
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="137a5-103">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="137a5-103">Profiling Global Static Functions</span></span>

<span data-ttu-id="137a5-104">このセクションでは、プロファイリング API が使用するアンマネージ API 関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="137a5-104">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="137a5-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="137a5-105">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="137a5-106">.NET Framework version 1 プロファイリング関数</span><span class="sxs-lookup"><span data-stu-id="137a5-106">.NET Framework version 1 Profiling Functions</span></span>  

 [<span data-ttu-id="137a5-107">FunctionEnter 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-107">FunctionEnter Function</span></span>](functionenter-function.md)  
 <span data-ttu-id="137a5-108">コントロールが関数に渡されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="137a5-108">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="137a5-109">.NET Framework 2.0 では非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="137a5-109">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="137a5-110">FunctionLeave 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-110">FunctionLeave Function</span></span>](functionleave-function.md)  
 <span data-ttu-id="137a5-111">関数が呼び出し元に戻りようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="137a5-111">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="137a5-112">.NET Framework 2.0 では非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="137a5-112">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="137a5-113">FunctionTailcall 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-113">FunctionTailcall Function</span></span>](functiontailcall-function.md)  
 <span data-ttu-id="137a5-114">現在実行中の関数が別の関数の末尾呼び出しを実行しようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="137a5-114">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="137a5-115">.NET Framework 2.0 では非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="137a5-115">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="137a5-116">.NET Framework version 2 プロファイリング関数</span><span class="sxs-lookup"><span data-stu-id="137a5-116">.NET Framework version 2 Profiling Functions</span></span>  

 [<span data-ttu-id="137a5-117">FunctionIDMapper 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-117">FunctionIDMapper Function</span></span>](functionidmapper-function.md)  
 <span data-ttu-id="137a5-118">関数の特定の識別子が、その関数の [FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)、および [FunctionTailcall2](functiontailcall2-function.md) コールバックで使用される代替 ID に再マップされる可能性があることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="137a5-118">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="137a5-119">また、プロファイラーが、その関数のコールバックを受信するかどうかを示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="137a5-119">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="137a5-120">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-120">FunctionEnter2 Function</span></span>](functionenter2-function.md)  
 <span data-ttu-id="137a5-121">コントロールが関数に渡されていることをプロファイラーに通知し、スタックフレームと関数の引数に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="137a5-121">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="137a5-122">.NET Framework 4 では非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="137a5-122">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="137a5-123">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-123">FunctionLeave2 Function</span></span>](functionleave2-function.md)  
 <span data-ttu-id="137a5-124">関数が呼び出し元に戻り、スタックフレームおよび関数の戻り値に関する情報を提供することをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="137a5-124">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="137a5-125">.NET Framework 4 では非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="137a5-125">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="137a5-126">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-126">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)  
 <span data-ttu-id="137a5-127">現在実行中の関数が別の関数の末尾呼び出しを実行しようとしていることをプロファイラーに通知し、スタックフレームに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="137a5-127">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="137a5-128">.NET Framework 4 では非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="137a5-128">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="137a5-129">StackSnapshotCallback 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-129">StackSnapshotCallback Function</span></span>](stacksnapshotcallback-function.md)  
 <span data-ttu-id="137a5-130">[ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md)メソッドによって開始されるスタックウォーク中に、各マネージフレームおよびスタック上のアンマネージフレームの各実行に関する情報をプロファイラーに提供します。</span><span class="sxs-lookup"><span data-stu-id="137a5-130">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="137a5-131">.NET Framework version 4 プロファイリング関数</span><span class="sxs-lookup"><span data-stu-id="137a5-131">.NET Framework version 4 Profiling Functions</span></span>  

 [<span data-ttu-id="137a5-132">FunctionIDMapper2 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)  
 <span data-ttu-id="137a5-133">指定された関数の識別子が、その関数の [FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)、 [FunctionTailcall3](functiontailcall3-function.md)、または[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)、および [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) コールバックで使用される代替 ID に再マップされる可能性があることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="137a5-133">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="137a5-134">また、プロファイラーは、その関数のコールバックを受信するかどうかを示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="137a5-134">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="137a5-135">`FunctionIDMapper2`[Functionidmapper](functionidmapper-function.md)関数をパラメーターで拡張し `clientData` ます。プロファイラーは、ランタイムを明確に区別するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="137a5-135">`FunctionIDMapper2` extends the [FunctionIDMapper](functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="137a5-136">FunctionEnter3 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-136">FunctionEnter3 Function</span></span>](functionenter3-function.md)  
 <span data-ttu-id="137a5-137">コントロールが関数に渡されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="137a5-137">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="137a5-138">FunctionEnter3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-138">FunctionEnter3WithInfo Function</span></span>](functionenter3withinfo-function.md)  
 <span data-ttu-id="137a5-139">コントロールが関数に渡されていることをプロファイラーに通知し、スタックフレームと関数の引数を取得するために [ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) に渡すことができるハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="137a5-139">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="137a5-140">FunctionLeave3 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-140">FunctionLeave3 Function</span></span>](functionleave3-function.md)  
 <span data-ttu-id="137a5-141">関数から制御が返されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="137a5-141">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="137a5-142">FunctionLeave3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-142">FunctionLeave3WithInfo Function</span></span>](functionleave3withinfo-function.md)  
 <span data-ttu-id="137a5-143">関数から制御が返されていることをプロファイラーに通知し、スタックフレームと戻り値を取得するために [ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) に渡すことができるハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="137a5-143">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="137a5-144">FunctionTailcall3 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-144">FunctionTailcall3 Function</span></span>](functiontailcall3-function.md)  
 <span data-ttu-id="137a5-145">現在実行中の関数が別の関数の末尾呼び出しを実行しようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="137a5-145">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="137a5-146">FunctionTailcall3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="137a5-146">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)  
 <span data-ttu-id="137a5-147">現在実行中の関数が別の関数の末尾呼び出しを実行しようとしていることをプロファイラーに通知し、スタックフレームを取得するために [ICorProfilerInfo3:: GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) に渡すことができるハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="137a5-147">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="137a5-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="137a5-148">Related Sections</span></span>  

 [<span data-ttu-id="137a5-149">プロファイリングの概要</span><span class="sxs-lookup"><span data-stu-id="137a5-149">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="137a5-150">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="137a5-150">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="137a5-151">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="137a5-151">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="137a5-152">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="137a5-152">Profiling Structures</span></span>](profiling-structures.md)

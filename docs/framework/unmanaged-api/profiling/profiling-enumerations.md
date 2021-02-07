---
description: 詳細については、「列挙型のプロファイリング」をご覧ください。
title: 列挙体のプロファイリング
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: f202e70dd27654dd39740851549477d4a6bf77a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736753"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="1cf51-103">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="1cf51-103">Profiling Enumerations</span></span>

<span data-ttu-id="1cf51-104">このセクションでは、プロファイル API が使用するアンマネージ列挙について説明します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-104">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1cf51-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1cf51-105">In This Section</span></span>  

 [<span data-ttu-id="1cf51-106">COR_PRF_CLAUSE_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-106">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="1cf51-107">コードが入った、または出た例外句のタイプを示します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-107">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="1cf51-108">COR_PRF_CODEGEN_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="1cf51-108">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="1cf51-109">[ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md)メソッドで設定できるコード生成フラグを定義します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-109">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="1cf51-110">COR_PRF_FINALIZER_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-110">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="1cf51-111">オブジェクトのファイナライザーを記述します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-111">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="1cf51-112">COR_PRF_GC_GENERATION 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-112">COR_PRF_GC_GENERATION Enumeration</span></span>](cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="1cf51-113">ガベージ コレクションのジェネレーションを識別します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-113">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="1cf51-114">COR_PRF_GC_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-114">COR_PRF_GC_REASON Enumeration</span></span>](cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="1cf51-115">ガベージ コレクションが発生している理由を示します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-115">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="1cf51-116">COR_PRF_GC_ROOT_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-116">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="1cf51-117">ガベージ コレクターのルートのプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-117">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="1cf51-118">COR_PRF_GC_ROOT_KIND 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-118">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="1cf51-119">[ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md)コールバックによって公開されるガベージコレクターのルートの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-119">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="1cf51-120">COR_PRF_HIGH_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-120">COR_PRF_HIGH_MONITOR Enumeration</span></span>](cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="1cf51-121">プロファイラーが読み込み時に[ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)メソッドに対して指定できる、 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列挙に含まれるフラグだけでなく、フラグも提供します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-121">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="1cf51-122">COR_PRF_JIT_CACHE 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-122">COR_PRF_JIT_CACHE Enumeration</span></span>](cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="1cf51-123">キャッシュされている関数検索の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-123">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="1cf51-124">COR_PRF_MISC 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-124">COR_PRF_MISC Enumeration</span></span>](cor-prf-misc-enumeration.md)  
 <span data-ttu-id="1cf51-125">特殊な識別子を指定する定数値を含めます。</span><span class="sxs-lookup"><span data-stu-id="1cf51-125">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="1cf51-126">COR_PRF_MODULE_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="1cf51-126">COR_PRF_MODULE_FLAGS Enumeration</span></span>](cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="1cf51-127">モジュールのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-127">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="1cf51-128">COR_PRF_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-128">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="1cf51-129">プロファイラーがサブスクライブしようとする動作、機能、またはイベントの指定で使用する値を含めます。</span><span class="sxs-lookup"><span data-stu-id="1cf51-129">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="1cf51-130">COR_PRF_RUNTIME_TYPE 列挙体</span><span class="sxs-lookup"><span data-stu-id="1cf51-130">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="1cf51-131">共通言語ランタイムのバージョンを表す値を含めます。</span><span class="sxs-lookup"><span data-stu-id="1cf51-131">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="1cf51-132">COR_PRF_SNAPSHOT_INFO 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-132">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="1cf51-133">プロファイラーの `StackSnapshotCallback` 関数への各呼び出しにおいて、スタック スナップショットでどのくらいのデータが返されるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-133">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="1cf51-134">COR_PRF_STATIC_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-134">COR_PRF_STATIC_TYPE Enumeration</span></span>](cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="1cf51-135">フィールドが静的であるかどうかを示し、静的な場合は、フィールドに適用される静的なクオリティを示します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-135">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="1cf51-136">COR_PRF_SUSPEND_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-136">COR_PRF_SUSPEND_REASON Enumeration</span></span>](cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="1cf51-137">ランタイムが中断された理由を示します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-137">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="1cf51-138">COR_PRF_TRANSITION_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="1cf51-138">COR_PRF_TRANSITION_REASON Enumeration</span></span>](cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="1cf51-139">マネージド コードからアンマネージド コードへ、またはその逆の遷移の理由を示します。</span><span class="sxs-lookup"><span data-stu-id="1cf51-139">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1cf51-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cf51-140">Related Sections</span></span>  

 [<span data-ttu-id="1cf51-141">プロファイリングの概要</span><span class="sxs-lookup"><span data-stu-id="1cf51-141">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="1cf51-142">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1cf51-142">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="1cf51-143">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="1cf51-143">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="1cf51-144">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="1cf51-144">Profiling Structures</span></span>](profiling-structures.md)

---
description: '詳細情報: プロファイルインターフェイス'
title: プロファイリングのインターフェイス
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: d35931c0caad93116d7ea26d29020d84e48ebc29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798928"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="a6d6b-103">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-103">Profiling Interfaces</span></span>

<span data-ttu-id="a6d6b-104">ここでは、共通言語ランタイム (CLR) で実行中のプログラムに対してプロファイルを可能にするアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-104">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6d6b-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a6d6b-105">In This Section</span></span>  

 [<span data-ttu-id="a6d6b-106">ICLRProfiling インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-106">ICLRProfiling Interface</span></span>](iclrprofiling-interface.md)  
 <span data-ttu-id="a6d6b-107">[Attachprofiler](iclrprofiling-attachprofiler-method.md)メソッドを提供します。これにより、実行中のプロセスにプロファイラーをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-107">Provides the [AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="a6d6b-108">ICorProfilerAssemblyReferenceProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-108">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="a6d6b-109">プロファイラーが [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) コールバックに追加するアセンブリ参照を CLR に通知できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-109">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="a6d6b-110">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-110">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)  
 <span data-ttu-id="a6d6b-111">プロファイラーがサブスクライブしたイベントが発生したときにコード プロファイラーに通知するために、CLR が使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-111">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="a6d6b-112">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-112">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)  
 <span data-ttu-id="a6d6b-113">.NET Framework 2.0 以降でサポートされるコールバックによって、`ICorProfilerCallback` インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-113">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="a6d6b-114">ICorProfilerCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-114">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)  
 <span data-ttu-id="a6d6b-115">CLR がプロファイラーにアタッチとデタッチの状態情報を伝えるために使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-115">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="a6d6b-116">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-116">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)  
 <span data-ttu-id="a6d6b-117">プロファイラーと情報をやりとりするために CLR が使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-117">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="a6d6b-118">ICorProfilerCallback5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-118">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)  
 <span data-ttu-id="a6d6b-119">ガベージ コレクションのルートによって参照されるオブジェクトの遷移的なクロージャを識別するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-119">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="a6d6b-120">ICorProfilerCallback6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-120">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)  
 <span data-ttu-id="a6d6b-121">CLR が プロファイラーに対して、アセンブリがロード中であることを通知するために使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-121">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="a6d6b-122">ICorProfilerCallback7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-122">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)  
 <span data-ttu-id="a6d6b-123">メモリ内モジュールに関連付けられているシンボルストリームが更新されたことをプロファイラーに通知するために共通言語ランタイムが使用するコールバックメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-123">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="a6d6b-124">ICorProfilerCallback8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-124">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)  
<span data-ttu-id="a6d6b-125">動的メソッドの JIT コンパイルが開始および終了したことをプロファイラーに通知するために共通言語ランタイムが使用するコールバックメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-125">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="a6d6b-126">ICorProfilerCallback9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-126">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)  
<span data-ttu-id="a6d6b-127">動的メソッドがガベージコレクションされ、その後アンロードされることをプロファイラーに通知するために共通言語ランタイムが使用するコールバックメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-127">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="a6d6b-128">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-128">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="a6d6b-129">コード プロファイラーが CLR と通信できるようにするためのメソッドを提供します。これは特定のメソッドを再コンパイルするときに、JIT コンパイラーがどのようにしてコードを生成するかを制御するためのものです。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-129">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="a6d6b-130">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-130">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="a6d6b-131">CLR で関数のコレクションを順番に反復処理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-131">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="a6d6b-132">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-132">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)  
 <span data-ttu-id="a6d6b-133">コード プロファイラーが、イベントの監視および情報の要求を制御するために CLR との通信で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-133">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="a6d6b-134">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-134">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)  
 <span data-ttu-id="a6d6b-135">.NET Framework 2.0 以降でサポートされるメソッドによって、`ICorProfilerInfo` インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-135">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="a6d6b-136">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-136">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)  
 <span data-ttu-id="a6d6b-137">`ICorProfilerInfo2`.NET Framework 4 以降のバージョンでサポートされているメソッドを使用して、インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-137">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="a6d6b-138">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-138">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)  
 <span data-ttu-id="a6d6b-139">コード プロファイラーが、イベントの監視および情報の要求を制御するために CLR との通信で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-139">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="a6d6b-140">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-140">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)  
 <span data-ttu-id="a6d6b-141">コード プロファイラーが、イベントの監視を制御するために CLR との通信で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-141">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="a6d6b-142">ICorProfilerInfo6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-142">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)  
 <span data-ttu-id="a6d6b-143">特定の NGen モジュールに属し、特定のメソッドの本体にインライン化されているすべてのメソッドに列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-143">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="a6d6b-144">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-144">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)  
 <span data-ttu-id="a6d6b-145">新しく定義されたメタデータをモジュールに適用し、メモリ内シンボルストリームへのアクセスを提供するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-145">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="a6d6b-146">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-146">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="a6d6b-147">アプリケーションまたはプロファイラーによってロードされたモジュールのコレクションを順番に反復処理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-147">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="a6d6b-148">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-148">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="a6d6b-149">[Ngen.exe (ネイティブイメージジェネレーター)](../../tools/ngen-exe-native-image-generator.md)によって生成される固定されたオブジェクトのコレクションを順番に反復処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-149">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="a6d6b-150">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-150">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="a6d6b-151">CLR でスレッドのコレクションを順番に反復処理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-151">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="a6d6b-152">IMethodMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6d6b-152">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)  
 <span data-ttu-id="a6d6b-153">新しい Microsoft 中間言語 (MSIL) 関数の本体にメモリを割り当てるための [Alloc](imethodmalloc-alloc-method.md) メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6d6b-153">Provides the [Alloc](imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a6d6b-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6d6b-154">Related Sections</span></span>  

 [<span data-ttu-id="a6d6b-155">プロファイリングの概要</span><span class="sxs-lookup"><span data-stu-id="a6d6b-155">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="a6d6b-156">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="a6d6b-156">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="a6d6b-157">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="a6d6b-157">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="a6d6b-158">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="a6d6b-158">Profiling Structures</span></span>](profiling-structures.md)

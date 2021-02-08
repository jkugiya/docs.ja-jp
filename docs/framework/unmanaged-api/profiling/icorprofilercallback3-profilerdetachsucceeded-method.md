---
description: '詳細について: ICorProfilerCallback3::P rofilerDetachSucceeded メソッド'
title: ICorProfilerCallback3::ProfilerDetachSucceeded メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
ms.openlocfilehash: bc80b5bd5301bb5b0278534cfba6ac23e5968620
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788775"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="3da07-103">ICorProfilerCallback3::ProfilerDetachSucceeded メソッド</span><span class="sxs-lookup"><span data-stu-id="3da07-103">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>

<span data-ttu-id="3da07-104">共通言語ランタイム (CLR: Common Language Runtime) がプロファイラー DLL をアンロードしようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="3da07-104">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3da07-105">構文</span><span class="sxs-lookup"><span data-stu-id="3da07-105">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3da07-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="3da07-106">Return Value</span></span>  

 <span data-ttu-id="3da07-107">このコールバックからの戻り値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="3da07-107">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3da07-108">解説</span><span class="sxs-lookup"><span data-stu-id="3da07-108">Remarks</span></span>  

 <span data-ttu-id="3da07-109">`ProfilerDetachSucceeded` コールバックは、すべてのスレッドでプロファイラーのコードが終了した後に発行されます。</span><span class="sxs-lookup"><span data-stu-id="3da07-109">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="3da07-110">このメソッドが呼び出された場合、プロファイラーは、そのデストラクターに適さない最後の段階のタスク (その UI またはログ コンポーネントの通知など) を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da07-110">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="3da07-111">ただし、プロファイラーは、このコールバック中に CLR によって提供されるインターフェイス ( [ICorProfilerInfo](icorprofilerinfo-interface.md) やインターフェイスなど) で関数を呼び出すことはできません `IMetaData*` 。</span><span class="sxs-lookup"><span data-stu-id="3da07-111">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="3da07-112">CLR は Windows アプリケーション イベント ログに、デタッチ操作が成功したことを示すエントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3da07-112">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="3da07-113">プロファイラーがこのコールバックから戻ると、CLR はプロファイラー オブジェクトを解放し、プロファイラー DLL をアンロードします。</span><span class="sxs-lookup"><span data-stu-id="3da07-113">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="3da07-114">したがって、プロファイラーは、コールバックから戻った後にプロファイラー DLL 内での実行を発生させるアクションを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="3da07-114">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="3da07-115">たとえば、プロファイラーは、スレッドを作成することも、タイマー コールバックを登録することもできません。</span><span class="sxs-lookup"><span data-stu-id="3da07-115">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3da07-116">要件</span><span class="sxs-lookup"><span data-stu-id="3da07-116">Requirements</span></span>  

 <span data-ttu-id="3da07-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3da07-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3da07-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3da07-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3da07-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3da07-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3da07-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3da07-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da07-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="3da07-121">See also</span></span>

- [<span data-ttu-id="3da07-122">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3da07-122">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
- [<span data-ttu-id="3da07-123">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3da07-123">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="3da07-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3da07-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3da07-125">プロファイル</span><span class="sxs-lookup"><span data-stu-id="3da07-125">Profiling</span></span>](index.md)

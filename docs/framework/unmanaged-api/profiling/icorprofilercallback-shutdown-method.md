---
description: '詳細情報: ICorProfilerCallback:: Shutdown メソッド'
title: ICorProfilerCallback::Shutdown メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: 7afc274579f248ee190e379160f2709b5cb9881a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657321"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="2f068-103">ICorProfilerCallback::Shutdown メソッド</span><span class="sxs-lookup"><span data-stu-id="2f068-103">ICorProfilerCallback::Shutdown Method</span></span>

<span data-ttu-id="2f068-104">アプリケーションがシャットダウン中であることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2f068-104">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f068-105">構文</span><span class="sxs-lookup"><span data-stu-id="2f068-105">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2f068-106">解説</span><span class="sxs-lookup"><span data-stu-id="2f068-106">Remarks</span></span>  

 <span data-ttu-id="2f068-107">プロファイラーコードは、メソッドが呼び出された後に、 [ICorProfilerInfo](icorprofilerinfo-interface.md) インターフェイスのメソッドを安全に呼び出すことができません `Shutdown` 。</span><span class="sxs-lookup"><span data-stu-id="2f068-107">The profiler code cannot safely call methods of the [ICorProfilerInfo](icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="2f068-108">メソッドを呼び出す `ICorProfilerInfo` と、メソッドから制御が戻った後に、未定義の動作が発生し `Shutdown` ます。</span><span class="sxs-lookup"><span data-stu-id="2f068-108">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="2f068-109">シャットダウン後も、特定の不変イベントが発生する可能性があります。プロファイラーは、このようになるとすぐに制御を戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f068-109">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="2f068-110">メソッドは、 `Shutdown` プロファイリングされているマネージアプリケーションがマネージコードとして開始されている場合にのみ呼び出されます (つまり、プロセススタックの初期フレームが管理されます)。</span><span class="sxs-lookup"><span data-stu-id="2f068-110">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="2f068-111">アプリケーションがアンマネージコードとして起動され、後でマネージコードにジャンプし、その結果、共通言語ランタイム (CLR) のインスタンスを作成した場合、 `Shutdown` は呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="2f068-111">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="2f068-112">このような場合、プロファイラーは、DLL_PROCESS_DETACH 値を使用してリソースを解放し、 `DllMain` トレースをディスクにフラッシュするなどのデータのクリーンアップ処理を実行するルーチンをライブラリに組み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f068-112">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="2f068-113">一般に、プロファイラーは予期しないシャットダウンに対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f068-113">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="2f068-114">たとえば、Win32's `TerminateProcess` メソッド (Winbase. h で宣言) によってプロセスが停止される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2f068-114">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="2f068-115">それ以外の場合、CLR は、特定のマネージスレッド (バックグラウンドスレッド) を停止します。</span><span class="sxs-lookup"><span data-stu-id="2f068-115">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f068-116">要件</span><span class="sxs-lookup"><span data-stu-id="2f068-116">Requirements</span></span>  

 <span data-ttu-id="2f068-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f068-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f068-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f068-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f068-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f068-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f068-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f068-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f068-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f068-121">See also</span></span>

- [<span data-ttu-id="2f068-122">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f068-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2f068-123">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="2f068-123">Initialize Method</span></span>](icorprofilercallback-initialize-method.md)

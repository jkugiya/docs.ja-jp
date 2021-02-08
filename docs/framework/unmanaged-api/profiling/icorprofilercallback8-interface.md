---
description: 詳細については、「ICorProfilerCallback8 インターフェイス」を参照してください。
title: ICorProfilerCallback8 インターフェイス
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 8dd9b8eea82f38b7598d578bd718743af826070d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781676"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="caad8-103">ICorProfilerCallback8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="caad8-103">ICorProfilerCallback8 Interface</span></span>

<span data-ttu-id="caad8-104">[.NET Framework 4.7 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="caad8-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="caad8-105">動的メソッドの JIT コンパイルが開始および終了したことをプロファイラーに通知するために、共通言語ランタイムによって使用されるコールバックメソッドを提供する [ICorProfilerCallback7](icorprofilercallback7-interface.md) のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="caad8-105">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="caad8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="caad8-106">Methods</span></span>  
  
|<span data-ttu-id="caad8-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="caad8-107">Method</span></span>|<span data-ttu-id="caad8-108">説明</span><span class="sxs-lookup"><span data-stu-id="caad8-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="caad8-109">DynamicMethodJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="caad8-109">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="caad8-110">動的メソッドの JIT コンパイルが開始されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="caad8-110">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="caad8-111">DynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="caad8-111">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="caad8-112">動的メソッドの JIT コンパイルが終了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="caad8-112">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="caad8-113">要件</span><span class="sxs-lookup"><span data-stu-id="caad8-113">Requirements</span></span>  

 <span data-ttu-id="caad8-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caad8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caad8-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="caad8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="caad8-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="caad8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="caad8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="caad8-117">See also</span></span>

- [<span data-ttu-id="caad8-118">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="caad8-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="caad8-119">ICorProfilerCallback9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="caad8-119">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)

---
description: 詳細については、「ICorProfilerCallback9 インターフェイス」を参照してください。
title: ICorProfilerCallback9 インターフェイス
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4bfcaf6f8985909ef9142ef4d08535a19facd7e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781650"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="b70e3-103">ICorProfilerCallback9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b70e3-103">ICorProfilerCallback9 Interface</span></span>

<span data-ttu-id="b70e3-104">[.NET Framework 4.7.2 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="b70e3-104">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="b70e3-105">動的メソッドがガベージコレクションされ、その後アンロードされたことをプロファイラーに通知するために、共通言語ランタイムによって使用されるコールバックメソッドを提供する [ICorProfilerCallback8](icorprofilercallback8-interface.md) のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="b70e3-105">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b70e3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b70e3-106">Methods</span></span>  
  
|<span data-ttu-id="b70e3-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="b70e3-107">Method</span></span>|<span data-ttu-id="b70e3-108">説明</span><span class="sxs-lookup"><span data-stu-id="b70e3-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b70e3-109">DynamicMethodUnloaded メソッド</span><span class="sxs-lookup"><span data-stu-id="b70e3-109">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="b70e3-110">動的メソッドがガベージコレクションされ、その後アンロードされたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b70e3-110">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b70e3-111">要件</span><span class="sxs-lookup"><span data-stu-id="b70e3-111">Requirements</span></span>  

 <span data-ttu-id="b70e3-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b70e3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b70e3-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b70e3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="b70e3-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b70e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b70e3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b70e3-115">See also</span></span>

- [<span data-ttu-id="b70e3-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b70e3-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b70e3-117">ICorProfilerCallback8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b70e3-117">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="b70e3-118">ICorProfilerCallback8 DynamicMethodJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="b70e3-118">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="b70e3-119">ICorProfilerCallback8 DynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="b70e3-119">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)

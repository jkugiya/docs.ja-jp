---
description: 詳細については、「ICorProfilerCallback7 インターフェイス」を参照してください。
title: ICorProfilerCallback7 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
ms.openlocfilehash: 3db402db221fca4487939f9817b20ec0c5207fc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781741"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="5664a-103">ICorProfilerCallback7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5664a-103">ICorProfilerCallback7 Interface</span></span>

<span data-ttu-id="5664a-104">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="5664a-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="5664a-105">[ICorProfilerCallback6](icorprofilercallback6-interface.md) のサブクラスは、メモリ内のモジュールに関連付けられているシンボルのストリームが更新されたことをプロファイラーに通知するために、共通言語ランタイムが使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5664a-105">A subclass of [ICorProfilerCallback6](icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5664a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5664a-106">Methods</span></span>  
  
|<span data-ttu-id="5664a-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="5664a-107">Method</span></span>|<span data-ttu-id="5664a-108">説明</span><span class="sxs-lookup"><span data-stu-id="5664a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5664a-109">ModuleInMemorySymbolsUpdated メソッド</span><span class="sxs-lookup"><span data-stu-id="5664a-109">ModuleInMemorySymbolsUpdated Method</span></span>](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="5664a-110">メモリ内のモジュールに関連付けられているシンボルのストリームが更新されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5664a-110">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5664a-111">要件</span><span class="sxs-lookup"><span data-stu-id="5664a-111">Requirements</span></span>  

 <span data-ttu-id="5664a-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5664a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5664a-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5664a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5664a-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5664a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5664a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5664a-115">See also</span></span>

- [<span data-ttu-id="5664a-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5664a-116">Profiling Interfaces</span></span>](profiling-interfaces.md)

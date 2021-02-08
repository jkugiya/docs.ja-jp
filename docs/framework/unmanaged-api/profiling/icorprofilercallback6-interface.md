---
description: 詳細については、「ICorProfilerCallback6 インターフェイス」を参照してください。
title: ICorProfilerCallback6 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 12eaafff8bd9ab8d4d58eac8f2d62415531bc898
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781754"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="9407b-103">ICorProfilerCallback6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9407b-103">ICorProfilerCallback6 Interface</span></span>

<span data-ttu-id="9407b-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="9407b-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9407b-105">アセンブリが読み込まれていることをプロファイラーに通知するために共通言語ランタイムが使用するコールバックメソッドを提供する [ICorProfilerCallback5](icorprofilercallback5-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="9407b-105">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9407b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9407b-106">Methods</span></span>  
  
|<span data-ttu-id="9407b-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="9407b-107">Method</span></span>|<span data-ttu-id="9407b-108">説明</span><span class="sxs-lookup"><span data-stu-id="9407b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9407b-109">GetAssemblyReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="9407b-109">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="9407b-110">共通言語ランタイムがアセンブリ参照クロージャのウォークを実行するときに、アセンブリがごく初期のローディング状態であることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9407b-110">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9407b-111">解説</span><span class="sxs-lookup"><span data-stu-id="9407b-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9407b-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="9407b-112">Requirements</span></span>  

 <span data-ttu-id="9407b-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9407b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9407b-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9407b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9407b-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9407b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9407b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9407b-116">See also</span></span>

- [<span data-ttu-id="9407b-117">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9407b-117">Profiling Interfaces</span></span>](profiling-interfaces.md)

---
description: 詳細については、「ICorProfilerAssemblyReferenceProvider インターフェイス」を参照してください。
title: ICorProfilerAssemblyReferenceProvider インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: 0f16bad95dba46452ce5cc8ad1bbe6ca1bfeb7c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648351"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="d8657-103">ICorProfilerAssemblyReferenceProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8657-103">ICorProfilerAssemblyReferenceProvider Interface</span></span>

<span data-ttu-id="d8657-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="d8657-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d8657-105">プロファイラーが [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) コールバックに追加するアセンブリ参照の共通言語ランタイム (CLR) を通知できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d8657-105">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8657-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d8657-106">Methods</span></span>  
  
|<span data-ttu-id="d8657-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="d8657-107">Method</span></span>|<span data-ttu-id="d8657-108">説明</span><span class="sxs-lookup"><span data-stu-id="d8657-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8657-109">AddAssemblyReference メソッド</span><span class="sxs-lookup"><span data-stu-id="d8657-109">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="d8657-110">プロファイラーが [Moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md) コールバックに追加する予定のアセンブリ参照を CLR に通知します。</span><span class="sxs-lookup"><span data-stu-id="d8657-110">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8657-111">解説</span><span class="sxs-lookup"><span data-stu-id="d8657-111">Remarks</span></span>  

 <span data-ttu-id="d8657-112">CLR は、プロファイラーに `ICorProfilerAssemblyReferenceProvider` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) コールバックのインターフェイスオブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="d8657-112">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="d8657-113">これにより、プロファイラーは、後で [ICorProfilerCallback:: ModuleLoadFinished 終了](icorprofilercallback-moduleloadfinished-method.md)した後に追加することを計画しているアセンブリ参照を CLR に通知できます。</span><span class="sxs-lookup"><span data-stu-id="d8657-113">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="d8657-114">コールバック。</span><span class="sxs-lookup"><span data-stu-id="d8657-114">callback.</span></span> <span data-ttu-id="d8657-115">これにより、CLR のアセンブリ参照クロージャ ウォーカーの正確性とアセンブリが共有可能かどうかを判断するアルゴリズムが強化されます。</span><span class="sxs-lookup"><span data-stu-id="d8657-115">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="d8657-116">このインターフェイスは、このインターフェイスオブジェクトをプロファイラーに渡す [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) コールバックでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8657-116">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8657-117">要件</span><span class="sxs-lookup"><span data-stu-id="d8657-117">Requirements</span></span>  

 <span data-ttu-id="d8657-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8657-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8657-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8657-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8657-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8657-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8657-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8657-121">See also</span></span>

- [<span data-ttu-id="d8657-122">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8657-122">Profiling Interfaces</span></span>](profiling-interfaces.md)

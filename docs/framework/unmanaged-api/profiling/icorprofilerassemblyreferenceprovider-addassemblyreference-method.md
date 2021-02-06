---
description: '詳細情報: ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference メソッド'
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 343e76dd64329c88bf4b52e24d45a1e7c8b639bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648377"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="25af9-103">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference メソッド</span><span class="sxs-lookup"><span data-stu-id="25af9-103">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>

<span data-ttu-id="25af9-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="25af9-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="25af9-105">プロファイラーが [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) コールバックに追加することを計画しているアセンブリ参照の共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="25af9-105">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25af9-106">構文</span><span class="sxs-lookup"><span data-stu-id="25af9-106">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25af9-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="25af9-107">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="25af9-108">アセンブリ参照クロージャウォークを実行するときに考慮する必要があるアセンブリ参照に関する情報を CLR に提供する、 [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25af9-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="25af9-109">解説</span><span class="sxs-lookup"><span data-stu-id="25af9-109">Remarks</span></span>  

 <span data-ttu-id="25af9-110">プロファイラーは、 `wszAssemblyPath` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) コールバックの引数で指定されたアセンブリから参照するターゲットアセンブリごとに、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25af9-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="25af9-111">[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)インターフェイスオブジェクトは、引数のアセンブリパスと名前と共に、プロファイラーの[ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)コールバックに渡され `wszAssemblyPath` ます。</span><span class="sxs-lookup"><span data-stu-id="25af9-111">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25af9-112">要件</span><span class="sxs-lookup"><span data-stu-id="25af9-112">Requirements</span></span>  

 <span data-ttu-id="25af9-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25af9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25af9-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="25af9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25af9-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25af9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25af9-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25af9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25af9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="25af9-117">See also</span></span>

- [<span data-ttu-id="25af9-118">ICorProfilerAssemblyReferenceProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25af9-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="25af9-119">GetAssemblyReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="25af9-119">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="25af9-120">ModuleLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="25af9-120">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)

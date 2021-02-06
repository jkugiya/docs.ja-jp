---
description: '詳細について: ICorProfilerCallback:: AssemblyUnloadStarted メソッド'
title: ICorProfilerCallback::AssemblyUnloadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
ms.openlocfilehash: e9c72d481df7242f305b5efa6f747866984b31f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657835"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="88730-103">ICorProfilerCallback::AssemblyUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="88730-103">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>

<span data-ttu-id="88730-104">アセンブリがアンロードされていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="88730-104">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88730-105">構文</span><span class="sxs-lookup"><span data-stu-id="88730-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88730-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="88730-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="88730-107">\[in] は、アンロードされるアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="88730-107">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="88730-108">解説</span><span class="sxs-lookup"><span data-stu-id="88730-108">Remarks</span></span>  

 <span data-ttu-id="88730-109">`assemblyId`メソッドから制御が戻った後、の値は情報要求に対して無効です `AssemblyUnloadStarted` 。これは、このアセンブリに関する情報を取得する最後の機会です。</span><span class="sxs-lookup"><span data-stu-id="88730-109">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88730-110">要件</span><span class="sxs-lookup"><span data-stu-id="88730-110">Requirements</span></span>  

 <span data-ttu-id="88730-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88730-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88730-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="88730-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="88730-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88730-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88730-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88730-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88730-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="88730-115">See also</span></span>

- [<span data-ttu-id="88730-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="88730-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="88730-117">AssemblyUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="88730-117">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)

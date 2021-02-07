---
description: '詳細について: ICorProfilerCallback9::D ynamicMethodUnloaded メソッド'
title: ICorProfilerCallback9::D ynamicMethodUnloaded メソッド
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 243660d3159e3c8c1d052c08e9c7499e7065d301
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753329"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="9f25f-103">ICorProfilerCallback9::D ynamicMethodUnloaded メソッド</span><span class="sxs-lookup"><span data-stu-id="9f25f-103">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>

<span data-ttu-id="9f25f-104">[.NET Framework 4.7.2 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="9f25f-104">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="9f25f-105">動的メソッドがガベージコレクションされ、その後アンロードされるたびに、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9f25f-105">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f25f-106">構文</span><span class="sxs-lookup"><span data-stu-id="9f25f-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f25f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f25f-107">Parameters</span></span>  

<span data-ttu-id="9f25f-108">[入力] `functionId`</span><span class="sxs-lookup"><span data-stu-id="9f25f-108">[in] `functionId`</span></span>  
<span data-ttu-id="9f25f-109">ガベージコレクションおよびアンロードされたメモリ内の関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="9f25f-109">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f25f-110">要件</span><span class="sxs-lookup"><span data-stu-id="9f25f-110">Requirements</span></span>  

 <span data-ttu-id="9f25f-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f25f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f25f-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9f25f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9f25f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f25f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f25f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9f25f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f25f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f25f-115">See also</span></span>

- [<span data-ttu-id="9f25f-116">ICorProfilerCallback8 DynamicMethodJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="9f25f-116">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="9f25f-117">ICorProfilerCallback8 DynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="9f25f-117">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="9f25f-118">ICorProfilerCallback9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f25f-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="9f25f-119">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="9f25f-119">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)

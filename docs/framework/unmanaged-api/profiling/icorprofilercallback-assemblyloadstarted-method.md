---
description: '詳細については、次を参照してください: ICorProfilerCallback:: AssemblyLoadStarted メソッド'
title: ICorProfilerCallback::AssemblyLoadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
ms.openlocfilehash: f771008b9aed9322f0c5fd279fa9dfb3086755e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648015"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="38fcb-103">ICorProfilerCallback::AssemblyLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="38fcb-103">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>

<span data-ttu-id="38fcb-104">アセンブリが読み込まれていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="38fcb-104">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38fcb-105">構文</span><span class="sxs-lookup"><span data-stu-id="38fcb-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38fcb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38fcb-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="38fcb-107">\[in] は、読み込むアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="38fcb-107">\[in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="38fcb-108">解説</span><span class="sxs-lookup"><span data-stu-id="38fcb-108">Remarks</span></span>  

 <span data-ttu-id="38fcb-109">の値 `assemblyId` は、 [ICorProfilerCallback:: AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) メソッドが呼び出されるまで、情報要求に対して無効です。</span><span class="sxs-lookup"><span data-stu-id="38fcb-109">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38fcb-110">要件</span><span class="sxs-lookup"><span data-stu-id="38fcb-110">Requirements</span></span>  

 <span data-ttu-id="38fcb-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38fcb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38fcb-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38fcb-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38fcb-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38fcb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38fcb-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38fcb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38fcb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="38fcb-115">See also</span></span>

- [<span data-ttu-id="38fcb-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38fcb-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)

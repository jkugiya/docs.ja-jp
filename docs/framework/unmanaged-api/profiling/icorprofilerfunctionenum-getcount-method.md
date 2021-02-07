---
description: '詳細について: ICorProfilerFunctionEnum:: GetCount メソッド'
title: ICorProfilerFunctionEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
ms.openlocfilehash: a3eccfa31676636aff7379b4080bcb85a268df6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737624"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="d726d-103">ICorProfilerFunctionEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="d726d-103">ICorProfilerFunctionEnum::GetCount Method</span></span>

<span data-ttu-id="d726d-104">アプリケーションによって読み込まれたか、またはプロファイラーによって強制的に読み込まれた関数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="d726d-104">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d726d-105">構文</span><span class="sxs-lookup"><span data-stu-id="d726d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d726d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d726d-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="d726d-107">入出力読み込まれた関数の数。</span><span class="sxs-lookup"><span data-stu-id="d726d-107">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d726d-108">要件</span><span class="sxs-lookup"><span data-stu-id="d726d-108">Requirements</span></span>  

 <span data-ttu-id="d726d-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d726d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d726d-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d726d-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d726d-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d726d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d726d-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d726d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d726d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d726d-113">See also</span></span>

- [<span data-ttu-id="d726d-114">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d726d-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="d726d-115">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d726d-115">Profiling Interfaces</span></span>](profiling-interfaces.md)

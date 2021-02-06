---
description: '詳細について: ICorProfilerThreadEnum:: GetCount メソッド'
title: ICorProfilerThreadEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 5219dfc71b79be82f769ac7c8230beaf62c6f33e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646427"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="ab836-103">ICorProfilerThreadEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="ab836-103">ICorProfilerThreadEnum::GetCount Method</span></span>

<span data-ttu-id="ab836-104">アプリケーションで使用されるスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="ab836-104">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab836-105">構文</span><span class="sxs-lookup"><span data-stu-id="ab836-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab836-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ab836-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="ab836-107">入出力アプリケーションによって使用されるスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="ab836-107">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab836-108">要件</span><span class="sxs-lookup"><span data-stu-id="ab836-108">Requirements</span></span>  

 <span data-ttu-id="ab836-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab836-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab836-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab836-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab836-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab836-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab836-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab836-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab836-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab836-113">See also</span></span>

- [<span data-ttu-id="ab836-114">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab836-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="ab836-115">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab836-115">Profiling Interfaces</span></span>](profiling-interfaces.md)

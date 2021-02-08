---
description: '詳細について: ICorProfilerModuleEnum:: GetCount メソッド'
title: ICorProfilerModuleEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
ms.openlocfilehash: efdd812795002c25aaeb7634e7a4f4e4287553e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781390"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="f0aae-103">ICorProfilerModuleEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="f0aae-103">ICorProfilerModuleEnum::GetCount Method</span></span>

<span data-ttu-id="f0aae-104">アプリケーションによって読み込まれたマネージド モジュールの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="f0aae-104">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0aae-105">構文</span><span class="sxs-lookup"><span data-stu-id="f0aae-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0aae-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0aae-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="f0aae-107">入出力コレクション内のランタイムモジュールの数。</span><span class="sxs-lookup"><span data-stu-id="f0aae-107">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0aae-108">要件</span><span class="sxs-lookup"><span data-stu-id="f0aae-108">Requirements</span></span>  

 <span data-ttu-id="f0aae-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0aae-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0aae-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0aae-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0aae-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0aae-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0aae-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0aae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0aae-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0aae-113">See also</span></span>

- [<span data-ttu-id="f0aae-114">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f0aae-114">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="f0aae-115">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f0aae-115">Profiling Interfaces</span></span>](profiling-interfaces.md)

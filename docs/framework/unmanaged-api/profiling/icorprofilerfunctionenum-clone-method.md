---
description: '詳細情報: ICorProfilerFunctionEnum:: Clone メソッド'
title: ICorProfilerFunctionEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
ms.openlocfilehash: 6cadadd98f64a27de0cd4e7d264fe797d22c33a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737676"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="eb913-103">ICorProfilerFunctionEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="eb913-103">ICorProfilerFunctionEnum::Clone Method</span></span>

<span data-ttu-id="eb913-104">この [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) インターフェイスのコピーへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="eb913-104">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb913-105">構文</span><span class="sxs-lookup"><span data-stu-id="eb913-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb913-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb913-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="eb913-107">入出力インターフェイスポインターへのポインター。これにより、この [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) インターフェイスのコピーが参照されます。</span><span class="sxs-lookup"><span data-stu-id="eb913-107">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="eb913-108">列挙子のコピーは、この列挙子とは別に独自の列挙状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="eb913-108">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="eb913-109">ただし、コピーの初期カーソル位置は、この列挙子の現在のカーソル位置と同じです。</span><span class="sxs-lookup"><span data-stu-id="eb913-109">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb913-110">要件</span><span class="sxs-lookup"><span data-stu-id="eb913-110">Requirements</span></span>  

 <span data-ttu-id="eb913-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb913-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb913-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb913-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb913-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb913-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb913-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb913-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb913-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb913-115">See also</span></span>

- [<span data-ttu-id="eb913-116">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb913-116">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="eb913-117">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb913-117">Profiling Interfaces</span></span>](profiling-interfaces.md)

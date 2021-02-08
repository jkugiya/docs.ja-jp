---
description: '詳細情報: ICorProfilerObjectEnum:: Skip メソッド'
title: ICorProfilerObjectEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
ms.openlocfilehash: 8a2aa5dd2b905931b97fafa4db6709aab16aacc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781260"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="af73b-103">ICorProfilerObjectEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="af73b-103">ICorProfilerObjectEnum::Skip Method</span></span>

<span data-ttu-id="af73b-104">指定された数の要素がスキップされるように、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="af73b-104">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af73b-105">構文</span><span class="sxs-lookup"><span data-stu-id="af73b-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af73b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="af73b-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="af73b-107">からスキップする要素の数。</span><span class="sxs-lookup"><span data-stu-id="af73b-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af73b-108">解説</span><span class="sxs-lookup"><span data-stu-id="af73b-108">Remarks</span></span>  

 <span data-ttu-id="af73b-109">この列挙子のカーソルの新しい位置は、(現在位置) + `celt` です。</span><span class="sxs-lookup"><span data-stu-id="af73b-109">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af73b-110">要件</span><span class="sxs-lookup"><span data-stu-id="af73b-110">Requirements</span></span>  

 <span data-ttu-id="af73b-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af73b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af73b-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af73b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af73b-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af73b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af73b-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af73b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af73b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="af73b-115">See also</span></span>

- [<span data-ttu-id="af73b-116">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af73b-116">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)

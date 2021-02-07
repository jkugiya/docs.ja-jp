---
description: '詳細情報: ICorProfilerThreadEnum:: Skip メソッド'
title: ICorProfilerThreadEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: 1da191980364868ed4237fccaf7495d5417705cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736896"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="62218-103">ICorProfilerThreadEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="62218-103">ICorProfilerThreadEnum::Skip Method</span></span>

<span data-ttu-id="62218-104">指定した数の要素をスキップするため、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="62218-104">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62218-105">構文</span><span class="sxs-lookup"><span data-stu-id="62218-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62218-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62218-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="62218-107">からスキップする要素の数。</span><span class="sxs-lookup"><span data-stu-id="62218-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62218-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="62218-108">Return Value</span></span>  

 <span data-ttu-id="62218-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="62218-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="62218-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62218-110">HRESULT</span></span>|<span data-ttu-id="62218-111">説明</span><span class="sxs-lookup"><span data-stu-id="62218-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62218-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="62218-112">S_OK</span></span>|<span data-ttu-id="62218-113">`celt` 要素はスキップされました。</span><span class="sxs-lookup"><span data-stu-id="62218-113">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="62218-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="62218-114">S_FALSE</span></span>|<span data-ttu-id="62218-115">より小さい `celt` 要素がスキップされました。これは、要素がこれ以上存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="62218-115">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62218-116">解説</span><span class="sxs-lookup"><span data-stu-id="62218-116">Remarks</span></span>  

 <span data-ttu-id="62218-117">この列挙子のカーソルの新しい位置は、(現在位置) + `celt` です。</span><span class="sxs-lookup"><span data-stu-id="62218-117">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62218-118">要件</span><span class="sxs-lookup"><span data-stu-id="62218-118">Requirements</span></span>  

 <span data-ttu-id="62218-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62218-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62218-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62218-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62218-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62218-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62218-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62218-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62218-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="62218-123">See also</span></span>

- [<span data-ttu-id="62218-124">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62218-124">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="62218-125">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="62218-125">Profiling Interfaces</span></span>](profiling-interfaces.md)

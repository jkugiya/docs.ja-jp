---
description: '詳細情報: ICorProfilerFunctionEnum:: Skip メソッド'
title: ICorProfilerFunctionEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
ms.openlocfilehash: 6d176c51788135952127008f2f43545ead1e2369
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657061"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="63026-103">ICorProfilerFunctionEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="63026-103">ICorProfilerFunctionEnum::Skip Method</span></span>

<span data-ttu-id="63026-104">指定した数の要素がスキップされるように、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="63026-104">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63026-105">構文</span><span class="sxs-lookup"><span data-stu-id="63026-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63026-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="63026-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="63026-107">からスキップする要素の数。</span><span class="sxs-lookup"><span data-stu-id="63026-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63026-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="63026-108">Return Value</span></span>  

 <span data-ttu-id="63026-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="63026-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="63026-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63026-110">HRESULT</span></span>|<span data-ttu-id="63026-111">説明</span><span class="sxs-lookup"><span data-stu-id="63026-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63026-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="63026-112">S_OK</span></span>|<span data-ttu-id="63026-113">`celt` 要素はスキップされました。</span><span class="sxs-lookup"><span data-stu-id="63026-113">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="63026-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="63026-114">S_FALSE</span></span>|<span data-ttu-id="63026-115">より小さい `celt` 要素がスキップされました。これは、要素がこれ以上存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="63026-115">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63026-116">解説</span><span class="sxs-lookup"><span data-stu-id="63026-116">Remarks</span></span>  

 <span data-ttu-id="63026-117">この列挙子のカーソルの新しい位置は、(現在位置) + `celt` です。</span><span class="sxs-lookup"><span data-stu-id="63026-117">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63026-118">要件</span><span class="sxs-lookup"><span data-stu-id="63026-118">Requirements</span></span>  

 <span data-ttu-id="63026-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63026-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63026-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="63026-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63026-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63026-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63026-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63026-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63026-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="63026-123">See also</span></span>

- [<span data-ttu-id="63026-124">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63026-124">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="63026-125">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="63026-125">Profiling Interfaces</span></span>](profiling-interfaces.md)

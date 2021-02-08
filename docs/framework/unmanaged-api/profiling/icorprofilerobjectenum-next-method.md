---
description: '詳細情報: ICorProfilerObjectEnum:: Next メソッド'
title: ICorProfilerObjectEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type:
- apiref
ms.openlocfilehash: 7f61fa1d4e28043bf5eda95f67dde0d8e87d8c0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781416"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="f2872-103">ICorProfilerObjectEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="f2872-103">ICorProfilerObjectEnum::Next Method</span></span>

<span data-ttu-id="f2872-104">シーケンス内の列挙子の現在位置を開始位置として、オブジェクトのシーケンシャルコレクションから、指定された数の連続するオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="f2872-104">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2872-105">構文</span><span class="sxs-lookup"><span data-stu-id="f2872-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2872-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f2872-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="f2872-107">[in] 取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="f2872-107">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="f2872-108">入出力値の配列 `ObjectID` 。各値は取得されたオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="f2872-108">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f2872-109">[out] `objects` 配列で実際に返されるモジュールの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f2872-109">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2872-110">要件</span><span class="sxs-lookup"><span data-stu-id="f2872-110">Requirements</span></span>  

 <span data-ttu-id="f2872-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2872-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2872-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2872-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2872-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2872-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2872-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2872-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2872-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2872-115">See also</span></span>

- [<span data-ttu-id="f2872-116">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2872-116">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)

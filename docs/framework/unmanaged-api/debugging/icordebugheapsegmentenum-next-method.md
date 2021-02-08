---
description: '詳細情報: ICorDebugHeapSegmentEnum:: Next メソッド'
title: ICorDebugHeapSegmentEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 8d2ddfb4df82969fa9cf580ed8a7f903f9d6c260
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803677"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="3133e-103">ICorDebugHeapSegmentEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="3133e-103">ICorDebugHeapSegmentEnum::Next Method</span></span>

<span data-ttu-id="3133e-104">マネージヒープのメモリ領域に関する情報を格納している、指定した数の [COR_SEGMENT](cor-segment-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="3133e-104">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3133e-105">構文</span><span class="sxs-lookup"><span data-stu-id="3133e-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3133e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3133e-106">Parameters</span></span>  

 <span data-ttu-id="3133e-107">celt</span><span class="sxs-lookup"><span data-stu-id="3133e-107">celt</span></span>  
 <span data-ttu-id="3133e-108">から取得するセグメントの数。</span><span class="sxs-lookup"><span data-stu-id="3133e-108">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="3133e-109">セグメント</span><span class="sxs-lookup"><span data-stu-id="3133e-109">segments</span></span>  
 <span data-ttu-id="3133e-110">入出力ポインターの配列。各ポインターは、マネージヒープ内のメモリ領域に関する情報を提供する [COR_SEGMENT](cor-segment-structure.md) オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="3133e-110">[out] An array of pointers, each of which points to a [COR_SEGMENT](cor-segment-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="3133e-111">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="3133e-111">pceltFetched</span></span>  
 <span data-ttu-id="3133e-112">入出力実際にで返される [COR_SEGMENT](cor-segment-structure.md) オブジェクトの数へのポインター `segments` 。</span><span class="sxs-lookup"><span data-stu-id="3133e-112">[out] A pointer to the number of [COR_SEGMENT](cor-segment-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="3133e-113">`celt` が 1 の場合、この値は`null` になることがあります。</span><span class="sxs-lookup"><span data-stu-id="3133e-113">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3133e-114">解説</span><span class="sxs-lookup"><span data-stu-id="3133e-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3133e-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="3133e-115">Requirements</span></span>  

 <span data-ttu-id="3133e-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3133e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3133e-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3133e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3133e-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3133e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3133e-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3133e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3133e-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3133e-120">See also</span></span>

- [<span data-ttu-id="3133e-121">ICorDebugHeapSegmentEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3133e-121">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="3133e-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3133e-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

---
description: 詳細については、「ICorDebugHeapSegmentEnum インターフェイス」を参照してください。
title: ICorDebugHeapSegmentEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: 614bae0ea5e3eb7816fdeec23a0dc7aa6e44801d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660883"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="6d30d-103">ICorDebugHeapSegmentEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d30d-103">ICorDebugHeapSegmentEnum Interface</span></span>

<span data-ttu-id="6d30d-104">マネージド ヒープのメモリ領域の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="6d30d-104">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="6d30d-105">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="6d30d-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d30d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="6d30d-106">Methods</span></span>  
  
|<span data-ttu-id="6d30d-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="6d30d-107">Method</span></span>|<span data-ttu-id="6d30d-108">説明</span><span class="sxs-lookup"><span data-stu-id="6d30d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d30d-109">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="6d30d-109">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="6d30d-110">マネージヒープの領域に関する情報を格納している、指定した数の [COR_SEGMENT](cor-segment-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6d30d-110">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d30d-111">解説</span><span class="sxs-lookup"><span data-stu-id="6d30d-111">Remarks</span></span>  

 <span data-ttu-id="6d30d-112">`ICorDebugHeapSegmentEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="6d30d-112">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="6d30d-113">`ICorDebugHeapSegmentEnum`インスタンスには、 [ICorDebugProcess5:: EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md)メソッドを呼び出すことによって[COR_SEGMENT](cor-segment-structure.md)インスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="6d30d-113">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_SEGMENT](cor-segment-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="6d30d-114">コレクション内の [COR_SEGMENT](cor-segment-structure.md) オブジェクトは、 [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md) メソッドを呼び出すことによって列挙できます。</span><span class="sxs-lookup"><span data-stu-id="6d30d-114">The [COR_SEGMENT](cor-segment-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="6d30d-115">`ICorDebugHeapSegmentEnum`コレクションオブジェクトは、マネージオブジェクトを含む可能性があるすべてのメモリ領域を列挙しますが、それらの領域にマネージオブジェクトが実際に存在することを保証するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="6d30d-115">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="6d30d-116">これには、空または予約済みのメモリ領域に関する情報が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6d30d-116">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d30d-117">要件</span><span class="sxs-lookup"><span data-stu-id="6d30d-117">Requirements</span></span>  

 <span data-ttu-id="6d30d-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d30d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d30d-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d30d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d30d-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d30d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d30d-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d30d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d30d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d30d-122">See also</span></span>

- [<span data-ttu-id="6d30d-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d30d-123">Debugging Interfaces</span></span>](debugging-interfaces.md)

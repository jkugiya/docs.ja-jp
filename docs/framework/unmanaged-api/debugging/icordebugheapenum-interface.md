---
description: '詳細情報: の説明'
title: ICorDebugHeapEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: c8a2f46bf412e2c4b2fe43d3eb50169191f40445
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660896"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="cc640-103">ICorDebugHeapEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc640-103">ICorDebugHeapEnum Interface</span></span>

<span data-ttu-id="cc640-104">マネージド ヒープのオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="cc640-104">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="cc640-105">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="cc640-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc640-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cc640-106">Methods</span></span>  
  
|<span data-ttu-id="cc640-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="cc640-107">Method</span></span>|<span data-ttu-id="cc640-108">説明</span><span class="sxs-lookup"><span data-stu-id="cc640-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc640-109">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="cc640-109">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="cc640-110">マネージヒープ上のオブジェクトに関する情報を格納している、指定した数の [COR_HEAPOBJECT](cor-heapobject-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc640-110">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc640-111">解説</span><span class="sxs-lookup"><span data-stu-id="cc640-111">Remarks</span></span>  

 <span data-ttu-id="cc640-112">`ICorDebugHeapEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="cc640-112">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="cc640-113">`ICorDebugHeapEnum`インスタンスには、 [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md)メソッドを呼び出すことによって[COR_HEAPOBJECT](cor-heapobject-structure.md)インスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="cc640-113">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="cc640-114">コレクション内の各 [COR_HEAPOBJECT](cor-heapobject-structure.md) インスタンスは、ヒープ上のライブオブジェクト、またはオブジェクトではなく、ガベージコレクターによってまだ収集されていないオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="cc640-114">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="cc640-115">コレクション内の [COR_HEAPOBJECT](cor-heapobject-structure.md) オブジェクトを列挙するには、 [次](icordebugheapenum-next-method.md) のメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="cc640-115">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc640-116">要件</span><span class="sxs-lookup"><span data-stu-id="cc640-116">Requirements</span></span>  

 <span data-ttu-id="cc640-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc640-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc640-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc640-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc640-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc640-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc640-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc640-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc640-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc640-121">See also</span></span>

- [<span data-ttu-id="cc640-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc640-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

---
description: 詳細については、次を参照してください
title: ICorDebugGCReferenceEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: ad4a61cdc2b30fb4c8e2be500eae878327c6b449
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801294"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="5d2a7-103">ICorDebugGCReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d2a7-103">ICorDebugGCReferenceEnum Interface</span></span>

<span data-ttu-id="5d2a7-104">ガベージ コレクトされるオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-104">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d2a7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5d2a7-105">Methods</span></span>  
  
|<span data-ttu-id="5d2a7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5d2a7-106">Method</span></span>|<span data-ttu-id="5d2a7-107">説明</span><span class="sxs-lookup"><span data-stu-id="5d2a7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d2a7-108">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="5d2a7-108">Next Method</span></span>](icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="5d2a7-109">ガベージコレクトされるオブジェクトに関する情報を格納している、指定した数の [COR_GC_REFERENCE](cor-gc-reference-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-109">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d2a7-110">解説</span><span class="sxs-lookup"><span data-stu-id="5d2a7-110">Remarks</span></span>  

 <span data-ttu-id="5d2a7-111">`ICorDebugGCReferenceEnum`インターフェイスは、"ICorDebugEnum" インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-111">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="5d2a7-112">`ICorDebugGCReferenceEnum`インスタンスには、 [ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md)メソッドを呼び出すことによって[COR_GC_REFERENCE](cor-gc-reference-structure.md)インスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-112">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="5d2a7-113">[COR_GC_REFERENCE](cor-gc-reference-structure.md) オブジェクトは、 [ICorDebugGCReference:: Next](icordebuggcreferenceenum-next-method.md) メソッドを呼び出すことによって列挙できます。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-113">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="5d2a7-114">このメソッドによって設定されるコレクション内の [COR_GC_REFERENCE](cor-gc-reference-structure.md) オブジェクトは、次の3種類のオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-114">The [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="5d2a7-115">すべてのマネージスタックからのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-115">Objects from all managed stacks.</span></span> <span data-ttu-id="5d2a7-116">これには、マネージコードのライブ参照や、共通言語ランタイムによって作成されたオブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-116">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="5d2a7-117">ハンドルテーブルのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-117">Objects from the handle table.</span></span> <span data-ttu-id="5d2a7-118">これには、モジュール内の厳密な参照 ( `HNDTYPE_STRONG` および `HNDTYPE_REFCOUNT` ) と静的変数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-118">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="5d2a7-119">ファイナライザーキューからのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-119">Objects from the finalizer queue.</span></span> <span data-ttu-id="5d2a7-120">ファイナライザーが実行されるまで、ファイナライザーはオブジェクトをキューに置いています。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-120">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d2a7-121">要件</span><span class="sxs-lookup"><span data-stu-id="5d2a7-121">Requirements</span></span>  

 <span data-ttu-id="5d2a7-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d2a7-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d2a7-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d2a7-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d2a7-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d2a7-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d2a7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d2a7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d2a7-126">See also</span></span>

- [<span data-ttu-id="5d2a7-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d2a7-127">Debugging Interfaces</span></span>](debugging-interfaces.md)

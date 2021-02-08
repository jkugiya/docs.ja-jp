---
description: '詳細については、次を参照してください: Corgcreの Encetype 列挙型'
title: CorGCReferenceType 列挙型
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
ms.openlocfilehash: a1f534f9fe4b9ba4ede0bef94f35cf1688fe1817
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801515"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="7b66e-103">CorGCReferenceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="7b66e-103">CorGCReferenceType Enumeration</span></span>

<span data-ttu-id="7b66e-104">ガベージ コレクトされる必要のあるオブジェクトのソースを識別します。</span><span class="sxs-lookup"><span data-stu-id="7b66e-104">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b66e-105">構文</span><span class="sxs-lookup"><span data-stu-id="7b66e-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="7b66e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="7b66e-106">Members</span></span>  
  
|<span data-ttu-id="7b66e-107">メンバー名</span><span class="sxs-lookup"><span data-stu-id="7b66e-107">Member name</span></span>|<span data-ttu-id="7b66e-108">説明</span><span class="sxs-lookup"><span data-stu-id="7b66e-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="7b66e-109">オブジェクト ハンドル テーブルからの強い参照へのハンドル。</span><span class="sxs-lookup"><span data-stu-id="7b66e-109">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="7b66e-110">オブジェクトハンドルテーブルからの固定された強い参照へのハンドル。</span><span class="sxs-lookup"><span data-stu-id="7b66e-110">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="7b66e-111">オブジェクトハンドルテーブルからの弱い参照へのハンドル。</span><span class="sxs-lookup"><span data-stu-id="7b66e-111">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="7b66e-112">オブジェクトハンドルテーブルからの弱い参照カウントオブジェクトへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="7b66e-112">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="7b66e-113">オブジェクトハンドルテーブルからの参照カウントオブジェクトへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="7b66e-113">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="7b66e-114">オブジェクトハンドルテーブルからの依存オブジェクトへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="7b66e-114">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="7b66e-115">オブジェクト ハンドル テーブルからの非同期固定オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7b66e-115">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="7b66e-116">ガベージ コレクション時に、すべてのオブジェクトおよびオブジェクト ルートの集合的なクロージャの概算サイズを保持する強力なハンドル。</span><span class="sxs-lookup"><span data-stu-id="7b66e-116">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="7b66e-117">マネージスタックからの参照。</span><span class="sxs-lookup"><span data-stu-id="7b66e-117">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="7b66e-118">ファイナライザーキューからの参照。</span><span class="sxs-lookup"><span data-stu-id="7b66e-118">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="7b66e-119">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="7b66e-119">CorHandleStrongOnly</span></span>|<span data-ttu-id="7b66e-120">ハンドルテーブルからの強い参照だけを返します。</span><span class="sxs-lookup"><span data-stu-id="7b66e-120">Return only strong references from the handle table.</span></span> <span data-ttu-id="7b66e-121">この値は、 [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) メソッドによってのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b66e-121">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="7b66e-122">ハンドルテーブルからの弱い参照だけを返します。</span><span class="sxs-lookup"><span data-stu-id="7b66e-122">Return only weak references from the handle table.</span></span> <span data-ttu-id="7b66e-123">この値は、 [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) メソッドによってのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b66e-123">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="7b66e-124">Handle テーブルからすべての参照を返します。</span><span class="sxs-lookup"><span data-stu-id="7b66e-124">Return all references from the handle table.</span></span> <span data-ttu-id="7b66e-125">この値は、 [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) メソッドによってのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b66e-125">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b66e-126">解説</span><span class="sxs-lookup"><span data-stu-id="7b66e-126">Remarks</span></span>  

 <span data-ttu-id="7b66e-127">`CorGCReferenceType`列挙体は次のように使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b66e-127">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="7b66e-128">`type` [COR_GC_REFERENCE](cor-gc-reference-structure.md)構造体のフィールドの値として、参照またはハンドルのソースを示します。</span><span class="sxs-lookup"><span data-stu-id="7b66e-128">As the value of the `type` field of the [COR_GC_REFERENCE](cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="7b66e-129">`types` [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md)メソッドの引数として、列挙体に含めるハンドルの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="7b66e-129">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b66e-130">要件</span><span class="sxs-lookup"><span data-stu-id="7b66e-130">Requirements</span></span>  

 <span data-ttu-id="7b66e-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b66e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b66e-132">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b66e-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b66e-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b66e-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b66e-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b66e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b66e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b66e-135">See also</span></span>

- [<span data-ttu-id="7b66e-136">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="7b66e-136">Debugging Enumerations</span></span>](debugging-enumerations.md)

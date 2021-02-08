---
description: '詳細情報: COR_HEAPOBJECT 構造'
title: COR_HEAPOBJECT 構造体
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: f41e02e7c528063f4b7ed485cbadbabb4d3e5ca7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801801"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="a62b5-103">COR_HEAPOBJECT 構造体</span><span class="sxs-lookup"><span data-stu-id="a62b5-103">COR_HEAPOBJECT Structure</span></span>

<span data-ttu-id="a62b5-104">マネージド ヒープ上のオブジェクトに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="a62b5-104">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a62b5-105">構文</span><span class="sxs-lookup"><span data-stu-id="a62b5-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="a62b5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a62b5-106">Members</span></span>  
  
|<span data-ttu-id="a62b5-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="a62b5-107">Member</span></span>|<span data-ttu-id="a62b5-108">説明</span><span class="sxs-lookup"><span data-stu-id="a62b5-108">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="a62b5-109">メモリ内のオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="a62b5-109">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="a62b5-110">オブジェクトの合計サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="a62b5-110">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="a62b5-111">オブジェクトの型を表す [COR_TYPEID](cor-typeid-structure.md) トークン。</span><span class="sxs-lookup"><span data-stu-id="a62b5-111">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a62b5-112">解説</span><span class="sxs-lookup"><span data-stu-id="a62b5-112">Remarks</span></span>  

 <span data-ttu-id="a62b5-113">`COR_HEAPOBJECT`インスタンスを取得するには、 [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md)メソッドを呼び出すことによって設定される、表示されている[heapheapenum](icordebugheapenum-interface.md)インターフェイスオブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a62b5-113">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="a62b5-114">インスタンスは、 `COR_HEAPOBJECT` マネージヒープ上のライブオブジェクトに関する情報、またはオブジェクトではなく、ガベージコレクターによってまだ収集されていないオブジェクトに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a62b5-114">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="a62b5-115">パフォーマンスを向上させるために、この `COR_HEAPOBJECT.address` フィールドは `CORDB_ADDRESS` デバッグ API の多くで使用される ICorDebugValue インターフェイス値ではなく、値になります。</span><span class="sxs-lookup"><span data-stu-id="a62b5-115">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="a62b5-116">指定されたオブジェクトアドレスの ICorDebugValue オブジェクトを取得するには、 `CORDB_ADDRESS` [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) メソッドに値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a62b5-116">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="a62b5-117">パフォーマンスを向上させるために、この `COR_HEAPOBJECT.type` フィールドは、 `COR_TYPEID` デバッグ API の多くで使用されている、テキスト型のインターフェイス値ではなく、値です。</span><span class="sxs-lookup"><span data-stu-id="a62b5-117">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="a62b5-118">指定された型 ID の `COR_TYPEID` [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) メソッドに値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a62b5-118">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="a62b5-119">構造体には、 `COR_HEAPOBJECT` 参照カウントの COM インターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a62b5-119">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="a62b5-120">のインスタンスを列挙子から取得する場合は、次の `COR_HEAPOBJECT` メソッドを呼び出す必要があります。その後、参照を解放する必要があります。 [](icordebugheapenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="a62b5-120">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a62b5-121">要件</span><span class="sxs-lookup"><span data-stu-id="a62b5-121">Requirements</span></span>  

 <span data-ttu-id="a62b5-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a62b5-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a62b5-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a62b5-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a62b5-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a62b5-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a62b5-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a62b5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62b5-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a62b5-126">See also</span></span>

- [<span data-ttu-id="a62b5-127">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="a62b5-127">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="a62b5-128">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a62b5-128">Debugging</span></span>](index.md)

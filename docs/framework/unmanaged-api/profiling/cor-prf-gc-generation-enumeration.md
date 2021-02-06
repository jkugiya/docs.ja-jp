---
description: '詳細情報: COR_PRF_GC_GENERATION 列挙型'
title: COR_PRF_GC_GENERATION 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
ms.openlocfilehash: 108bb4b2b4cba57235d354efe3b815a0e0df17ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648936"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="480e4-103">COR_PRF_GC_GENERATION 列挙型</span><span class="sxs-lookup"><span data-stu-id="480e4-103">COR_PRF_GC_GENERATION Enumeration</span></span>

<span data-ttu-id="480e4-104">ガベージコレクションの生成を識別します。</span><span class="sxs-lookup"><span data-stu-id="480e4-104">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="480e4-105">構文</span><span class="sxs-lookup"><span data-stu-id="480e4-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3,
    COR_PRF_GC_PINNED_OBJECT_HEAP= 4
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="480e4-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="480e4-106">Members</span></span>  
  
|<span data-ttu-id="480e4-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="480e4-107">Member</span></span>|<span data-ttu-id="480e4-108">説明</span><span class="sxs-lookup"><span data-stu-id="480e4-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="480e4-109">オブジェクトは、ジェネレーション0として格納されます。</span><span class="sxs-lookup"><span data-stu-id="480e4-109">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="480e4-110">オブジェクトは、ジェネレーション1として格納されます。</span><span class="sxs-lookup"><span data-stu-id="480e4-110">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="480e4-111">オブジェクトは、ジェネレーション2として格納されます。</span><span class="sxs-lookup"><span data-stu-id="480e4-111">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="480e4-112">オブジェクトは、ラージオブジェクトヒープに格納されます。</span><span class="sxs-lookup"><span data-stu-id="480e4-112">The object is stored in the large-object heap.</span></span>|  
|`COR_PRF_GC_PINNED_OBJECT_HEAP`|<span data-ttu-id="480e4-113">オブジェクトは、固定されたオブジェクトヒープに格納されます。</span><span class="sxs-lookup"><span data-stu-id="480e4-113">The object is stored in the pinned-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="480e4-114">解説</span><span class="sxs-lookup"><span data-stu-id="480e4-114">Remarks</span></span>  

 <span data-ttu-id="480e4-115">ガベージコレクターは、オブジェクトを経過期間に基づいてジェネレーションに分割することによって、メモリ管理のパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="480e4-115">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="480e4-116">現在、ガベージコレクターは、番号0、1、および2の3つのジェネレーションと、2つの特殊なヒープセグメント (大きなオブジェクト用とピン留めオブジェクト用) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="480e4-116">The garbage collector currently uses three generations, numbered 0, 1, and 2, and two special heap segments, one for large objects and one for pinned objects.</span></span>
  
 <span data-ttu-id="480e4-117">サイズがしきい値を超えるオブジェクトは、大きなオブジェクトヒープに格納されます。</span><span class="sxs-lookup"><span data-stu-id="480e4-117">Objects whose size is larger than a threshold value are stored in the large-object heap.</span></span> <span data-ttu-id="480e4-118">ピン留めされたオブジェクトは、通常のヒープに割り当てた場合のパフォーマンスコストを回避するために、固定されたオブジェクトヒープに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="480e4-118">Pinned objects can be allocated to the pinned-object heap to avoid the performance cost of allocating them on the normal heaps.</span></span> <span data-ttu-id="480e4-119">割り当てられた他のオブジェクトは、ジェネレーション0に属しています。</span><span class="sxs-lookup"><span data-stu-id="480e4-119">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="480e4-120">ジェネレーション0でガベージコレクションが発生した後に存在するすべてのオブジェクトは、ジェネレーション1に昇格されます。</span><span class="sxs-lookup"><span data-stu-id="480e4-120">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="480e4-121">ジェネレーション1でガベージコレクションが発生した後に存在するオブジェクトは、ジェネレーション2に移動します。</span><span class="sxs-lookup"><span data-stu-id="480e4-121">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="480e4-122">ジェネレーションを使用することは、ガベージコレクターが、割り当てられたオブジェクトのサブセットだけを一度に処理する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="480e4-122">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="480e4-123">`COR_PRF_GC_GENERATION`列挙体は、 [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md)構造体によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="480e4-123">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="480e4-124">要件</span><span class="sxs-lookup"><span data-stu-id="480e4-124">Requirements</span></span>  

 <span data-ttu-id="480e4-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="480e4-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="480e4-126">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="480e4-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="480e4-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="480e4-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="480e4-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="480e4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="480e4-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="480e4-129">See also</span></span>

- [<span data-ttu-id="480e4-130">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="480e4-130">Profiling Enumerations</span></span>](profiling-enumerations.md)

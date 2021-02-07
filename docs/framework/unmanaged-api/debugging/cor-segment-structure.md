---
description: '詳細情報: COR_SEGMENT 構造'
title: COR_SEGMENT 構造体
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
ms.openlocfilehash: 9bbc452b2c2036d019175ac1be8b9917ffa07b6a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712183"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="bc35e-103">COR_SEGMENT 構造体</span><span class="sxs-lookup"><span data-stu-id="bc35e-103">COR_SEGMENT Structure</span></span>

<span data-ttu-id="bc35e-104">マネージド ヒープのメモリ領域に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bc35e-104">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc35e-105">構文</span><span class="sxs-lookup"><span data-stu-id="bc35e-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;
    CORDB_ADDRESS end;
    CorDebugGenerationTypes gen;
    ULONG heap;
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="bc35e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="bc35e-106">Members</span></span>  
  
|<span data-ttu-id="bc35e-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="bc35e-107">Member</span></span>|<span data-ttu-id="bc35e-108">説明</span><span class="sxs-lookup"><span data-stu-id="bc35e-108">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="bc35e-109">メモリ領域の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="bc35e-109">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="bc35e-110">メモリ領域の終了アドレス。</span><span class="sxs-lookup"><span data-stu-id="bc35e-110">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="bc35e-111">メモリ領域の生成を示す [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) 列挙メンバー。</span><span class="sxs-lookup"><span data-stu-id="bc35e-111">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="bc35e-112">メモリ領域が存在するヒープ番号。</span><span class="sxs-lookup"><span data-stu-id="bc35e-112">The heap number in which the memory region resides.</span></span> <span data-ttu-id="bc35e-113">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc35e-113">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc35e-114">解説</span><span class="sxs-lookup"><span data-stu-id="bc35e-114">Remarks</span></span>  

 <span data-ttu-id="bc35e-115">`COR_SEGMENTS` 構造体は、マネージド ヒープのメモリ領域を表します。</span><span class="sxs-lookup"><span data-stu-id="bc35e-115">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="bc35e-116">`COR_SEGMENTS` オブジェクトは、[ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) メソッドを呼び出すことによって入力される [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) コレクション オブジェクトのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="bc35e-116">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="bc35e-117">`heap` フィールドは、報告されたヒープに対応するプロセッサ番号です。</span><span class="sxs-lookup"><span data-stu-id="bc35e-117">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="bc35e-118">ワークステーション ガベージ コレクターでは、ワークステーションにガベージ コレクション ヒープが 1 つしかないため、その値は常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="bc35e-118">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="bc35e-119">サーバー ガベージ コレクターでは、その値はヒープがアタッチされているプロセッサに対応します。</span><span class="sxs-lookup"><span data-stu-id="bc35e-119">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="bc35e-120">ガベージ コレクターの実装の詳細が原因で、実際のプロセッサ数よりも、ガベージ コレクション ヒープが多かったり少なかったりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="bc35e-120">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc35e-121">要件</span><span class="sxs-lookup"><span data-stu-id="bc35e-121">Requirements</span></span>  

 <span data-ttu-id="bc35e-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc35e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc35e-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc35e-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc35e-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc35e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc35e-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc35e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc35e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc35e-126">See also</span></span>

- [<span data-ttu-id="bc35e-127">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="bc35e-127">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="bc35e-128">デバッグ</span><span class="sxs-lookup"><span data-stu-id="bc35e-128">Debugging</span></span>](index.md)

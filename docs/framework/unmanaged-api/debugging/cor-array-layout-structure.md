---
description: '詳細情報: COR_ARRAY_LAYOUT 構造'
title: COR_ARRAY_LAYOUT 構造体
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
ms.openlocfilehash: dfd9f503356b65d0a85cb3a8f108409dc6aea011
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801827"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="1f21b-103">COR_ARRAY_LAYOUT 構造体</span><span class="sxs-lookup"><span data-stu-id="1f21b-103">COR_ARRAY_LAYOUT Structure</span></span>

<span data-ttu-id="1f21b-104">メモリ内の配列オブジェクトのレイアウトに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="1f21b-104">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f21b-105">構文</span><span class="sxs-lookup"><span data-stu-id="1f21b-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;
    ULONG32 rankSize;
    ULONG32 numRanks;
    ULONG32 rankOffset;
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="1f21b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1f21b-106">Members</span></span>  
  
|<span data-ttu-id="1f21b-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="1f21b-107">Member</span></span>|<span data-ttu-id="1f21b-108">説明</span><span class="sxs-lookup"><span data-stu-id="1f21b-108">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="1f21b-109">配列に格納されているオブジェクトの型の識別子。</span><span class="sxs-lookup"><span data-stu-id="1f21b-109">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="1f21b-110">コンポーネントがガベージコレクション参照、値クラス、またはプリミティブであるかどうかを示す CorElementType 列挙値。</span><span class="sxs-lookup"><span data-stu-id="1f21b-110">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="1f21b-111">配列内の最初の要素へのオフセット。</span><span class="sxs-lookup"><span data-stu-id="1f21b-111">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="1f21b-112">各要素のサイズ。</span><span class="sxs-lookup"><span data-stu-id="1f21b-112">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="1f21b-113">配列内の要素の数へのオフセット。</span><span class="sxs-lookup"><span data-stu-id="1f21b-113">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="1f21b-114">ランクのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="1f21b-114">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="1f21b-115">配列内のランクの数。</span><span class="sxs-lookup"><span data-stu-id="1f21b-115">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="1f21b-116">ランクの開始位置を示すオフセット。</span><span class="sxs-lookup"><span data-stu-id="1f21b-116">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f21b-117">解説</span><span class="sxs-lookup"><span data-stu-id="1f21b-117">Remarks</span></span>  

 <span data-ttu-id="1f21b-118">この `rankSize` フィールドは、多次元配列内のランクのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="1f21b-118">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="1f21b-119">これは、1次元配列に対しても正確です。</span><span class="sxs-lookup"><span data-stu-id="1f21b-119">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="1f21b-120">の値は、1 `numRanks` 次元配列の場合は1、 `N` 次元の多次元配列の場合は1になり `N` ます。</span><span class="sxs-lookup"><span data-stu-id="1f21b-120">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f21b-121">要件</span><span class="sxs-lookup"><span data-stu-id="1f21b-121">Requirements</span></span>  

 <span data-ttu-id="1f21b-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f21b-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f21b-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f21b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f21b-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f21b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f21b-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f21b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f21b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f21b-126">See also</span></span>

- [<span data-ttu-id="1f21b-127">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="1f21b-127">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="1f21b-128">デバッグ</span><span class="sxs-lookup"><span data-stu-id="1f21b-128">Debugging</span></span>](index.md)

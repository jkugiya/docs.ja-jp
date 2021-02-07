---
description: '詳細情報: COR_HEAPINFO 構造'
title: COR_HEAPINFO 構造体
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: 0841739172b3eaf807813af28e0b20fbb54608b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712315"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="de8f6-103">COR_HEAPINFO 構造体</span><span class="sxs-lookup"><span data-stu-id="de8f6-103">COR_HEAPINFO Structure</span></span>

<span data-ttu-id="de8f6-104">列挙可能かどうかなど、ガベージ コレクション ヒープに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="de8f6-104">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de8f6-105">構文</span><span class="sxs-lookup"><span data-stu-id="de8f6-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="de8f6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="de8f6-106">Members</span></span>  
  
|<span data-ttu-id="de8f6-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="de8f6-107">Member</span></span>|<span data-ttu-id="de8f6-108">説明</span><span class="sxs-lookup"><span data-stu-id="de8f6-108">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="de8f6-109">`true` ガベージコレクション構造体が有効で、ヒープを列挙できる場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="de8f6-109">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="de8f6-110">ターゲットアーキテクチャのポインターのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="de8f6-110">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="de8f6-111">プロセス内の論理ガベージコレクションヒープの数。</span><span class="sxs-lookup"><span data-stu-id="de8f6-111">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="de8f6-112">`TRUE` 同時実行 (バックグラウンド) ガベージコレクションが有効な場合は。それ以外の場合は `FALSE` 。</span><span class="sxs-lookup"><span data-stu-id="de8f6-112">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="de8f6-113">ガベージコレクターがワークステーションまたはサーバーのどちらで実行されているかを示す [CorDebugGCType](cordebuggctype-enumeration.md) 列挙体のメンバー。</span><span class="sxs-lookup"><span data-stu-id="de8f6-113">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de8f6-114">解説</span><span class="sxs-lookup"><span data-stu-id="de8f6-114">Remarks</span></span>  

 <span data-ttu-id="de8f6-115">構造体のインスタンス `COR_HEAPINFO` は、 [ICorDebugProcess5:: Getg apinformation](icordebugprocess5-getgcheapinformation-method.md) メソッドを呼び出すことによって返されます。</span><span class="sxs-lookup"><span data-stu-id="de8f6-115">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="de8f6-116">ガベージコレクションヒープ上のオブジェクトを列挙する前に、必ずフィールドをチェックし `areGCStructuresValid` て、ヒープが列挙可能な状態であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de8f6-116">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="de8f6-117">詳細については、「 [ICorDebugProcess5:: Getg](icordebugprocess5-getgcheapinformation-method.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de8f6-117">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de8f6-118">要件</span><span class="sxs-lookup"><span data-stu-id="de8f6-118">Requirements</span></span>  

 <span data-ttu-id="de8f6-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de8f6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de8f6-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de8f6-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de8f6-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de8f6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de8f6-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de8f6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de8f6-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="de8f6-123">See also</span></span>

- [<span data-ttu-id="de8f6-124">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="de8f6-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="de8f6-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="de8f6-125">Debugging</span></span>](index.md)

---
description: 詳細については、「IHostMalloc インターフェイス」を参照してください。
title: IHostMalloc インターフェイス
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: cd04a0f71fd429ea10b9edcce02806f4afa57148
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708178"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="233c3-103">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="233c3-103">IHostMalloc Interface</span></span>

<span data-ttu-id="233c3-104">共通言語ランタイム (CLR) がホストを介してヒープから細かい割り当てを要求できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="233c3-104">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="233c3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="233c3-105">Methods</span></span>  
  
|<span data-ttu-id="233c3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="233c3-106">Method</span></span>|<span data-ttu-id="233c3-107">説明</span><span class="sxs-lookup"><span data-stu-id="233c3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="233c3-108">Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="233c3-108">Alloc Method</span></span>](ihostmalloc-alloc-method.md)|<span data-ttu-id="233c3-109">ホストがヒープから要求された量のメモリを割り当てることを要求します。</span><span class="sxs-lookup"><span data-stu-id="233c3-109">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="233c3-110">DebugAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="233c3-110">DebugAlloc Method</span></span>](ihostmalloc-debugalloc-method.md)|<span data-ttu-id="233c3-111">は、要求されたメモリ量をヒープから割り当て、さらにメモリが割り当てられた場所を追跡することをホストに要求します。</span><span class="sxs-lookup"><span data-stu-id="233c3-111">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="233c3-112">Free メソッド</span><span class="sxs-lookup"><span data-stu-id="233c3-112">Free Method</span></span>](ihostmalloc-free-method.md)|<span data-ttu-id="233c3-113">メソッドを使用して割り当てられたメモリを解放し `Alloc` ます。</span><span class="sxs-lookup"><span data-stu-id="233c3-113">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="233c3-114">解説</span><span class="sxs-lookup"><span data-stu-id="233c3-114">Remarks</span></span>  

 <span data-ttu-id="233c3-115">CLR は、 `IHostMalloc` [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md) メソッドを呼び出すことによって、インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="233c3-115">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="233c3-116">要件</span><span class="sxs-lookup"><span data-stu-id="233c3-116">Requirements</span></span>  

 <span data-ttu-id="233c3-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="233c3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="233c3-118">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="233c3-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="233c3-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="233c3-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="233c3-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="233c3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="233c3-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="233c3-121">See also</span></span>

- [<span data-ttu-id="233c3-122">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="233c3-122">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="233c3-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="233c3-123">Hosting Interfaces</span></span>](hosting-interfaces.md)

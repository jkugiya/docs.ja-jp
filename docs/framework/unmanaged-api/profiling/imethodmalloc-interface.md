---
description: '詳細情報: IMethodMalloc インターフェイス'
title: IMethodMalloc インターフェイス
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 6b84ac0ddb49718d24b2cad174613bc311dc509b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736960"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="1e71a-103">IMethodMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e71a-103">IMethodMalloc Interface</span></span>

<span data-ttu-id="1e71a-104">新しい Microsoft 中間言語 (MSIL) 関数の本体にメモリを割り当てる方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="1e71a-104">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e71a-105">インターフェイスは、 `IMethodMalloc` 単純なメモリアロケーターです。</span><span class="sxs-lookup"><span data-stu-id="1e71a-105">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="1e71a-106">メモリを割り当てることはできますが、解放することはできません。</span><span class="sxs-lookup"><span data-stu-id="1e71a-106">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e71a-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="1e71a-107">Methods</span></span>  
  
|<span data-ttu-id="1e71a-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="1e71a-108">Method</span></span>|<span data-ttu-id="1e71a-109">説明</span><span class="sxs-lookup"><span data-stu-id="1e71a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e71a-110">Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="1e71a-110">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="1e71a-111">新しい MSIL 関数本体に指定された量のメモリを割り当てようとします。</span><span class="sxs-lookup"><span data-stu-id="1e71a-111">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e71a-112">解説</span><span class="sxs-lookup"><span data-stu-id="1e71a-112">Remarks</span></span>  

 <span data-ttu-id="1e71a-113">各アロケーターはモジュール固有であり、関数本体がモジュールのベースから正のオフセットになるようにします。</span><span class="sxs-lookup"><span data-stu-id="1e71a-113">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="1e71a-114">モジュールのベースを超えるメモリは貴重な場合があるため、アロケーターを使用して、関数本体にのみメモリを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e71a-114">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e71a-115">要件</span><span class="sxs-lookup"><span data-stu-id="1e71a-115">Requirements</span></span>  

 <span data-ttu-id="1e71a-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e71a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e71a-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1e71a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e71a-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e71a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e71a-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e71a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e71a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e71a-120">See also</span></span>

- [<span data-ttu-id="1e71a-121">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e71a-121">Profiling Interfaces</span></span>](profiling-interfaces.md)

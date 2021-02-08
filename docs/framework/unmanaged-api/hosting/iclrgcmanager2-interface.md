---
description: 詳細については、「ICLRGCManager2 インターフェイス」を参照してください。
title: ICLRGCManager2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: 455b3a99d10fa43bf325e9f7075d255dd55ae38b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789958"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="a6ce8-103">ICLRGCManager2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6ce8-103">ICLRGCManager2 Interface</span></span>

<span data-ttu-id="a6ce8-104">ホストが共通言語ランタイムのガベージコレクションシステムと対話できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6ce8-104">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a6ce8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a6ce8-105">Methods</span></span>  
  
|<span data-ttu-id="a6ce8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a6ce8-106">Method</span></span>|<span data-ttu-id="a6ce8-107">説明</span><span class="sxs-lookup"><span data-stu-id="a6ce8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6ce8-108">SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="a6ce8-108">SetGCStartupLimitsEx Method</span></span>](iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="a6ce8-109">ガベージコレクションセグメントのサイズとガベージコレクションシステムのジェネレーション0の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="a6ce8-109">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="a6ce8-110">より大きいジェネレーション0およびセグメントサイズを有効に `DWORD` します。</span><span class="sxs-lookup"><span data-stu-id="a6ce8-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6ce8-111">解説</span><span class="sxs-lookup"><span data-stu-id="a6ce8-111">Remarks</span></span>  

 <span data-ttu-id="a6ce8-112">このインターフェイスは、 [ICLRGCManager インターフェイス](iclrgcmanager-interface.md)から継承されます。</span><span class="sxs-lookup"><span data-stu-id="a6ce8-112">This interface inherits from the [ICLRGCManager Interface](iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="a6ce8-113">共通言語ランタイム (CLR) は、マネージ型を使用してガベージコレクション機構を実装し <xref:System.GC> ます。</span><span class="sxs-lookup"><span data-stu-id="a6ce8-113">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="a6ce8-114">ガベージコレクションシステムの詳細については、「 [ガベージコレクション](../../../standard/garbage-collection/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ce8-114">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6ce8-115">要件</span><span class="sxs-lookup"><span data-stu-id="a6ce8-115">Requirements</span></span>  

 <span data-ttu-id="a6ce8-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ce8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6ce8-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a6ce8-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6ce8-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a6ce8-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6ce8-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6ce8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6ce8-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6ce8-120">See also</span></span>

- [<span data-ttu-id="a6ce8-121">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="a6ce8-121">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="a6ce8-122">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="a6ce8-122">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="a6ce8-123">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6ce8-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a6ce8-124">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6ce8-124">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="a6ce8-125">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6ce8-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="a6ce8-126">ホスティング</span><span class="sxs-lookup"><span data-stu-id="a6ce8-126">Hosting</span></span>](index.md)

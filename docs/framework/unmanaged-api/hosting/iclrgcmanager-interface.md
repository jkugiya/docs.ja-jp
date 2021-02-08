---
description: 詳細については、「ICLRGCManager インターフェイス」を参照してください。
title: ICLRGCManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
ms.openlocfilehash: 648b2b131e28da8aabc7028b6d745351cae772fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789997"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="e6439-103">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6439-103">ICLRGCManager Interface</span></span>

<span data-ttu-id="e6439-104">ホストが共通言語ランタイムのガベージコレクションシステムと対話できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e6439-104">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6439-105">.NET Framework 4.5 以降では、 [ICLRGCManager2:: SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) メソッドを使用して、ガベージコレクションセグメントのサイズと、ガベージコレクションシステムのジェネレーション0の最大サイズを、 `DWORD` [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) メソッドによって設定された制限を超える値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="e6439-105">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6439-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6439-106">Methods</span></span>  
  
|<span data-ttu-id="e6439-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6439-107">Method</span></span>|<span data-ttu-id="e6439-108">説明</span><span class="sxs-lookup"><span data-stu-id="e6439-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6439-109">Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="e6439-109">Collect Method</span></span>](iclrgcmanager-collect-method.md)|<span data-ttu-id="e6439-110">指定したジェネレーションのガベージコレクションを強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="e6439-110">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="e6439-111">GetStats メソッド</span><span class="sxs-lookup"><span data-stu-id="e6439-111">GetStats Method</span></span>](iclrgcmanager-getstats-method.md)|<span data-ttu-id="e6439-112">ガベージコレクションシステムに関する現在の統計のセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="e6439-112">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="e6439-113">SetGCStartupLimits メソッド</span><span class="sxs-lookup"><span data-stu-id="e6439-113">SetGCStartupLimits Method</span></span>](iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="e6439-114">ガベージコレクションセグメントのサイズとガベージコレクションシステムのジェネレーション0の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="e6439-114">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6439-115">解説</span><span class="sxs-lookup"><span data-stu-id="e6439-115">Remarks</span></span>  

 <span data-ttu-id="e6439-116">共通言語ランタイム (CLR) は、マネージ型を使用してガベージコレクション機構を実装し <xref:System.GC> ます。</span><span class="sxs-lookup"><span data-stu-id="e6439-116">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="e6439-117">ガベージコレクションシステムの詳細については、「 [ガベージコレクション](../../../standard/garbage-collection/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6439-117">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6439-118">要件</span><span class="sxs-lookup"><span data-stu-id="e6439-118">Requirements</span></span>  

 <span data-ttu-id="e6439-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6439-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6439-120">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e6439-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6439-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e6439-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6439-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6439-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6439-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6439-123">See also</span></span>

- [<span data-ttu-id="e6439-124">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="e6439-124">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="e6439-125">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="e6439-125">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="e6439-126">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6439-126">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="e6439-127">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6439-127">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="e6439-128">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6439-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e6439-129">ホスティング</span><span class="sxs-lookup"><span data-stu-id="e6439-129">Hosting</span></span>](index.md)

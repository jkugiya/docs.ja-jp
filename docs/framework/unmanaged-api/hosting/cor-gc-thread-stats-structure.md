---
description: '詳細情報: COR_GC_THREAD_STATS 構造'
title: COR_GC_THREAD_STATS 構造体
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 179eb335e9f8c118ee98d4b777c347f3758ee0c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799786"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="88dca-103">COR_GC_THREAD_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="88dca-103">COR_GC_THREAD_STATS Structure</span></span>

<span data-ttu-id="88dca-104">ガベージコレクションに関連するスレッドごとの統計情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="88dca-104">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88dca-105">構文</span><span class="sxs-lookup"><span data-stu-id="88dca-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="88dca-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="88dca-106">Members</span></span>  
  
|<span data-ttu-id="88dca-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="88dca-107">Member</span></span>|<span data-ttu-id="88dca-108">説明</span><span class="sxs-lookup"><span data-stu-id="88dca-108">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="88dca-109">現在のインスタンスに関連付けられているスレッドに割り当てられたメモリのバイト数 `COR_GC_THREAD_STATS` 。</span><span class="sxs-lookup"><span data-stu-id="88dca-109">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="88dca-110">ジェネレーション0のガベージコレクションが発生するたびに、この数値はゼロにクリアされます。</span><span class="sxs-lookup"><span data-stu-id="88dca-110">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="88dca-111">最新のガベージコレクションで上位のジェネレーションに昇格されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="88dca-111">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88dca-112">解説</span><span class="sxs-lookup"><span data-stu-id="88dca-112">Remarks</span></span>  

 <span data-ttu-id="88dca-113">[ICLRTask:: GetMemStats](iclrtask-getmemstats-method.md) は、型の出力パラメーターを受け取り `COR_GC_THREAD_STATS` ます。</span><span class="sxs-lookup"><span data-stu-id="88dca-113">[ICLRTask::GetMemStats](iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88dca-114">要件</span><span class="sxs-lookup"><span data-stu-id="88dca-114">Requirements</span></span>  

 <span data-ttu-id="88dca-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88dca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88dca-116">**ヘッダー:** GCHost</span><span class="sxs-lookup"><span data-stu-id="88dca-116">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="88dca-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="88dca-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88dca-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88dca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88dca-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="88dca-119">See also</span></span>

- [<span data-ttu-id="88dca-120">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="88dca-120">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="88dca-121">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="88dca-121">IHostTask Interface</span></span>](ihosttask-interface.md)

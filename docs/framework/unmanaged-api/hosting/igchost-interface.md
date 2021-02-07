---
description: 詳細については、「IGCHost インターフェイス」を参照してください。
title: IGCHost インターフェイス
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
ms.openlocfilehash: 73b1125eb66a38373da85769ab80ddcaf0b955c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709595"
---
# <a name="igchost-interface"></a><span data-ttu-id="7c005-103">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c005-103">IGCHost Interface</span></span>

<span data-ttu-id="7c005-104">ガベージコレクションシステムに関する情報を取得し、ガベージコレクションのいくつかの側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7c005-104">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c005-105">.NET Framework 4.5 以降では、 [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) メソッドを使用して、ガベージコレクションセグメントのサイズと、ガベージコレクションシステムのジェネレーション0の最大サイズを、 `DWORD` [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) メソッドによって設定された制限を超える値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="7c005-105">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c005-106">このインターフェイスは、専門家による使用のみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="7c005-106">This interface is for expert usage only.</span></span> <span data-ttu-id="7c005-107">不適切に使用した場合、アプリケーションのパフォーマンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c005-107">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c005-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c005-108">Methods</span></span>  
  
|<span data-ttu-id="7c005-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c005-109">Method</span></span>|<span data-ttu-id="7c005-110">説明</span><span class="sxs-lookup"><span data-stu-id="7c005-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c005-111">Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="7c005-111">Collect Method</span></span>](igchost-collect-method.md)|<span data-ttu-id="7c005-112">現在のガベージコレクションの状態に関係なく、指定したジェネレーションに対して強制的にコレクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="7c005-112">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="7c005-113">GetStats メソッド</span><span class="sxs-lookup"><span data-stu-id="7c005-113">GetStats Method</span></span>](igchost-getstats-method.md)|<span data-ttu-id="7c005-114">ガベージコレクションシステムの現在の状態の統計を取得します。</span><span class="sxs-lookup"><span data-stu-id="7c005-114">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="7c005-115">GetThreadStats メソッド</span><span class="sxs-lookup"><span data-stu-id="7c005-115">GetThreadStats Method</span></span>](igchost-getthreadstats-method.md)|<span data-ttu-id="7c005-116">ガベージコレクションのスレッドごとの統計を取得します。</span><span class="sxs-lookup"><span data-stu-id="7c005-116">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="7c005-117">SetGCStartupLimits メソッド</span><span class="sxs-lookup"><span data-stu-id="7c005-117">SetGCStartupLimits Method</span></span>](igchost-setgcstartuplimits-method.md)|<span data-ttu-id="7c005-118">ジェネレーション0のセグメントサイズと最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="7c005-118">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="7c005-119">SetVirtualMemLimit メソッド</span><span class="sxs-lookup"><span data-stu-id="7c005-119">SetVirtualMemLimit Method</span></span>](igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="7c005-120">ランタイムの仮想メモリの最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="7c005-120">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c005-121">要件</span><span class="sxs-lookup"><span data-stu-id="7c005-121">Requirements</span></span>  

 <span data-ttu-id="7c005-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c005-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c005-123">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="7c005-123">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="7c005-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7c005-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c005-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c005-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c005-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c005-126">See also</span></span>

- [<span data-ttu-id="7c005-127">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c005-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7c005-128">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="7c005-128">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)

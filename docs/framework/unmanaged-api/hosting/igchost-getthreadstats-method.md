---
description: '詳細について: IGCHost:: GetThreadStats メソッド'
title: IGCHost::GetThreadStats メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: 2d923560e915a0c88035caad70ad91149d793cb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709660"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="9be37-103">IGCHost::GetThreadStats メソッド</span><span class="sxs-lookup"><span data-stu-id="9be37-103">IGCHost::GetThreadStats Method</span></span>

<span data-ttu-id="9be37-104">ガベージコレクションのスレッドごとの統計を取得します。</span><span class="sxs-lookup"><span data-stu-id="9be37-104">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9be37-105">構文</span><span class="sxs-lookup"><span data-stu-id="9be37-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9be37-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9be37-106">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="9be37-107">から統計を取得するスレッドを指定するファイバークッキーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9be37-107">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="9be37-108">[入力、出力]指定したスレッドのガベージコレクションの統計情報を格納している [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9be37-108">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9be37-109">要件</span><span class="sxs-lookup"><span data-stu-id="9be37-109">Requirements</span></span>  

 <span data-ttu-id="9be37-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9be37-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9be37-111">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="9be37-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="9be37-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9be37-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9be37-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9be37-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be37-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9be37-114">See also</span></span>

- [<span data-ttu-id="9be37-115">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9be37-115">IGCHost Interface</span></span>](igchost-interface.md)

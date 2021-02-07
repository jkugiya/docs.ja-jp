---
description: '詳細について: IGCHost:: GetStats メソッド'
title: IGCHost::GetStats メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
ms.openlocfilehash: 564224d01e23c8ac1fe81025ee87dabc41ed5166
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709692"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="73716-103">IGCHost::GetStats メソッド</span><span class="sxs-lookup"><span data-stu-id="73716-103">IGCHost::GetStats Method</span></span>

<span data-ttu-id="73716-104">ガベージコレクションシステムの現在の状態の統計を取得します。</span><span class="sxs-lookup"><span data-stu-id="73716-104">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73716-105">構文</span><span class="sxs-lookup"><span data-stu-id="73716-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73716-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="73716-106">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="73716-107">[入力、出力]ガベージコレクションシステムの現在の状態の統計情報を格納している [COR_GC_STATS](cor-gc-stats-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="73716-107">[in, out] A pointer to a [COR_GC_STATS](cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73716-108">解説</span><span class="sxs-lookup"><span data-stu-id="73716-108">Remarks</span></span>  

 <span data-ttu-id="73716-109">統計は、ガベージコレクションシステムが動作するためにスマートアロケーションシステムによって使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="73716-109">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="73716-110">たとえば、割り当てシステムでは、統計情報を確認した後に、メモリを追加したり、コレクションを強制したりする必要があることを判断できます。</span><span class="sxs-lookup"><span data-stu-id="73716-110">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73716-111">要件</span><span class="sxs-lookup"><span data-stu-id="73716-111">Requirements</span></span>  

 <span data-ttu-id="73716-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73716-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73716-113">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="73716-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="73716-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="73716-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73716-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73716-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73716-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="73716-116">See also</span></span>

- [<span data-ttu-id="73716-117">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73716-117">IGCHost Interface</span></span>](igchost-interface.md)

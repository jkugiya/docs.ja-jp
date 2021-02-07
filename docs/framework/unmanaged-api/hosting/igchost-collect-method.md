---
description: '詳細について: IGCHost:: Collect メソッド'
title: IGCHost::Collect メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
ms.openlocfilehash: b4c249e07709dc443ae7dd6c6a5bfd206b7f1caa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709695"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="2dc93-103">IGCHost::Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="2dc93-103">IGCHost::Collect Method</span></span>

<span data-ttu-id="2dc93-104">現在のガベージコレクションの状態に関係なく、指定したジェネレーションに対して強制的にコレクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="2dc93-104">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc93-105">構文</span><span class="sxs-lookup"><span data-stu-id="2dc93-105">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dc93-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2dc93-106">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="2dc93-107">からガベージコレクションを実行する生成。</span><span class="sxs-lookup"><span data-stu-id="2dc93-107">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="2dc93-108">値-1 は、すべてのジェネレーションがガベージコレクションを実行することを示します。</span><span class="sxs-lookup"><span data-stu-id="2dc93-108">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dc93-109">要件</span><span class="sxs-lookup"><span data-stu-id="2dc93-109">Requirements</span></span>  

 <span data-ttu-id="2dc93-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dc93-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dc93-111">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="2dc93-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="2dc93-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2dc93-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2dc93-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dc93-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc93-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2dc93-114">See also</span></span>

- [<span data-ttu-id="2dc93-115">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2dc93-115">IGCHost Interface</span></span>](igchost-interface.md)

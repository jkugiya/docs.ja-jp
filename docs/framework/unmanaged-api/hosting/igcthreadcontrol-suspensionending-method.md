---
description: '詳細情報: IGCThreadControl:: SuspensionEnding メソッド'
title: IGCThreadControl::SuspensionEnding メソッド
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
ms.openlocfilehash: 5ff889f45ea3664312060f373907e65c367276f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709270"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="fabf7-103">IGCThreadControl::SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="fabf7-103">IGCThreadControl::SuspensionEnding Method</span></span>

<span data-ttu-id="fabf7-104">ランタイムがガベージコレクションまたはその他の中断後にスレッドを再開していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="fabf7-104">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fabf7-105">構文</span><span class="sxs-lookup"><span data-stu-id="fabf7-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fabf7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fabf7-106">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="fabf7-107">からガベージコレクションが実行された生成。</span><span class="sxs-lookup"><span data-stu-id="fabf7-107">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fabf7-108">解説</span><span class="sxs-lookup"><span data-stu-id="fabf7-108">Remarks</span></span>  

 <span data-ttu-id="fabf7-109">コールバック中にスレッドを再スケジュールしないでください `SuspensionEnding` 。</span><span class="sxs-lookup"><span data-stu-id="fabf7-109">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fabf7-110">要件</span><span class="sxs-lookup"><span data-stu-id="fabf7-110">Requirements</span></span>  

 <span data-ttu-id="fabf7-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fabf7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fabf7-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fabf7-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fabf7-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="fabf7-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fabf7-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fabf7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fabf7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fabf7-115">See also</span></span>

- [<span data-ttu-id="fabf7-116">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fabf7-116">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)

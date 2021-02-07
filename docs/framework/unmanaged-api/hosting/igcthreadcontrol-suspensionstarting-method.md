---
description: '詳細情報: IGCThreadControl:: SuspensionStarting メソッド'
title: IGCThreadControl::SuspensionStarting メソッド
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
ms.openlocfilehash: b9d068e6995a73e9a9a31d5d5debf008f9748630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709296"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="0d68a-103">IGCThreadControl::SuspensionStarting メソッド</span><span class="sxs-lookup"><span data-stu-id="0d68a-103">IGCThreadControl::SuspensionStarting Method</span></span>

<span data-ttu-id="0d68a-104">ランタイムがガベージコレクションまたは他の中断のためにスレッドの中断を開始していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="0d68a-104">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d68a-105">構文</span><span class="sxs-lookup"><span data-stu-id="0d68a-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="0d68a-106">解説</span><span class="sxs-lookup"><span data-stu-id="0d68a-106">Remarks</span></span>  

 <span data-ttu-id="0d68a-107">コールバック中にスレッドを再スケジュールしないでください `SuspensionStarting` 。</span><span class="sxs-lookup"><span data-stu-id="0d68a-107">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d68a-108">要件</span><span class="sxs-lookup"><span data-stu-id="0d68a-108">Requirements</span></span>  

 <span data-ttu-id="0d68a-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d68a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d68a-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0d68a-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d68a-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0d68a-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d68a-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d68a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d68a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d68a-113">See also</span></span>

- [<span data-ttu-id="0d68a-114">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d68a-114">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)

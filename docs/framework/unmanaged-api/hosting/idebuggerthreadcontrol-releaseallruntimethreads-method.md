---
description: '詳細情報: Iデバッガ Threadcontrol:: ReleaseAllRuntimeThreads メソッド'
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads メソッド
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
ms.openlocfilehash: bf551ccc2ae5bde3333dc8e3957099590a494dd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709773"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="92ac2-103">IDebuggerThreadControl::ReleaseAllRuntimeThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="92ac2-103">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>

<span data-ttu-id="92ac2-104">デバッグサービスがブロックされているすべてのスレッドを解放しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="92ac2-104">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92ac2-105">構文</span><span class="sxs-lookup"><span data-stu-id="92ac2-105">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="92ac2-106">解説</span><span class="sxs-lookup"><span data-stu-id="92ac2-106">Remarks</span></span>  

 <span data-ttu-id="92ac2-107">メソッドは、 `ReleaseAllRuntimeThreads` ランタイムスレッドでは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="92ac2-107">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="92ac2-108">ホストにランタイムスレッドがブロックされている場合は、この時点で解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92ac2-108">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92ac2-109">要件</span><span class="sxs-lookup"><span data-stu-id="92ac2-109">Requirements</span></span>  

 <span data-ttu-id="92ac2-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92ac2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92ac2-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="92ac2-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92ac2-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="92ac2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92ac2-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92ac2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ac2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="92ac2-114">See also</span></span>

- [<span data-ttu-id="92ac2-115">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92ac2-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)

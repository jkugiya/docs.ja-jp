---
description: '詳細情報: IGCThreadControl:: ThreadIsBlockingForSuspension メソッド'
title: IGCThreadControl::ThreadIsBlockingForSuspension メソッド
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: 13023a75ab1c438abebbeb16fd9fe7c4b95c37ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709205"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="bd1cb-103">IGCThreadControl::ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="bd1cb-103">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="bd1cb-104">呼び出しを行っているスレッドがブロックしようとしていることをホストに通知します。ガベージコレクションやその他の中断が考えられます。</span><span class="sxs-lookup"><span data-stu-id="bd1cb-104">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd1cb-105">構文</span><span class="sxs-lookup"><span data-stu-id="bd1cb-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd1cb-106">解説</span><span class="sxs-lookup"><span data-stu-id="bd1cb-106">Remarks</span></span>  

 <span data-ttu-id="bd1cb-107">ホストは、 `ThreadIsBlockingForSuspension` スレッドを再スケジュールするかどうかをコールバック内で選択できます。</span><span class="sxs-lookup"><span data-stu-id="bd1cb-107">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd1cb-108">要件</span><span class="sxs-lookup"><span data-stu-id="bd1cb-108">Requirements</span></span>  

 <span data-ttu-id="bd1cb-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd1cb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd1cb-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bd1cb-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd1cb-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bd1cb-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd1cb-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd1cb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1cb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd1cb-113">See also</span></span>

- [<span data-ttu-id="bd1cb-114">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bd1cb-114">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)

---
description: '詳細について: ICorConfiguration:: SetGCThreadControl メソッド'
title: ICorConfiguration::SetGCThreadControl メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: 8b9388bdefb9da2ce51b62ab68eeee54645e43ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636640"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="265a3-103">ICorConfiguration::SetGCThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="265a3-103">ICorConfiguration::SetGCThreadControl Method</span></span>

<span data-ttu-id="265a3-104">ガベージコレクションに対してブロックされる非ランタイムタスクのスレッドをスケジュールするためのコールバックインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="265a3-104">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="265a3-105">構文</span><span class="sxs-lookup"><span data-stu-id="265a3-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="265a3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="265a3-106">Parameters</span></span>  

 `pGCThreadControl`  
 <span data-ttu-id="265a3-107">から非ランタイムタスクのスレッドの中断をホストに通知する [Igcthreadcontrol](igcthreadcontrol-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="265a3-107">[in] A pointer to an [IGCThreadControl](igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="265a3-108">解説</span><span class="sxs-lookup"><span data-stu-id="265a3-108">Remarks</span></span>  

 <span data-ttu-id="265a3-109">ホストは、スレッドを再スケジュールするかどうかにかかわらず、 [Igcthreadcontrol:: ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) コールバック内で選択できます。</span><span class="sxs-lookup"><span data-stu-id="265a3-109">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="265a3-110">要件</span><span class="sxs-lookup"><span data-stu-id="265a3-110">Requirements</span></span>  

 <span data-ttu-id="265a3-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="265a3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="265a3-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="265a3-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="265a3-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="265a3-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="265a3-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="265a3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="265a3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="265a3-115">See also</span></span>

- [<span data-ttu-id="265a3-116">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="265a3-116">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)

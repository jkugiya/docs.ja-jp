---
description: '詳細情報: ICorConfiguration::SetGCThreadControl メソッド'
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636640"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="a3048-103">ICorConfiguration::SetGCThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="a3048-103">ICorConfiguration::SetGCThreadControl Method</span></span>

<span data-ttu-id="a3048-104">本来ならガベージ コレクションのためにブロックされる非ランタイム タスク用のスレッドをスケジュールするための、コールバック インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="a3048-104">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3048-105">構文</span><span class="sxs-lookup"><span data-stu-id="a3048-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3048-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a3048-106">Parameters</span></span>  

 `pGCThreadControl`  
 <span data-ttu-id="a3048-107">[in] 非ランタイム タスク用のスレッドの中断をホストに通知する [IGCThreadControl](igcthreadcontrol-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a3048-107">[in] A pointer to an [IGCThreadControl](igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3048-108">解説</span><span class="sxs-lookup"><span data-stu-id="a3048-108">Remarks</span></span>  

 <span data-ttu-id="a3048-109">ホストでは、スレッドを再スケジュールするかどうかを [IGCThreadControl::ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) コールバック内で選択できます。</span><span class="sxs-lookup"><span data-stu-id="a3048-109">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3048-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="a3048-110">Requirements</span></span>  

 <span data-ttu-id="a3048-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3048-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3048-112">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3048-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3048-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="a3048-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3048-114">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3048-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3048-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3048-115">See also</span></span>

- [<span data-ttu-id="a3048-116">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3048-116">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)

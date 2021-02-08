---
description: ': IHostTask:: Start メソッドの詳細について説明します。'
title: IHostTask::Start メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
ms.openlocfilehash: 48352a3df49ba2ef3e008ed211da19f54deb82f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784627"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="42f7b-103">IHostTask::Start メソッド</span><span class="sxs-lookup"><span data-stu-id="42f7b-103">IHostTask::Start Method</span></span>

<span data-ttu-id="42f7b-104">現在の [IHostTask](ihosttask-interface.md) インスタンスによって表されているタスクを、中断されているからライブ状態 (コードを実行できる) に移動するようホストに要求します。</span><span class="sxs-lookup"><span data-stu-id="42f7b-104">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f7b-105">構文</span><span class="sxs-lookup"><span data-stu-id="42f7b-105">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="42f7b-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="42f7b-106">Return Value</span></span>  
  
|<span data-ttu-id="42f7b-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42f7b-107">HRESULT</span></span>|<span data-ttu-id="42f7b-108">説明</span><span class="sxs-lookup"><span data-stu-id="42f7b-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42f7b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="42f7b-109">S_OK</span></span>|<span data-ttu-id="42f7b-110">Start が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="42f7b-110">Start returned successfully.</span></span>|  
|<span data-ttu-id="42f7b-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42f7b-111">E_FAIL</span></span>|<span data-ttu-id="42f7b-112">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="42f7b-112">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42f7b-113">メソッドから E_FAIL が返された場合、そのプロセス内で共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="42f7b-113">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="42f7b-114">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="42f7b-114">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42f7b-115">解説</span><span class="sxs-lookup"><span data-stu-id="42f7b-115">Remarks</span></span>  

 <span data-ttu-id="42f7b-116">`Start` 重大なエラーが発生した場合を除き、は常に S_OK の HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="42f7b-116">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42f7b-117">要件</span><span class="sxs-lookup"><span data-stu-id="42f7b-117">Requirements</span></span>  

 <span data-ttu-id="42f7b-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42f7b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42f7b-119">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="42f7b-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42f7b-120">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="42f7b-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42f7b-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42f7b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f7b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="42f7b-122">See also</span></span>

- [<span data-ttu-id="42f7b-123">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42f7b-123">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="42f7b-124">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42f7b-124">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="42f7b-125">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42f7b-125">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="42f7b-126">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42f7b-126">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

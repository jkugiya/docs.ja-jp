---
description: '詳細について: IHostTaskManager:: SetCLRTaskManager メソッド'
title: IHostTaskManager::SetCLRTaskManager メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: 438a5b56afd42eceafb484bdf0020efbad86d052
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680877"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="35f28-103">IHostTaskManager::SetCLRTaskManager メソッド</span><span class="sxs-lookup"><span data-stu-id="35f28-103">IHostTaskManager::SetCLRTaskManager Method</span></span>

<span data-ttu-id="35f28-104">共通言語ランタイム (CLR) によって実装された [ICLRTaskManager](iclrtaskmanager-interface.md) インスタンスへのインターフェイスポインターをホストに提供します。</span><span class="sxs-lookup"><span data-stu-id="35f28-104">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35f28-105">構文</span><span class="sxs-lookup"><span data-stu-id="35f28-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35f28-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="35f28-106">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="35f28-107">から `ICLRTaskManager` 共通言語ランタイムによって実装されたインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="35f28-107">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35f28-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="35f28-108">Return Value</span></span>  
  
|<span data-ttu-id="35f28-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="35f28-109">HRESULT</span></span>|<span data-ttu-id="35f28-110">説明</span><span class="sxs-lookup"><span data-stu-id="35f28-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35f28-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="35f28-111">S_OK</span></span>|<span data-ttu-id="35f28-112">`SetCLRTaskManager` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="35f28-112">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="35f28-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="35f28-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="35f28-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="35f28-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="35f28-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="35f28-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="35f28-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="35f28-116">The call timed out.</span></span>|  
|<span data-ttu-id="35f28-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="35f28-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="35f28-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="35f28-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="35f28-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="35f28-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="35f28-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="35f28-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="35f28-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="35f28-121">E_FAIL</span></span>|<span data-ttu-id="35f28-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="35f28-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="35f28-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="35f28-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="35f28-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="35f28-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35f28-125">解説</span><span class="sxs-lookup"><span data-stu-id="35f28-125">Remarks</span></span>  

 <span data-ttu-id="35f28-126">ランタイムはを呼び出して、 `SetCLRTaskManager` ホストにインスタンスへのインターフェイスポインターを提供し `ICLRTaskManager` ます。</span><span class="sxs-lookup"><span data-stu-id="35f28-126">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35f28-127">要件</span><span class="sxs-lookup"><span data-stu-id="35f28-127">Requirements</span></span>  

 <span data-ttu-id="35f28-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35f28-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35f28-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="35f28-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35f28-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="35f28-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35f28-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35f28-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f28-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="35f28-132">See also</span></span>

- [<span data-ttu-id="35f28-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35f28-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="35f28-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35f28-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="35f28-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35f28-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="35f28-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35f28-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

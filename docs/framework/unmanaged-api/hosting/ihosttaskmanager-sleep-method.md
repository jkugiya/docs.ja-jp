---
description: '詳細について: IHostTaskManager:: Sleep メソッド'
title: IHostTaskManager::Sleep メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
ms.openlocfilehash: fedb87c6bd4558a2aa6158299551327cb2271d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789373"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="0f84e-103">IHostTaskManager::Sleep メソッド</span><span class="sxs-lookup"><span data-stu-id="0f84e-103">IHostTaskManager::Sleep Method</span></span>

<span data-ttu-id="0f84e-104">現在のタスクがスリープ状態になることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="0f84e-104">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f84e-105">構文</span><span class="sxs-lookup"><span data-stu-id="0f84e-105">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f84e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f84e-106">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="0f84e-107">からスレッドがスリープする時間間隔 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="0f84e-107">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="0f84e-108">から [WAIT_OPTION](wait-option-enumeration.md) 列挙値の1つ。このアクションがブロックされた場合にホストが実行するアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="0f84e-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f84e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="0f84e-109">Return Value</span></span>  
  
|<span data-ttu-id="0f84e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f84e-110">HRESULT</span></span>|<span data-ttu-id="0f84e-111">説明</span><span class="sxs-lookup"><span data-stu-id="0f84e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f84e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f84e-112">S_OK</span></span>|<span data-ttu-id="0f84e-113">`Sleep` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="0f84e-113">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="0f84e-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f84e-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f84e-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="0f84e-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f84e-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f84e-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f84e-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0f84e-117">The call timed out.</span></span>|  
|<span data-ttu-id="0f84e-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f84e-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f84e-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0f84e-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f84e-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f84e-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f84e-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="0f84e-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f84e-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f84e-122">E_FAIL</span></span>|<span data-ttu-id="0f84e-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0f84e-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f84e-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="0f84e-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f84e-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="0f84e-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f84e-126">解説</span><span class="sxs-lookup"><span data-stu-id="0f84e-126">Remarks</span></span>  

 <span data-ttu-id="0f84e-127">CLR は、通常 `IHostTaskManager::Sleep` 、 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> がユーザーコードから呼び出されたときにを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0f84e-127">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f84e-128">要件</span><span class="sxs-lookup"><span data-stu-id="0f84e-128">Requirements</span></span>  

 <span data-ttu-id="0f84e-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f84e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f84e-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0f84e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f84e-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0f84e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f84e-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f84e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f84e-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f84e-133">See also</span></span>

- [<span data-ttu-id="0f84e-134">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f84e-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="0f84e-135">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f84e-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="0f84e-136">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f84e-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="0f84e-137">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f84e-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

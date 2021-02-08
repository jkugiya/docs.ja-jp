---
description: '詳細について: IHostTaskManager:: SetUILocale メソッド'
title: IHostTaskManager::SetUILocale メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
ms.openlocfilehash: 0b81f127c6afb64670424a05db6cc57c4918396a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789386"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="eb2c4-103">IHostTaskManager::SetUILocale メソッド</span><span class="sxs-lookup"><span data-stu-id="eb2c4-103">IHostTaskManager::SetUILocale Method</span></span>

<span data-ttu-id="eb2c4-104">共通言語ランタイム (CLR) によって、現在実行中のタスクのユーザーインターフェイス (UI) ロケール (カルチャ) が変更されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-104">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2c4-105">構文</span><span class="sxs-lookup"><span data-stu-id="eb2c4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb2c4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb2c4-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="eb2c4-107">から新しく割り当てられた地理的カルチャおよび言語にマップされるロケール識別子の値。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb2c4-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="eb2c4-108">Return Value</span></span>  
  
|<span data-ttu-id="eb2c4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eb2c4-109">HRESULT</span></span>|<span data-ttu-id="eb2c4-110">説明</span><span class="sxs-lookup"><span data-stu-id="eb2c4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb2c4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eb2c4-111">S_OK</span></span>|<span data-ttu-id="eb2c4-112">`SetUILocale` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-112">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="eb2c4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eb2c4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eb2c4-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eb2c4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eb2c4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eb2c4-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-116">The call timed out.</span></span>|  
|<span data-ttu-id="eb2c4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eb2c4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eb2c4-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eb2c4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eb2c4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eb2c4-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eb2c4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eb2c4-121">E_FAIL</span></span>|<span data-ttu-id="eb2c4-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eb2c4-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eb2c4-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eb2c4-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="eb2c4-125">E_NOTIMPL</span></span>|<span data-ttu-id="eb2c4-126">ホストでは、マネージユーザーコードで UI カルチャを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-126">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb2c4-127">解説</span><span class="sxs-lookup"><span data-stu-id="eb2c4-127">Remarks</span></span>  

 <span data-ttu-id="eb2c4-128">ランタイムは、 `SetUILocale` プロパティの値 <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> がマネージコードによって変更されたときにを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-128">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="eb2c4-129">この方法を使用すると、ホストはロケールの同期に必要なメカニズムを実行できます。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-129">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="eb2c4-130">ホストで UI ロケールをマネージコードから変更できない場合、またはロケールを同期する機構を実装していない場合は、このメソッドから E_NOTIMPL が返されます。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-130">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb2c4-131">要件</span><span class="sxs-lookup"><span data-stu-id="eb2c4-131">Requirements</span></span>  

 <span data-ttu-id="eb2c4-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb2c4-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb2c4-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="eb2c4-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb2c4-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="eb2c4-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb2c4-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb2c4-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2c4-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb2c4-136">See also</span></span>

- [<span data-ttu-id="eb2c4-137">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb2c4-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="eb2c4-138">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb2c4-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="eb2c4-139">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb2c4-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="eb2c4-140">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb2c4-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="eb2c4-141">SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="eb2c4-141">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)

---
description: '詳細について: IHostTaskManager:: SetLocale メソッド'
title: IHostTaskManager::SetLocale メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: 522a3da9bcd8d61754684091f6de3f11f7ed478c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789412"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="0366a-103">IHostTaskManager::SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="0366a-103">IHostTaskManager::SetLocale Method</span></span>

<span data-ttu-id="0366a-104">共通言語ランタイム (CLR) によって、現在実行中のタスクのロケール (カルチャ) が変更されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="0366a-104">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0366a-105">構文</span><span class="sxs-lookup"><span data-stu-id="0366a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0366a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0366a-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="0366a-107">から新しく割り当てられた地理的カルチャおよび言語にマップされるロケール識別子の値。</span><span class="sxs-lookup"><span data-stu-id="0366a-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0366a-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0366a-108">Return Value</span></span>  
  
|<span data-ttu-id="0366a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0366a-109">HRESULT</span></span>|<span data-ttu-id="0366a-110">説明</span><span class="sxs-lookup"><span data-stu-id="0366a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0366a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0366a-111">S_OK</span></span>|<span data-ttu-id="0366a-112">`SetLocale` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="0366a-112">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="0366a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0366a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0366a-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="0366a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0366a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0366a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0366a-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0366a-116">The call timed out.</span></span>|  
|<span data-ttu-id="0366a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0366a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0366a-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0366a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0366a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0366a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0366a-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="0366a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0366a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0366a-121">E_FAIL</span></span>|<span data-ttu-id="0366a-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0366a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0366a-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="0366a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0366a-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="0366a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0366a-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0366a-125">E_NOTIMPL</span></span>|<span data-ttu-id="0366a-126">ホストでは、マネージユーザーコードでロケールを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="0366a-126">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0366a-127">解説</span><span class="sxs-lookup"><span data-stu-id="0366a-127">Remarks</span></span>  

 <span data-ttu-id="0366a-128">ランタイムは、 `SetLocale` プロパティの値 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> がマネージコードによって変更されたときにを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0366a-128">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="0366a-129">この方法を使用すると、ホストはロケールの同期に必要なメカニズムを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0366a-129">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="0366a-130">ホストでロケールをマネージコードから変更できない場合、またはロケールを同期する機構を実装していない場合は、このメソッドから E_NOTIMPL が返されます。</span><span class="sxs-lookup"><span data-stu-id="0366a-130">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0366a-131">要件</span><span class="sxs-lookup"><span data-stu-id="0366a-131">Requirements</span></span>  

 <span data-ttu-id="0366a-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0366a-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0366a-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0366a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0366a-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0366a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0366a-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0366a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0366a-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="0366a-136">See also</span></span>

- [<span data-ttu-id="0366a-137">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0366a-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="0366a-138">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0366a-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="0366a-139">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0366a-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="0366a-140">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0366a-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="0366a-141">SetUILocale メソッド</span><span class="sxs-lookup"><span data-stu-id="0366a-141">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)

---
description: '詳細について: IHostMemoryManager:: RegisterMemoryNotificationCallback メソッド'
title: IHostMemoryManager::RegisterMemoryNotificationCallback メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: 26a7468aba4f473eebff78a8c67eeb5b3e866e9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707764"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="3fb35-103">IHostMemoryManager::RegisterMemoryNotificationCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="3fb35-103">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>

<span data-ttu-id="3fb35-104">コンピューターの現在のメモリ負荷を共通言語ランタイム (CLR) に通知するために、ホストが呼び出すコールバック関数へのポインターを登録します。</span><span class="sxs-lookup"><span data-stu-id="3fb35-104">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb35-105">構文</span><span class="sxs-lookup"><span data-stu-id="3fb35-105">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fb35-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3fb35-106">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="3fb35-107">からCLR によって実装される [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) インスタンスへのインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="3fb35-107">[in] An interface pointer to an [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fb35-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3fb35-108">Return Value</span></span>  
  
|<span data-ttu-id="3fb35-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3fb35-109">HRESULT</span></span>|<span data-ttu-id="3fb35-110">説明</span><span class="sxs-lookup"><span data-stu-id="3fb35-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3fb35-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3fb35-111">S_OK</span></span>|<span data-ttu-id="3fb35-112">`RegisterMemoryNotificationCallback` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="3fb35-112">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="3fb35-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3fb35-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3fb35-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="3fb35-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3fb35-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3fb35-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3fb35-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3fb35-116">The call timed out.</span></span>|  
|<span data-ttu-id="3fb35-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3fb35-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3fb35-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3fb35-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3fb35-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3fb35-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3fb35-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="3fb35-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3fb35-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3fb35-121">E_FAIL</span></span>|<span data-ttu-id="3fb35-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3fb35-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3fb35-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3fb35-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3fb35-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="3fb35-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fb35-125">解説</span><span class="sxs-lookup"><span data-stu-id="3fb35-125">Remarks</span></span>  

 <span data-ttu-id="3fb35-126">インターフェイスで `ICLRMemoryNotificationCallback` 定義されるメソッドは1つだけであるため ([ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md))、 `pCallback` は `ICLRMemoryNotificationCallback` CLR によって提供されるインスタンスへのポインターであるため、コールバック関数自体に対して実際に登録が行われます。</span><span class="sxs-lookup"><span data-stu-id="3fb35-126">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="3fb35-127">ホストは、 `OnMemoryNotification` 標準の Win32 関数を使用するのではなく、メモリ不足状態を報告するためにを呼び出し `CreateMemoryResourceNotification` ます。</span><span class="sxs-lookup"><span data-stu-id="3fb35-127">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="3fb35-128">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fb35-128">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fb35-129">を呼び出しても `OnMemoryNotification` ブロックされません。</span><span class="sxs-lookup"><span data-stu-id="3fb35-129">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="3fb35-130">常に直ちに返されます。</span><span class="sxs-lookup"><span data-stu-id="3fb35-130">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fb35-131">要件</span><span class="sxs-lookup"><span data-stu-id="3fb35-131">Requirements</span></span>  

 <span data-ttu-id="3fb35-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fb35-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fb35-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3fb35-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3fb35-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3fb35-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fb35-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb35-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb35-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fb35-136">See also</span></span>

- [<span data-ttu-id="3fb35-137">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fb35-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="3fb35-138">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fb35-138">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)

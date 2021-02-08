---
description: '詳細については、次を参照してください: IHostSyncManager:: SetCLRSyncManager メソッド'
title: IHostSyncManager::SetCLRSyncManager メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: e2a6a54334f7b8a63696ead918f4f34e0c36e438
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784715"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="9cb0e-103">IHostSyncManager::SetCLRSyncManager メソッド</span><span class="sxs-lookup"><span data-stu-id="9cb0e-103">IHostSyncManager::SetCLRSyncManager Method</span></span>

<span data-ttu-id="9cb0e-104">現在の[IHostSyncManager](ihostsyncmanager-interface.md)インスタンスに関連付ける[ICLRSyncManager](iclrsyncmanager-interface.md)インスタンスを設定します。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-104">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb0e-105">構文</span><span class="sxs-lookup"><span data-stu-id="9cb0e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cb0e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9cb0e-106">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="9cb0e-107">から `ICLRSyncManager` 共通言語ランタイム (CLR) によって提供されるインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-107">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cb0e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="9cb0e-108">Return Value</span></span>  
  
|<span data-ttu-id="9cb0e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9cb0e-109">HRESULT</span></span>|<span data-ttu-id="9cb0e-110">説明</span><span class="sxs-lookup"><span data-stu-id="9cb0e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9cb0e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cb0e-111">S_OK</span></span>|<span data-ttu-id="9cb0e-112">`SetCLRSyncManager` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-112">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="9cb0e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9cb0e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9cb0e-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9cb0e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9cb0e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9cb0e-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-116">The call timed out.</span></span>|  
|<span data-ttu-id="9cb0e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9cb0e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9cb0e-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9cb0e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9cb0e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9cb0e-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9cb0e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9cb0e-121">E_FAIL</span></span>|<span data-ttu-id="9cb0e-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9cb0e-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9cb0e-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cb0e-125">解説</span><span class="sxs-lookup"><span data-stu-id="9cb0e-125">Remarks</span></span>  

 <span data-ttu-id="9cb0e-126">ホストと CLR の間の通信を容易にするために、ホストインターフェイスは通常、ペアになっています。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-126">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="9cb0e-127">ペアの1つのメンバーはホストによって実装され、もう一方のメンバーは CLR によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-127">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="9cb0e-128">ホスト側の実装として、 `IHostSyncManager` インターフェイスは、 `ICLRSyncManager` CLR によって実装されるインターフェイスに対応します。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-128">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="9cb0e-129">CLR は、を呼び出して、 `SetCLRSyncManager` `ICLRSyncManager` 現在のインスタンスに関連付けられているホストのインスタンスを指定 `IHostSyncManager` します。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-129">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cb0e-130">要件</span><span class="sxs-lookup"><span data-stu-id="9cb0e-130">Requirements</span></span>  

 <span data-ttu-id="9cb0e-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cb0e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb0e-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9cb0e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cb0e-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9cb0e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cb0e-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb0e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb0e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cb0e-135">See also</span></span>

- [<span data-ttu-id="9cb0e-136">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9cb0e-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="9cb0e-137">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9cb0e-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)

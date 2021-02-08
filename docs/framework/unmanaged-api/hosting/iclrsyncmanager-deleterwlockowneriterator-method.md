---
description: '詳細について: ICLRSyncManager::D eleteRWLockOwnerIterator メソッド'
title: ICLRSyncManager::DeleteRWLockOwnerIterator メソッド
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: 7968f326f1ad92fe6e3a0f91749fb7e462e81c04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789776"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="9eb33-103">ICLRSyncManager::DeleteRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="9eb33-103">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>

<span data-ttu-id="9eb33-104">[ICLRSyncManager:: CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)の呼び出しによって作成された反復子を、共通言語ランタイム (CLR) が破棄することを要求します。</span><span class="sxs-lookup"><span data-stu-id="9eb33-104">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eb33-105">構文</span><span class="sxs-lookup"><span data-stu-id="9eb33-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9eb33-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9eb33-106">Parameters</span></span>  

 `Iterator`  
 <span data-ttu-id="9eb33-107">からの呼び出しを使用して作成された反復子 `CreateRWLockOwnerIterator` 。</span><span class="sxs-lookup"><span data-stu-id="9eb33-107">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9eb33-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="9eb33-108">Return Value</span></span>  
  
|<span data-ttu-id="9eb33-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9eb33-109">HRESULT</span></span>|<span data-ttu-id="9eb33-110">説明</span><span class="sxs-lookup"><span data-stu-id="9eb33-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9eb33-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9eb33-111">S_OK</span></span>|<span data-ttu-id="9eb33-112">`DeleteRWLockOwnerIterator` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9eb33-112">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="9eb33-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9eb33-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9eb33-114">CLR がプロセスに読み込まれていないか、マネージコードを実行できないか、または呼び出しを正常に処理できない状態になっています。</span><span class="sxs-lookup"><span data-stu-id="9eb33-114">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="9eb33-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9eb33-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9eb33-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9eb33-116">The call timed out.</span></span>|  
|<span data-ttu-id="9eb33-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9eb33-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9eb33-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9eb33-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9eb33-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9eb33-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9eb33-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="9eb33-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9eb33-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9eb33-121">E_FAIL</span></span>|<span data-ttu-id="9eb33-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9eb33-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9eb33-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9eb33-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9eb33-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9eb33-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eb33-125">解説</span><span class="sxs-lookup"><span data-stu-id="9eb33-125">Remarks</span></span>  

 <span data-ttu-id="9eb33-126">ホストは、このメソッドを呼び出して、 `CreateRWLockOwnerIterator` スレッドの実装が同期された状態を維持することができます。</span><span class="sxs-lookup"><span data-stu-id="9eb33-126">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eb33-127">要件</span><span class="sxs-lookup"><span data-stu-id="9eb33-127">Requirements</span></span>  

 <span data-ttu-id="9eb33-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9eb33-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eb33-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9eb33-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9eb33-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9eb33-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9eb33-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eb33-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eb33-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="9eb33-132">See also</span></span>

- [<span data-ttu-id="9eb33-133">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9eb33-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="9eb33-134">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9eb33-134">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)

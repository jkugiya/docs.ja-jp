---
description: '詳細について: ICLRGCManager:: Collect メソッド'
title: ICLRGCManager::Collect メソッド
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
ms.openlocfilehash: 7c2649f7ce3472c504c1e48a203cf89d4b8508e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746062"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="5051c-103">ICLRGCManager::Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="5051c-103">ICLRGCManager::Collect Method</span></span>

<span data-ttu-id="5051c-104">指定したジェネレーションのガベージコレクションを強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="5051c-104">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5051c-105">構文</span><span class="sxs-lookup"><span data-stu-id="5051c-105">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5051c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5051c-106">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="5051c-107">から収集するジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="5051c-107">[in] The generation to collect.</span></span> <span data-ttu-id="5051c-108">値が-1 の場合は、すべてのジェネレーションのコレクションが強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="5051c-108">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5051c-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="5051c-109">Return Value</span></span>  
  
|<span data-ttu-id="5051c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5051c-110">HRESULT</span></span>|<span data-ttu-id="5051c-111">説明</span><span class="sxs-lookup"><span data-stu-id="5051c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5051c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5051c-112">S_OK</span></span>|<span data-ttu-id="5051c-113">`Collect` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="5051c-113">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="5051c-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5051c-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5051c-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="5051c-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5051c-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5051c-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5051c-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5051c-117">The call timed out.</span></span>|  
|<span data-ttu-id="5051c-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5051c-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5051c-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5051c-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5051c-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5051c-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5051c-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="5051c-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5051c-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5051c-122">E_FAIL</span></span>|<span data-ttu-id="5051c-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5051c-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5051c-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5051c-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5051c-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="5051c-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5051c-126">解説</span><span class="sxs-lookup"><span data-stu-id="5051c-126">Remarks</span></span>  

 <span data-ttu-id="5051c-127">メソッドは、 `Collect` 現在の状態に関係なく、CLR のガベージコレクターがコレクションを実行するように強制します。</span><span class="sxs-lookup"><span data-stu-id="5051c-127">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5051c-128">要件</span><span class="sxs-lookup"><span data-stu-id="5051c-128">Requirements</span></span>  

 <span data-ttu-id="5051c-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5051c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5051c-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5051c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5051c-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5051c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5051c-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5051c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5051c-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="5051c-133">See also</span></span>

- [<span data-ttu-id="5051c-134">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="5051c-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="5051c-135">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="5051c-135">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="5051c-136">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5051c-136">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="5051c-137">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5051c-137">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="5051c-138">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5051c-138">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="5051c-139">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5051c-139">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="5051c-140">ホスティング</span><span class="sxs-lookup"><span data-stu-id="5051c-140">Hosting</span></span>](index.md)

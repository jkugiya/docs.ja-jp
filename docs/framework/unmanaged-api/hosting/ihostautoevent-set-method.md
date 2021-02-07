---
description: '詳細情報: IHostAutoEvent:: Set メソッド'
title: IHostAutoEvent::Set メソッド
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
ms.openlocfilehash: e4ba63b5250a383431e410cd6e552f8344fedf5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708919"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="56782-103">IHostAutoEvent::Set メソッド</span><span class="sxs-lookup"><span data-stu-id="56782-103">IHostAutoEvent::Set Method</span></span>

<span data-ttu-id="56782-104">現在の [IHostAutoEvent](ihostautoevent-interface.md) インスタンスをシグナル状態に設定します。</span><span class="sxs-lookup"><span data-stu-id="56782-104">Sets the current [IHostAutoEvent](ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56782-105">構文</span><span class="sxs-lookup"><span data-stu-id="56782-105">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="56782-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="56782-106">Return Value</span></span>  
  
|<span data-ttu-id="56782-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56782-107">HRESULT</span></span>|<span data-ttu-id="56782-108">説明</span><span class="sxs-lookup"><span data-stu-id="56782-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56782-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="56782-109">S_OK</span></span>|<span data-ttu-id="56782-110">`Set` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="56782-110">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="56782-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="56782-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="56782-112">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="56782-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="56782-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="56782-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="56782-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="56782-114">The call timed out.</span></span>|  
|<span data-ttu-id="56782-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="56782-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="56782-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="56782-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="56782-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="56782-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="56782-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="56782-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="56782-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="56782-119">E_FAIL</span></span>|<span data-ttu-id="56782-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="56782-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="56782-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="56782-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="56782-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="56782-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56782-123">要件</span><span class="sxs-lookup"><span data-stu-id="56782-123">Requirements</span></span>  

 <span data-ttu-id="56782-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56782-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56782-125">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="56782-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56782-126">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="56782-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56782-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56782-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56782-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="56782-128">See also</span></span>

- [<span data-ttu-id="56782-129">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56782-129">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="56782-130">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56782-130">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="56782-131">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56782-131">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="56782-132">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56782-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)

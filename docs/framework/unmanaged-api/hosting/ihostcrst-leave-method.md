---
description: '詳細について: IHostCrst:: Leave メソッド'
title: IHostCrst::Leave メソッド
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
ms.openlocfilehash: b00e62c7b2683ab6024a7c9b8de4645ceb59fb02
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708841"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="14d5f-103">IHostCrst::Leave メソッド</span><span class="sxs-lookup"><span data-stu-id="14d5f-103">IHostCrst::Leave Method</span></span>

<span data-ttu-id="14d5f-104">[IHostCrst](ihostcrst-interface.md)の現在のインスタンスによって表されるクリティカルセクションを残します。</span><span class="sxs-lookup"><span data-stu-id="14d5f-104">Leaves the critical section that is represented by the current instance of [IHostCrst](ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14d5f-105">構文</span><span class="sxs-lookup"><span data-stu-id="14d5f-105">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="14d5f-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="14d5f-106">Return Value</span></span>  
  
|<span data-ttu-id="14d5f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14d5f-107">HRESULT</span></span>|<span data-ttu-id="14d5f-108">説明</span><span class="sxs-lookup"><span data-stu-id="14d5f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14d5f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="14d5f-109">S_OK</span></span>|<span data-ttu-id="14d5f-110">`Leave` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="14d5f-110">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="14d5f-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="14d5f-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="14d5f-112">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="14d5f-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="14d5f-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="14d5f-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="14d5f-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="14d5f-114">The call timed out.</span></span>|  
|<span data-ttu-id="14d5f-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="14d5f-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="14d5f-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="14d5f-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="14d5f-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="14d5f-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="14d5f-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="14d5f-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="14d5f-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="14d5f-119">E_FAIL</span></span>|<span data-ttu-id="14d5f-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="14d5f-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="14d5f-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="14d5f-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="14d5f-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="14d5f-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14d5f-123">解説</span><span class="sxs-lookup"><span data-stu-id="14d5f-123">Remarks</span></span>  

 <span data-ttu-id="14d5f-124">`Leave` 対応する Win32 関数を使用するのではなく、CLR がホストのスレッド実装と直接通信できるようにし `LeaveCriticalSection` ます。</span><span class="sxs-lookup"><span data-stu-id="14d5f-124">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="14d5f-125">現在のインスタンスによって表されるクリティカルセクションの所有権を取得するスレッドは、 `IHostCrst` `Leave` そのクリティカルセクションに入るたびに1回呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="14d5f-125">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14d5f-126">要件</span><span class="sxs-lookup"><span data-stu-id="14d5f-126">Requirements</span></span>  

 <span data-ttu-id="14d5f-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14d5f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14d5f-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="14d5f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14d5f-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="14d5f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14d5f-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14d5f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d5f-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="14d5f-131">See also</span></span>

- [<span data-ttu-id="14d5f-132">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="14d5f-132">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="14d5f-133">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="14d5f-133">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="14d5f-134">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="14d5f-134">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)

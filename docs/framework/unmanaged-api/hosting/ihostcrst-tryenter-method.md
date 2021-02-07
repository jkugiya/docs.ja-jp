---
description: '詳細について: IHostCrst:: TryEnter メソッド'
title: IHostCrst::TryEnter メソッド
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
ms.openlocfilehash: 59c632b7c9edd422e2ceee1e0526a7bb077759a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708724"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="ad53f-103">IHostCrst::TryEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="ad53f-103">IHostCrst::TryEnter Method</span></span>

<span data-ttu-id="ad53f-104">現在の [IHostCrst](ihostcrst-interface.md) インスタンスによって表されるクリティカルセクションへの入力を試みます。</span><span class="sxs-lookup"><span data-stu-id="ad53f-104">Attempts to enter the critical section represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad53f-105">構文</span><span class="sxs-lookup"><span data-stu-id="ad53f-105">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad53f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad53f-106">Parameters</span></span>  

 `option`  
 <span data-ttu-id="ad53f-107">から [WAIT_OPTION](wait-option-enumeration.md) 値の1つ。操作がブロックされた場合にホストが実行するアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="ad53f-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="ad53f-108">[出力] `true` クリティカルセクションを入力できる場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="ad53f-108">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad53f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad53f-109">Return Value</span></span>  
  
|<span data-ttu-id="ad53f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad53f-110">HRESULT</span></span>|<span data-ttu-id="ad53f-111">説明</span><span class="sxs-lookup"><span data-stu-id="ad53f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad53f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad53f-112">S_OK</span></span>|<span data-ttu-id="ad53f-113">`TryEnter` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="ad53f-113">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="ad53f-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ad53f-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ad53f-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="ad53f-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ad53f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ad53f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ad53f-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ad53f-117">The call timed out.</span></span>|  
|<span data-ttu-id="ad53f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ad53f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ad53f-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ad53f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ad53f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ad53f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ad53f-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="ad53f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ad53f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ad53f-122">E_FAIL</span></span>|<span data-ttu-id="ad53f-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ad53f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ad53f-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ad53f-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ad53f-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="ad53f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad53f-126">解説</span><span class="sxs-lookup"><span data-stu-id="ad53f-126">Remarks</span></span>  

 <span data-ttu-id="ad53f-127">`TryEnter` を直ちに返し、呼び出し元のスレッドがクリティカルセクションに入ったかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ad53f-127">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="ad53f-128">このメソッドは、Wind32 関数をミラー化 `TryEnterCriticalSection` します。</span><span class="sxs-lookup"><span data-stu-id="ad53f-128">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad53f-129">要件</span><span class="sxs-lookup"><span data-stu-id="ad53f-129">Requirements</span></span>  

 <span data-ttu-id="ad53f-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad53f-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad53f-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ad53f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad53f-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ad53f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad53f-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad53f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad53f-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad53f-134">See also</span></span>

- [<span data-ttu-id="ad53f-135">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad53f-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="ad53f-136">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad53f-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="ad53f-137">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad53f-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)

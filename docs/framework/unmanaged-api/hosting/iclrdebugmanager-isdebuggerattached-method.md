---
description: '詳細情報: ICLRDebugManager:: Isデバッガ添付メソッド'
title: ICLRDebugManager::IsDebuggerAttached メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
ms.openlocfilehash: 74305989797bcb553feb727a133e24bd308ac715
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772134"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="322df-103">ICLRDebugManager::IsDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="322df-103">ICLRDebugManager::IsDebuggerAttached Method</span></span>

<span data-ttu-id="322df-104">デバッガーがプロセスにアタッチされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="322df-104">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="322df-105">構文</span><span class="sxs-lookup"><span data-stu-id="322df-105">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="322df-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="322df-106">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="322df-107">[出力] `true` デバッガーがプロセスにアタッチされている場合は、それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="322df-107">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="322df-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="322df-108">Return Value</span></span>  
  
|<span data-ttu-id="322df-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="322df-109">HRESULT</span></span>|<span data-ttu-id="322df-110">説明</span><span class="sxs-lookup"><span data-stu-id="322df-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="322df-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="322df-111">S_OK</span></span>|<span data-ttu-id="322df-112">`IsDebuggerAttached` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="322df-112">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="322df-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="322df-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="322df-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="322df-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="322df-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="322df-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="322df-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="322df-116">The call timed out.</span></span>|  
|<span data-ttu-id="322df-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="322df-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="322df-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="322df-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="322df-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="322df-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="322df-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="322df-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="322df-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="322df-121">E_FAIL</span></span>|<span data-ttu-id="322df-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="322df-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="322df-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="322df-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="322df-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="322df-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="322df-125">解説</span><span class="sxs-lookup"><span data-stu-id="322df-125">Remarks</span></span>  

 <span data-ttu-id="322df-126">`IsDebuggerAttached` デバッガーがプロセスにアタッチされているかどうかを判断するために、ホストが CLR を照会できるようにします。</span><span class="sxs-lookup"><span data-stu-id="322df-126">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="322df-127">要件</span><span class="sxs-lookup"><span data-stu-id="322df-127">Requirements</span></span>  

 <span data-ttu-id="322df-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="322df-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="322df-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="322df-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="322df-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="322df-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="322df-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="322df-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="322df-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="322df-132">See also</span></span>

- [<span data-ttu-id="322df-133">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="322df-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="322df-134">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="322df-134">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="322df-135">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="322df-135">IHostControl Interface</span></span>](ihostcontrol-interface.md)

---
description: '詳細については、次を参照してください: Ihohoo参照マネージャー:: Closeioて Port メソッド'
title: IHostIoCompletionManager::CloseIoCompletionPort メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
ms.openlocfilehash: 987b9f4e0fa22fa977fa1b14c77c8c0381e3e399
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728510"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="bdb80-103">IHostIoCompletionManager::CloseIoCompletionPort メソッド</span><span class="sxs-lookup"><span data-stu-id="bdb80-103">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>

<span data-ttu-id="bdb80-104">[CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)の以前の呼び出しで開かれたポートをホストが閉じることを要求します。</span><span class="sxs-lookup"><span data-stu-id="bdb80-104">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb80-105">構文</span><span class="sxs-lookup"><span data-stu-id="bdb80-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdb80-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bdb80-106">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="bdb80-107">から閉じるポートのハンドル。</span><span class="sxs-lookup"><span data-stu-id="bdb80-107">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bdb80-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bdb80-108">Return Value</span></span>  
  
|<span data-ttu-id="bdb80-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bdb80-109">HRESULT</span></span>|<span data-ttu-id="bdb80-110">説明</span><span class="sxs-lookup"><span data-stu-id="bdb80-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bdb80-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bdb80-111">S_OK</span></span>|<span data-ttu-id="bdb80-112">`CloseIoCompletionPort` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="bdb80-112">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="bdb80-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bdb80-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bdb80-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="bdb80-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bdb80-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bdb80-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bdb80-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bdb80-116">The call timed out.</span></span>|  
|<span data-ttu-id="bdb80-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bdb80-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bdb80-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bdb80-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bdb80-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bdb80-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bdb80-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="bdb80-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bdb80-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bdb80-121">E_FAIL</span></span>|<span data-ttu-id="bdb80-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bdb80-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bdb80-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bdb80-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bdb80-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="bdb80-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bdb80-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bdb80-125">E_INVALIDARG</span></span>|<span data-ttu-id="bdb80-126">無効なポートハンドルが渡されました。</span><span class="sxs-lookup"><span data-stu-id="bdb80-126">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdb80-127">解説</span><span class="sxs-lookup"><span data-stu-id="bdb80-127">Remarks</span></span>  

 <span data-ttu-id="bdb80-128">`hPort` は、の以前の呼び出しによって作成されたポートへのハンドルである必要があり `CreateIoCompletionPort` ます。</span><span class="sxs-lookup"><span data-stu-id="bdb80-128">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdb80-129">要件</span><span class="sxs-lookup"><span data-stu-id="bdb80-129">Requirements</span></span>  

 <span data-ttu-id="bdb80-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdb80-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdb80-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bdb80-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bdb80-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bdb80-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bdb80-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdb80-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb80-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdb80-134">See also</span></span>

- [<span data-ttu-id="bdb80-135">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bdb80-135">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="bdb80-136">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bdb80-136">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)

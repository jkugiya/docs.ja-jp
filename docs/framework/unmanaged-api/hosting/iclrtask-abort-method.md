---
description: '詳細について: ICLRTask:: Abort メソッド'
title: ICLRTask::Abort メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
ms.openlocfilehash: ddb761ac50d7401180355236aa8fdc22cca1c580
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785007"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="f57a5-103">ICLRTask::Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="f57a5-103">ICLRTask::Abort Method</span></span>

<span data-ttu-id="f57a5-104">現在の [ICLRTask](iclrtask-interface.md) インスタンスが表すタスクを共通言語ランタイム (CLR) が中止することを要求します。</span><span class="sxs-lookup"><span data-stu-id="f57a5-104">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57a5-105">構文</span><span class="sxs-lookup"><span data-stu-id="f57a5-105">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f57a5-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="f57a5-106">Return Value</span></span>  
  
|<span data-ttu-id="f57a5-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f57a5-107">HRESULT</span></span>|<span data-ttu-id="f57a5-108">説明</span><span class="sxs-lookup"><span data-stu-id="f57a5-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f57a5-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="f57a5-109">S_OK</span></span>|<span data-ttu-id="f57a5-110">`Abort` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f57a5-110">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="f57a5-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f57a5-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f57a5-112">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f57a5-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f57a5-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f57a5-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f57a5-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f57a5-114">The call timed out.</span></span>|  
|<span data-ttu-id="f57a5-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f57a5-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f57a5-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f57a5-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f57a5-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f57a5-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f57a5-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f57a5-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f57a5-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f57a5-119">E_FAIL</span></span>|<span data-ttu-id="f57a5-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f57a5-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f57a5-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f57a5-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f57a5-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f57a5-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f57a5-123">解説</span><span class="sxs-lookup"><span data-stu-id="f57a5-123">Remarks</span></span>  

 <span data-ttu-id="f57a5-124">CLR は、 <xref:System.Threading.ThreadAbortException> ホストがを呼び出したときにを発生させ `Abort` ます。</span><span class="sxs-lookup"><span data-stu-id="f57a5-124">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="f57a5-125">ファイナライザーや例外処理機構などのユーザーコードが実行されるのを待たずに、例外情報が初期化された直後に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="f57a5-125">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="f57a5-126">を呼び出すと、が `Abort` すぐに返されます。</span><span class="sxs-lookup"><span data-stu-id="f57a5-126">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f57a5-127">要件</span><span class="sxs-lookup"><span data-stu-id="f57a5-127">Requirements</span></span>  

 <span data-ttu-id="f57a5-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f57a5-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f57a5-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f57a5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f57a5-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f57a5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f57a5-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f57a5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57a5-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="f57a5-132">See also</span></span>

- [<span data-ttu-id="f57a5-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f57a5-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f57a5-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f57a5-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f57a5-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f57a5-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f57a5-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f57a5-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

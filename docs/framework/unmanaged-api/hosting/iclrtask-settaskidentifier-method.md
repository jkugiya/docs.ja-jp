---
description: '次の詳細情報: ICLRTask:: SetTaskIdentifier メソッド'
title: ICLRTask::SetTaskIdentifier メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
ms.openlocfilehash: e746d8ec96d16f7761dd49ac814ddbed073c2686
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784952"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="bbbc8-103">ICLRTask::SetTaskIdentifier メソッド</span><span class="sxs-lookup"><span data-stu-id="bbbc8-103">ICLRTask::SetTaskIdentifier Method</span></span>

<span data-ttu-id="bbbc8-104">共通言語ランタイム (CLR) に対して、指定された識別子の値を現在の [ICLRTask](iclrtask-interface.md) インスタンスによって表されるタスクに関連付けるように指示します。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-104">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbbc8-105">構文</span><span class="sxs-lookup"><span data-stu-id="bbbc8-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbbc8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bbbc8-106">Parameters</span></span>  

 `Asked`  
 <span data-ttu-id="bbbc8-107">から現在のインスタンスによって表されるタスクに関連付ける共通言語ランタイムの一意の識別子 `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-107">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbbc8-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bbbc8-108">Return Value</span></span>  
  
|<span data-ttu-id="bbbc8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bbbc8-109">HRESULT</span></span>|<span data-ttu-id="bbbc8-110">説明</span><span class="sxs-lookup"><span data-stu-id="bbbc8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbbc8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbbc8-111">S_OK</span></span>|<span data-ttu-id="bbbc8-112">`SetTaskIdentifier` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-112">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="bbbc8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bbbc8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bbbc8-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bbbc8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bbbc8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bbbc8-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-116">The call timed out.</span></span>|  
|<span data-ttu-id="bbbc8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bbbc8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bbbc8-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bbbc8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bbbc8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bbbc8-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bbbc8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bbbc8-121">E_FAIL</span></span>|<span data-ttu-id="bbbc8-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bbbc8-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bbbc8-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbbc8-125">解説</span><span class="sxs-lookup"><span data-stu-id="bbbc8-125">Remarks</span></span>  

 <span data-ttu-id="bbbc8-126">ホストは、デバッグ環境で CLR とホストを統合できるように、識別子をタスクに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-126">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="bbbc8-127">この識別子は、CLR には意味がありません。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-127">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="bbbc8-128">CLR はこれをデバッガーアプリケーションに渡します。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-128">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="bbbc8-129">デバッガーはこの識別子を使用して、CLR 呼び出し履歴をホストの呼び出し履歴に関連付けて、デバッガーのユーザーインターフェイスに表示されたときに、それぞれのトレース情報を統合できるようにします。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-129">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbbc8-130">要件</span><span class="sxs-lookup"><span data-stu-id="bbbc8-130">Requirements</span></span>  

 <span data-ttu-id="bbbc8-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbbc8-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbbc8-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bbbc8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbbc8-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bbbc8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbbc8-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbbc8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbc8-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbbc8-135">See also</span></span>

- [<span data-ttu-id="bbbc8-136">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbbc8-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="bbbc8-137">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbbc8-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="bbbc8-138">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbbc8-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="bbbc8-139">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbbc8-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

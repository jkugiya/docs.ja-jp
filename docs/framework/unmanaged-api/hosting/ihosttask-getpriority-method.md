---
description: '次の情報を参照してください: IHostTask:: GetPriority メソッド'
title: IHostTask::GetPriority メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
ms.openlocfilehash: fb64164a54806a362888e93f031713ccc0ac3578
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784692"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="bb130-103">IHostTask::GetPriority メソッド</span><span class="sxs-lookup"><span data-stu-id="bb130-103">IHostTask::GetPriority Method</span></span>

<span data-ttu-id="bb130-104">現在の [IHostTask](ihosttask-interface.md) インスタンスによって表されるタスクのスレッド優先度レベルを取得します。</span><span class="sxs-lookup"><span data-stu-id="bb130-104">Gets the thread priority level of the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb130-105">構文</span><span class="sxs-lookup"><span data-stu-id="bb130-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb130-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb130-106">Parameters</span></span>  

 `pPriority`  
 <span data-ttu-id="bb130-107">入出力現在のインスタンスによって表されるタスクのスレッド優先度レベルを示す整数を指すポインターです `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="bb130-107">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb130-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bb130-108">Return Value</span></span>  
  
|<span data-ttu-id="bb130-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb130-109">HRESULT</span></span>|<span data-ttu-id="bb130-110">説明</span><span class="sxs-lookup"><span data-stu-id="bb130-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb130-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb130-111">S_OK</span></span>|<span data-ttu-id="bb130-112">`GetPriority` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="bb130-112">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="bb130-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb130-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb130-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="bb130-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bb130-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb130-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb130-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bb130-116">The call timed out.</span></span>|  
|<span data-ttu-id="bb130-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb130-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb130-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bb130-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb130-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb130-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb130-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="bb130-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb130-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb130-121">E_FAIL</span></span>|<span data-ttu-id="bb130-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bb130-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb130-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bb130-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb130-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="bb130-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb130-125">解説</span><span class="sxs-lookup"><span data-stu-id="bb130-125">Remarks</span></span>  

 <span data-ttu-id="bb130-126">スレッドの優先度レベルの値は、Win32 関数によって定義され `SetThreadPriority` ます。</span><span class="sxs-lookup"><span data-stu-id="bb130-126">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb130-127">要件</span><span class="sxs-lookup"><span data-stu-id="bb130-127">Requirements</span></span>  

 <span data-ttu-id="bb130-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb130-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb130-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bb130-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb130-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bb130-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb130-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb130-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb130-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb130-132">See also</span></span>

- [<span data-ttu-id="bb130-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb130-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="bb130-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb130-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="bb130-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb130-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="bb130-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb130-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

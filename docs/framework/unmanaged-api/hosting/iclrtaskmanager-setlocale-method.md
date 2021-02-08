---
description: '詳細について: ICLRTaskManager:: SetLocale メソッド'
title: ICLRTaskManager::SetLocale メソッド
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
ms.openlocfilehash: 401f227f900ab4b89cd6fc5b7902b4314a7687e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799477"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="5bc9b-103">ICLRTaskManager::SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="5bc9b-103">ICLRTaskManager::SetLocale Method</span></span>

<span data-ttu-id="5bc9b-104">現在実行中のタスクのロケール識別子 (地理的なカルチャおよび言語にマップされる) の値がホストによって変更されたことを、共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-104">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc9b-105">構文</span><span class="sxs-lookup"><span data-stu-id="5bc9b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc9b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5bc9b-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="5bc9b-107">から新しく割り当てられた地理的カルチャおよび言語にマップされるロケール識別子の値。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bc9b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="5bc9b-108">Return Value</span></span>  
  
|<span data-ttu-id="5bc9b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5bc9b-109">HRESULT</span></span>|<span data-ttu-id="5bc9b-110">説明</span><span class="sxs-lookup"><span data-stu-id="5bc9b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5bc9b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5bc9b-111">S_OK</span></span>|<span data-ttu-id="5bc9b-112">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="5bc9b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5bc9b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5bc9b-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5bc9b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5bc9b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5bc9b-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-116">The call timed out.</span></span>|  
|<span data-ttu-id="5bc9b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5bc9b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5bc9b-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5bc9b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5bc9b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5bc9b-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5bc9b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5bc9b-121">E_FAIL</span></span>|<span data-ttu-id="5bc9b-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5bc9b-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5bc9b-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bc9b-125">解説</span><span class="sxs-lookup"><span data-stu-id="5bc9b-125">Remarks</span></span>  

 <span data-ttu-id="5bc9b-126">`SetLocale` ホストに、ロケールの同期に必要なメカニズムを実行する機会を与えます。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-126">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc9b-127">要件</span><span class="sxs-lookup"><span data-stu-id="5bc9b-127">Requirements</span></span>  

 <span data-ttu-id="5bc9b-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bc9b-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc9b-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5bc9b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5bc9b-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5bc9b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bc9b-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc9b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc9b-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bc9b-132">See also</span></span>

- [<span data-ttu-id="5bc9b-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bc9b-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5bc9b-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bc9b-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5bc9b-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bc9b-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5bc9b-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bc9b-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

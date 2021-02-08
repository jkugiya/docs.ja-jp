---
description: '詳細について: IHostCrst:: Enter メソッド'
title: IHostCrst::Enter メソッド
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
ms.openlocfilehash: ef8e4ce71cde75fe6b834802b08d22aedbd6fab9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789451"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="ba2e9-103">IHostCrst::Enter メソッド</span><span class="sxs-lookup"><span data-stu-id="ba2e9-103">IHostCrst::Enter Method</span></span>

<span data-ttu-id="ba2e9-104">現在の [IHostCrst](ihostcrst-interface.md) インスタンスによって表されるクリティカルセクションを入力します。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-104">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba2e9-105">構文</span><span class="sxs-lookup"><span data-stu-id="ba2e9-105">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba2e9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ba2e9-106">Parameters</span></span>  

 `option`  
 <span data-ttu-id="ba2e9-107">から [WAIT_OPTION](wait-option-enumeration.md) 値の1つ。操作がブロックされた場合にホストが実行するアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba2e9-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ba2e9-108">Return Value</span></span>  
  
|<span data-ttu-id="ba2e9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ba2e9-109">HRESULT</span></span>|<span data-ttu-id="ba2e9-110">説明</span><span class="sxs-lookup"><span data-stu-id="ba2e9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ba2e9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ba2e9-111">S_OK</span></span>|<span data-ttu-id="ba2e9-112">`Enter` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-112">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="ba2e9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ba2e9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ba2e9-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ba2e9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ba2e9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ba2e9-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-116">The call timed out.</span></span>|  
|<span data-ttu-id="ba2e9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ba2e9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ba2e9-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ba2e9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ba2e9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ba2e9-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ba2e9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ba2e9-121">E_FAIL</span></span>|<span data-ttu-id="ba2e9-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ba2e9-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ba2e9-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba2e9-125">解説</span><span class="sxs-lookup"><span data-stu-id="ba2e9-125">Remarks</span></span>  

 <span data-ttu-id="ba2e9-126">`Enter` Win32 関数をミラー化 `EnterCriticalSection` します。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-126">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba2e9-127">このメソッドは、クリティカルセクションが入力されるまでを返しません。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-127">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba2e9-128">要件</span><span class="sxs-lookup"><span data-stu-id="ba2e9-128">Requirements</span></span>  

 <span data-ttu-id="ba2e9-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba2e9-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba2e9-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ba2e9-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba2e9-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ba2e9-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba2e9-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba2e9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba2e9-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba2e9-133">See also</span></span>

- [<span data-ttu-id="ba2e9-134">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ba2e9-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="ba2e9-135">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ba2e9-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="ba2e9-136">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ba2e9-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)

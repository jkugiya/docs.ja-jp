---
description: '詳細については、次を参照してください: ICLROnEventManager:: UnregisterActionOnEvent メソッド'
title: ICLROnEventManager::UnregisterActionOnEvent メソッド
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
ms.openlocfilehash: 8131c58669ff7be0fdc2b2e063c70d3b370921e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789815"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="f82c9-103">ICLROnEventManager::UnregisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="f82c9-103">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>

<span data-ttu-id="f82c9-104">指定されたイベントに対して、以前に登録されたコールバックポインターの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="f82c9-104">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82c9-105">構文</span><span class="sxs-lookup"><span data-stu-id="f82c9-105">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f82c9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f82c9-106">Parameters</span></span>  

 `event`  
 <span data-ttu-id="f82c9-107">から [Eclrevent](eclrevent-enumeration.md) 値の1つ。によって記述されたコールバックポインターの登録を解除する対象のイベントを示し `pAction` ます。</span><span class="sxs-lookup"><span data-stu-id="f82c9-107">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="f82c9-108">から[Registeractiononevent](iclroneventmanager-registeractiononevent-method.md)メソッドにパラメーターとして渡された[Iactiononclrevent](iactiononclrevent-interface.md)オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f82c9-108">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f82c9-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f82c9-109">Return Value</span></span>  
  
|<span data-ttu-id="f82c9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f82c9-110">HRESULT</span></span>|<span data-ttu-id="f82c9-111">説明</span><span class="sxs-lookup"><span data-stu-id="f82c9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f82c9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f82c9-112">S_OK</span></span>|<span data-ttu-id="f82c9-113">`UnregisterActionOnEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f82c9-113">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="f82c9-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f82c9-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f82c9-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f82c9-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f82c9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f82c9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f82c9-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f82c9-117">The call timed out.</span></span>|  
|<span data-ttu-id="f82c9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f82c9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f82c9-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f82c9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f82c9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f82c9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f82c9-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f82c9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f82c9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f82c9-122">E_FAIL</span></span>|<span data-ttu-id="f82c9-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f82c9-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f82c9-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f82c9-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f82c9-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f82c9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f82c9-126">要件</span><span class="sxs-lookup"><span data-stu-id="f82c9-126">Requirements</span></span>  

 <span data-ttu-id="f82c9-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f82c9-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f82c9-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f82c9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f82c9-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f82c9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f82c9-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f82c9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82c9-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="f82c9-131">See also</span></span>

- [<span data-ttu-id="f82c9-132">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="f82c9-132">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="f82c9-133">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f82c9-133">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="f82c9-134">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f82c9-134">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="f82c9-135">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f82c9-135">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)

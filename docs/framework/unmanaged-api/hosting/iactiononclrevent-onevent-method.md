---
description: '詳細については、次を参照してください: IActionOnCLREvent:: OnEvent メソッド'
title: IActionOnCLREvent::OnEvent メソッド
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
ms.openlocfilehash: 163956ab319eb34d58da23d2c4ef2a6b592aab0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785141"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="a622e-103">IActionOnCLREvent::OnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="a622e-103">IActionOnCLREvent::OnEvent Method</span></span>

<span data-ttu-id="a622e-104">[ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)メソッドの呼び出しを使用して登録されたイベントに対してコールバックを実行します。</span><span class="sxs-lookup"><span data-stu-id="a622e-104">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a622e-105">構文</span><span class="sxs-lookup"><span data-stu-id="a622e-105">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a622e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a622e-106">Parameters</span></span>  

 `event`  
 <span data-ttu-id="a622e-107">からイベントの種類を示す、 [Eclrevent](eclrevent-enumeration.md) の値の1つ。</span><span class="sxs-lookup"><span data-stu-id="a622e-107">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="a622e-108">からの詳細を格納しているオブジェクトへのポインター `event` 。</span><span class="sxs-lookup"><span data-stu-id="a622e-108">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a622e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="a622e-109">Return Value</span></span>  
  
|<span data-ttu-id="a622e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a622e-110">HRESULT</span></span>|<span data-ttu-id="a622e-111">説明</span><span class="sxs-lookup"><span data-stu-id="a622e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a622e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a622e-112">S_OK</span></span>|<span data-ttu-id="a622e-113">`OnEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="a622e-113">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="a622e-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a622e-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a622e-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="a622e-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a622e-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a622e-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a622e-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a622e-117">The call timed out.</span></span>|  
|<span data-ttu-id="a622e-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a622e-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a622e-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a622e-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a622e-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a622e-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a622e-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="a622e-121">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a622e-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a622e-122">E_FAIL</span></span>|<span data-ttu-id="a622e-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a622e-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a622e-124">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a622e-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a622e-125">後続のホストメソッドを呼び出すと HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="a622e-125">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a622e-126">解説</span><span class="sxs-lookup"><span data-stu-id="a622e-126">Remarks</span></span>  

 <span data-ttu-id="a622e-127">`data`パラメーターが、指定されていない型のオブジェクトへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="a622e-127">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="a622e-128">`event`パラメーターがの場合 `Event_DomainUnload` 、 `data` は、 <xref:System.AppDomain> アンロードされたの数値識別子です。</span><span class="sxs-lookup"><span data-stu-id="a622e-128">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="a622e-129">ホストは、この識別子をキーとして使用して適切なアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a622e-129">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="a622e-130">がの場合 `event` `Event_MDAFired` 、 `data` はマネージデバッグアシスタント (MDA) からのメッセージ出力を格納する [MDAInfo](mdainfo-structure.md) インスタンスへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="a622e-130">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="a622e-131">Mda は、開発者がデバッグを支援する CLR の機能です。これは、特にトラップが困難なイベントに関する XML メッセージを生成することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="a622e-131">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="a622e-132">このようなメッセージは、マネージコードとアンマネージコードの間の遷移をデバッグする場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a622e-132">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="a622e-133">詳細については、「 [マネージデバッグアシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a622e-133">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a622e-134">要件</span><span class="sxs-lookup"><span data-stu-id="a622e-134">Requirements</span></span>  

 <span data-ttu-id="a622e-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a622e-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a622e-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a622e-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a622e-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a622e-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a622e-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a622e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a622e-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="a622e-139">See also</span></span>

- [<span data-ttu-id="a622e-140">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="a622e-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a622e-141">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="a622e-141">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="a622e-142">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a622e-142">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="a622e-143">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a622e-143">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a622e-144">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a622e-144">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="a622e-145">MDAInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="a622e-145">MDAInfo Structure</span></span>](mdainfo-structure.md)

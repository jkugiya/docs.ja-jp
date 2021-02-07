---
description: '詳細について: ICLRPolicyManager:: SetActionOnTimeout メソッド'
title: ICLRPolicyManager::SetActionOnTimeout メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: d682acd49bdc4fa0f8c58a1300e2215816fe2718
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689028"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="bfbf1-103">ICLRPolicyManager::SetActionOnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="bfbf1-103">ICLRPolicyManager::SetActionOnTimeout Method</span></span>

<span data-ttu-id="bfbf1-104">指定された操作がタイムアウトしたときに共通言語ランタイム (CLR) が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-104">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfbf1-105">構文</span><span class="sxs-lookup"><span data-stu-id="bfbf1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfbf1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bfbf1-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="bfbf1-107">からタイムアウトアクションを指定する操作を示す [EClrOperation](eclroperation-enumeration.md) 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="bfbf1-108">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="bfbf1-109">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="bfbf1-109">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="bfbf1-110">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="bfbf1-110">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="bfbf1-111">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="bfbf1-111">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="bfbf1-112">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="bfbf1-112">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="bfbf1-113">から [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。操作がタイムアウトしたときに実行されるポリシーアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-113">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfbf1-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="bfbf1-114">Return Value</span></span>  
  
|<span data-ttu-id="bfbf1-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bfbf1-115">HRESULT</span></span>|<span data-ttu-id="bfbf1-116">説明</span><span class="sxs-lookup"><span data-stu-id="bfbf1-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bfbf1-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="bfbf1-117">S_OK</span></span>|<span data-ttu-id="bfbf1-118">`SetActionOnTimeout` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-118">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="bfbf1-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bfbf1-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bfbf1-120">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bfbf1-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bfbf1-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bfbf1-122">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-122">The call timed out.</span></span>|  
|<span data-ttu-id="bfbf1-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bfbf1-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bfbf1-124">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bfbf1-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bfbf1-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bfbf1-126">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bfbf1-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bfbf1-127">E_FAIL</span></span>|<span data-ttu-id="bfbf1-128">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bfbf1-129">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bfbf1-130">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bfbf1-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bfbf1-131">E_INVALIDARG</span></span>|<span data-ttu-id="bfbf1-132">指定されたに対してタイムアウトを設定できない `operation` か、に無効な値が指定されました `operation` 。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfbf1-133">解説</span><span class="sxs-lookup"><span data-stu-id="bfbf1-133">Remarks</span></span>  

 <span data-ttu-id="bfbf1-134">タイムアウト値は、CLR によって設定された既定のタイムアウトか、 [ICLRPolicyManager:: SetTimeout](iclrpolicymanager-settimeout-method.md) メソッドの呼び出しでホストによって指定された値のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-134">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="bfbf1-135">すべてのポリシーアクション値は、CLR 操作のタイムアウト動作として指定できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-135">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="bfbf1-136">`SetActionOnTimeout` は、通常、動作をエスカレートするためにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-136">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="bfbf1-137">たとえば、ホストは、スレッドの中止をルースレッドの中止に変換するように指定できますが、逆のを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-137">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="bfbf1-138">次の表は、 `action` 有効な値の有効な値を示して `operation` います。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-138">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="bfbf1-139">の値 `operation`</span><span class="sxs-lookup"><span data-stu-id="bfbf1-139">Value for `operation`</span></span>|<span data-ttu-id="bfbf1-140">`action` の有効な値</span><span class="sxs-lookup"><span data-stu-id="bfbf1-140">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="bfbf1-141">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="bfbf1-141">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="bfbf1-142">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="bfbf1-142">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="bfbf1-143">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="bfbf1-143">-   eRudeAbortThread</span></span><br /><span data-ttu-id="bfbf1-144">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="bfbf1-144">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="bfbf1-145">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="bfbf1-145">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="bfbf1-146">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="bfbf1-146">-   eExitProcess</span></span><br /><span data-ttu-id="bfbf1-147">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="bfbf1-147">-   eFastExitProcess</span></span><br /><span data-ttu-id="bfbf1-148">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="bfbf1-148">-   eRudeExitProcess</span></span><br /><span data-ttu-id="bfbf1-149">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="bfbf1-149">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="bfbf1-150">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="bfbf1-150">OPR_AppDomainUnload</span></span>|<span data-ttu-id="bfbf1-151">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="bfbf1-151">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="bfbf1-152">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="bfbf1-152">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="bfbf1-153">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="bfbf1-153">-   eExitProcess</span></span><br /><span data-ttu-id="bfbf1-154">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="bfbf1-154">-   eFastExitProcess</span></span><br /><span data-ttu-id="bfbf1-155">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="bfbf1-155">-   eRudeExitProcess</span></span><br /><span data-ttu-id="bfbf1-156">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="bfbf1-156">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="bfbf1-157">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="bfbf1-157">OPR_ProcessExit</span></span>|<span data-ttu-id="bfbf1-158">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="bfbf1-158">-   eExitProcess</span></span><br /><span data-ttu-id="bfbf1-159">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="bfbf1-159">-   eFastExitProcess</span></span><br /><span data-ttu-id="bfbf1-160">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="bfbf1-160">-   eRudeExitProcess</span></span><br /><span data-ttu-id="bfbf1-161">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="bfbf1-161">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bfbf1-162">要件</span><span class="sxs-lookup"><span data-stu-id="bfbf1-162">Requirements</span></span>  

 <span data-ttu-id="bfbf1-163">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfbf1-163">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfbf1-164">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bfbf1-164">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfbf1-165">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bfbf1-165">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfbf1-166">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfbf1-166">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfbf1-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfbf1-167">See also</span></span>

- [<span data-ttu-id="bfbf1-168">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="bfbf1-168">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="bfbf1-169">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="bfbf1-169">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="bfbf1-170">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfbf1-170">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="bfbf1-171">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfbf1-171">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)

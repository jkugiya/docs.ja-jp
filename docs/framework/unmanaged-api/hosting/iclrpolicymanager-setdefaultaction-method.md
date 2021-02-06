---
description: '詳細について: ICLRPolicyManager:: SetDefaultAction メソッド'
title: ICLRPolicyManager::SetDefaultAction メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type:
- apiref
ms.openlocfilehash: cedf29f6217660493b151e06220158e931385d79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637366"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="6a80b-103">ICLRPolicyManager::SetDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="6a80b-103">ICLRPolicyManager::SetDefaultAction Method</span></span>

<span data-ttu-id="6a80b-104">指定された操作が発生したときに共通言語ランタイム (CLR) が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="6a80b-104">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a80b-105">構文</span><span class="sxs-lookup"><span data-stu-id="6a80b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a80b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a80b-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="6a80b-107">から [EClrOperation](eclroperation-enumeration.md) 値の1つ。 CLR 動作をカスタマイズする必要があるアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="6a80b-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="6a80b-108">から [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。 CLR が発生したときに実行するポリシーアクションを示し `operation` ます。</span><span class="sxs-lookup"><span data-stu-id="6a80b-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a80b-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="6a80b-109">Return Value</span></span>  
  
|<span data-ttu-id="6a80b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a80b-110">HRESULT</span></span>|<span data-ttu-id="6a80b-111">説明</span><span class="sxs-lookup"><span data-stu-id="6a80b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a80b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a80b-112">S_OK</span></span>|<span data-ttu-id="6a80b-113">`SetDefaultAction` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="6a80b-113">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="6a80b-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6a80b-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6a80b-115">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6a80b-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6a80b-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6a80b-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6a80b-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6a80b-117">The call timed out.</span></span>|  
|<span data-ttu-id="6a80b-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6a80b-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6a80b-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6a80b-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6a80b-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6a80b-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6a80b-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="6a80b-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6a80b-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6a80b-122">E_FAIL</span></span>|<span data-ttu-id="6a80b-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6a80b-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6a80b-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6a80b-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6a80b-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6a80b-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6a80b-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6a80b-126">E_INVALIDARG</span></span>|<span data-ttu-id="6a80b-127">に対して無効なが指定された `action` `operation` か、またはに無効な値が指定されました `operation` 。</span><span class="sxs-lookup"><span data-stu-id="6a80b-127">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a80b-128">解説</span><span class="sxs-lookup"><span data-stu-id="6a80b-128">Remarks</span></span>  

 <span data-ttu-id="6a80b-129">すべてのポリシーアクション値を、CLR 操作の既定の動作として指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="6a80b-129">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="6a80b-130">`SetDefaultAction` 通常は、動作をエスカレートするためにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="6a80b-130">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="6a80b-131">たとえば、ホストは、スレッドの中止をルースレッドの中止に変換するように指定できますが、逆のを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="6a80b-131">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="6a80b-132">次の表は、 `action` 使用可能な各値の有効な値を示して `operation` います。</span><span class="sxs-lookup"><span data-stu-id="6a80b-132">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="6a80b-133">の値 `operation`</span><span class="sxs-lookup"><span data-stu-id="6a80b-133">Value for `operation`</span></span>|<span data-ttu-id="6a80b-134">`action` の有効な値</span><span class="sxs-lookup"><span data-stu-id="6a80b-134">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="6a80b-135">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="6a80b-135">OPR_ThreadAbort</span></span>|<span data-ttu-id="6a80b-136">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="6a80b-136">-   eAbortThread</span></span><br /><span data-ttu-id="6a80b-137">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="6a80b-137">-   eRudeAbortThread</span></span><br /><span data-ttu-id="6a80b-138">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="6a80b-138">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="6a80b-139">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="6a80b-139">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="6a80b-140">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-140">-   eExitProcess</span></span><br /><span data-ttu-id="6a80b-141">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-141">-   eFastExitProcess</span></span><br /><span data-ttu-id="6a80b-142">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-142">-   eRudeExitProcess</span></span><br /><span data-ttu-id="6a80b-143">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="6a80b-143">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="6a80b-144">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="6a80b-144">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="6a80b-145">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="6a80b-145">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="6a80b-146">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="6a80b-146">-   eRudeAbortThread</span></span><br /><span data-ttu-id="6a80b-147">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="6a80b-147">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="6a80b-148">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="6a80b-148">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="6a80b-149">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-149">-   eExitProcess</span></span><br /><span data-ttu-id="6a80b-150">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-150">-   eFastExitProcess</span></span><br /><span data-ttu-id="6a80b-151">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-151">-   eRudeExitProcess</span></span><br /><span data-ttu-id="6a80b-152">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="6a80b-152">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="6a80b-153">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="6a80b-153">OPR_AppDomainUnload</span></span>|<span data-ttu-id="6a80b-154">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="6a80b-154">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="6a80b-155">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="6a80b-155">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="6a80b-156">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-156">-   eExitProcess</span></span><br /><span data-ttu-id="6a80b-157">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-157">-   eFastExitProcess</span></span><br /><span data-ttu-id="6a80b-158">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-158">-   eRudeExitProcess</span></span><br /><span data-ttu-id="6a80b-159">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="6a80b-159">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="6a80b-160">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="6a80b-160">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="6a80b-161">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="6a80b-161">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="6a80b-162">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-162">-   eExitProcess</span></span><br /><span data-ttu-id="6a80b-163">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-163">-   eFastExitProcess</span></span><br /><span data-ttu-id="6a80b-164">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-164">-   eRudeExitProcess</span></span><br /><span data-ttu-id="6a80b-165">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="6a80b-165">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="6a80b-166">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="6a80b-166">OPR_ProcessExit</span></span>|<span data-ttu-id="6a80b-167">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-167">-   eExitProcess</span></span><br /><span data-ttu-id="6a80b-168">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-168">-   eFastExitProcess</span></span><br /><span data-ttu-id="6a80b-169">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-169">-   eRudeExitProcess</span></span><br /><span data-ttu-id="6a80b-170">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="6a80b-170">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="6a80b-171">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="6a80b-171">OPR_FinalizerRun</span></span>|<span data-ttu-id="6a80b-172">-"-" アクション</span><span class="sxs-lookup"><span data-stu-id="6a80b-172">-   eNoAction</span></span><br /><span data-ttu-id="6a80b-173">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="6a80b-173">-   eAbortThread</span></span><br /><span data-ttu-id="6a80b-174">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="6a80b-174">-   eRudeAbortThread</span></span><br /><span data-ttu-id="6a80b-175">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="6a80b-175">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="6a80b-176">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="6a80b-176">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="6a80b-177">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-177">-   eExitProcess</span></span><br /><span data-ttu-id="6a80b-178">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-178">-   eFastExitProcess</span></span><br /><span data-ttu-id="6a80b-179">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="6a80b-179">-   eRudeExitProcess</span></span><br /><span data-ttu-id="6a80b-180">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="6a80b-180">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a80b-181">要件</span><span class="sxs-lookup"><span data-stu-id="6a80b-181">Requirements</span></span>  

 <span data-ttu-id="6a80b-182">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a80b-182">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a80b-183">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6a80b-183">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a80b-184">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6a80b-184">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a80b-185">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a80b-185">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a80b-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a80b-186">See also</span></span>

- [<span data-ttu-id="6a80b-187">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="6a80b-187">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="6a80b-188">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="6a80b-188">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="6a80b-189">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a80b-189">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)

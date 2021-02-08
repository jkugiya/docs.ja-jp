---
description: '詳細について: ICLRPolicyManager:: SetActionOnFailure メソッド'
title: ICLRPolicyManager::SetActionOnFailure メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 67d3ca5d7924caf0a768b4de53b4b24f1c72fa27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789802"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="57146-103">ICLRPolicyManager::SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="57146-103">ICLRPolicyManager::SetActionOnFailure Method</span></span>

<span data-ttu-id="57146-104">指定したエラーが発生したときに共通言語ランタイム (CLR) が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="57146-104">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57146-105">構文</span><span class="sxs-lookup"><span data-stu-id="57146-105">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57146-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="57146-106">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="57146-107">から [Eclrfailure](eclrfailure-enumeration.md) 値の1つで、アクションを実行するエラーの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="57146-107">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="57146-108">から [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。エラーが発生したときに実行するアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="57146-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="57146-109">サポートされている値の一覧については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57146-109">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57146-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="57146-110">Return Value</span></span>  
  
|<span data-ttu-id="57146-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57146-111">HRESULT</span></span>|<span data-ttu-id="57146-112">説明</span><span class="sxs-lookup"><span data-stu-id="57146-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57146-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="57146-113">S_OK</span></span>|<span data-ttu-id="57146-114">`SetActionOnFailure` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="57146-114">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="57146-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57146-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57146-116">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="57146-116">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57146-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57146-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57146-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="57146-118">The call timed out.</span></span>|  
|<span data-ttu-id="57146-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57146-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57146-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="57146-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57146-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57146-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57146-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="57146-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57146-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57146-123">E_FAIL</span></span>|<span data-ttu-id="57146-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="57146-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57146-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="57146-125">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57146-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="57146-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="57146-127">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="57146-127">E_INVALIDARG</span></span>|<span data-ttu-id="57146-128">指定された操作に対してポリシーアクションを設定できないか、操作に無効なポリシーアクションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="57146-128">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57146-129">解説</span><span class="sxs-lookup"><span data-stu-id="57146-129">Remarks</span></span>  

 <span data-ttu-id="57146-130">既定では、メモリなどのリソースの割り当てに失敗した場合、CLR は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="57146-130">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="57146-131">`SetActionOnFailure` エラー発生時に実行するポリシーアクションを指定して、ホストがこの動作をオーバーライドできるようにします。</span><span class="sxs-lookup"><span data-stu-id="57146-131">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="57146-132">次の表は、サポートされている [Eclrfailure](eclrfailure-enumeration.md) 値と [epolicyaction](epolicyaction-enumeration.md) 値の組み合わせを示しています。</span><span class="sxs-lookup"><span data-stu-id="57146-132">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="57146-133">(FAIL_ プレフィックスは [Eclrfailure](eclrfailure-enumeration.md) 値から省略されています)。</span><span class="sxs-lookup"><span data-stu-id="57146-133">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="57146-134">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="57146-134">NonCriticalResource</span></span>|<span data-ttu-id="57146-135">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="57146-135">CriticalResource</span></span>|<span data-ttu-id="57146-136">Fat (Alruntime)</span><span class="sxs-lookup"><span data-stu-id="57146-136">FatalRuntime</span></span>|<span data-ttu-id="57146-137">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="57146-137">OrphanedLock</span></span>|<span data-ttu-id="57146-138">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="57146-138">StackOverflow</span></span>|<span data-ttu-id="57146-139">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="57146-139">AccessViolation</span></span>|<span data-ttu-id="57146-140">CodeContract</span><span class="sxs-lookup"><span data-stu-id="57146-140">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="57146-141">X</span><span class="sxs-lookup"><span data-stu-id="57146-141">X</span></span>|<span data-ttu-id="57146-142">X</span><span class="sxs-lookup"><span data-stu-id="57146-142">X</span></span>||||<span data-ttu-id="57146-143">該当なし</span><span class="sxs-lookup"><span data-stu-id="57146-143">N/A</span></span>||  
|<span data-ttu-id="57146-144">の例外</span><span class="sxs-lookup"><span data-stu-id="57146-144">eThrowException</span></span>|<span data-ttu-id="57146-145">X</span><span class="sxs-lookup"><span data-stu-id="57146-145">X</span></span>|<span data-ttu-id="57146-146">X</span><span class="sxs-lookup"><span data-stu-id="57146-146">X</span></span>||||<span data-ttu-id="57146-147">該当なし</span><span class="sxs-lookup"><span data-stu-id="57146-147">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="57146-148">X</span><span class="sxs-lookup"><span data-stu-id="57146-148">X</span></span>|<span data-ttu-id="57146-149">X</span><span class="sxs-lookup"><span data-stu-id="57146-149">X</span></span>||||<span data-ttu-id="57146-150">該当なし</span><span class="sxs-lookup"><span data-stu-id="57146-150">N/A</span></span>|<span data-ttu-id="57146-151">X</span><span class="sxs-lookup"><span data-stu-id="57146-151">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="57146-152">X</span><span class="sxs-lookup"><span data-stu-id="57146-152">X</span></span>|<span data-ttu-id="57146-153">X</span><span class="sxs-lookup"><span data-stu-id="57146-153">X</span></span>||||<span data-ttu-id="57146-154">該当なし</span><span class="sxs-lookup"><span data-stu-id="57146-154">N/A</span></span>|<span data-ttu-id="57146-155">X</span><span class="sxs-lookup"><span data-stu-id="57146-155">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="57146-156">X</span><span class="sxs-lookup"><span data-stu-id="57146-156">X</span></span>|<span data-ttu-id="57146-157">X</span><span class="sxs-lookup"><span data-stu-id="57146-157">X</span></span>||<span data-ttu-id="57146-158">X</span><span class="sxs-lookup"><span data-stu-id="57146-158">X</span></span>||<span data-ttu-id="57146-159">該当なし</span><span class="sxs-lookup"><span data-stu-id="57146-159">N/A</span></span>|<span data-ttu-id="57146-160">X</span><span class="sxs-lookup"><span data-stu-id="57146-160">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="57146-161">X</span><span class="sxs-lookup"><span data-stu-id="57146-161">X</span></span>|<span data-ttu-id="57146-162">X</span><span class="sxs-lookup"><span data-stu-id="57146-162">X</span></span>||<span data-ttu-id="57146-163">X</span><span class="sxs-lookup"><span data-stu-id="57146-163">X</span></span>|<span data-ttu-id="57146-164">X</span><span class="sxs-lookup"><span data-stu-id="57146-164">X</span></span>|<span data-ttu-id="57146-165">該当なし</span><span class="sxs-lookup"><span data-stu-id="57146-165">N/A</span></span>|<span data-ttu-id="57146-166">X</span><span class="sxs-lookup"><span data-stu-id="57146-166">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="57146-167">X</span><span class="sxs-lookup"><span data-stu-id="57146-167">X</span></span>|<span data-ttu-id="57146-168">X</span><span class="sxs-lookup"><span data-stu-id="57146-168">X</span></span>||<span data-ttu-id="57146-169">X</span><span class="sxs-lookup"><span data-stu-id="57146-169">X</span></span>|<span data-ttu-id="57146-170">X</span><span class="sxs-lookup"><span data-stu-id="57146-170">X</span></span>|<span data-ttu-id="57146-171">該当なし</span><span class="sxs-lookup"><span data-stu-id="57146-171">N/A</span></span>|<span data-ttu-id="57146-172">X</span><span class="sxs-lookup"><span data-stu-id="57146-172">X</span></span>|  
|<span data-ttu-id="57146-173">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="57146-173">eFastExitProcess</span></span>|<span data-ttu-id="57146-174">X</span><span class="sxs-lookup"><span data-stu-id="57146-174">X</span></span>|<span data-ttu-id="57146-175">X</span><span class="sxs-lookup"><span data-stu-id="57146-175">X</span></span>||<span data-ttu-id="57146-176">X</span><span class="sxs-lookup"><span data-stu-id="57146-176">X</span></span>|<span data-ttu-id="57146-177">X</span><span class="sxs-lookup"><span data-stu-id="57146-177">X</span></span>|<span data-ttu-id="57146-178">該当なし</span><span class="sxs-lookup"><span data-stu-id="57146-178">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="57146-179">X</span><span class="sxs-lookup"><span data-stu-id="57146-179">X</span></span>|<span data-ttu-id="57146-180">X</span><span class="sxs-lookup"><span data-stu-id="57146-180">X</span></span>|<span data-ttu-id="57146-181">X</span><span class="sxs-lookup"><span data-stu-id="57146-181">X</span></span>|<span data-ttu-id="57146-182">X</span><span class="sxs-lookup"><span data-stu-id="57146-182">X</span></span>|<span data-ttu-id="57146-183">X</span><span class="sxs-lookup"><span data-stu-id="57146-183">X</span></span>|<span data-ttu-id="57146-184">該当なし</span><span class="sxs-lookup"><span data-stu-id="57146-184">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="57146-185">X</span><span class="sxs-lookup"><span data-stu-id="57146-185">X</span></span>|<span data-ttu-id="57146-186">X</span><span class="sxs-lookup"><span data-stu-id="57146-186">X</span></span>|<span data-ttu-id="57146-187">X</span><span class="sxs-lookup"><span data-stu-id="57146-187">X</span></span>|<span data-ttu-id="57146-188">X</span><span class="sxs-lookup"><span data-stu-id="57146-188">X</span></span>|<span data-ttu-id="57146-189">X</span><span class="sxs-lookup"><span data-stu-id="57146-189">X</span></span>|<span data-ttu-id="57146-190">該当なし</span><span class="sxs-lookup"><span data-stu-id="57146-190">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="57146-191">要件</span><span class="sxs-lookup"><span data-stu-id="57146-191">Requirements</span></span>  

 <span data-ttu-id="57146-192">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57146-192">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57146-193">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="57146-193">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57146-194">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="57146-194">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57146-195">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57146-195">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57146-196">関連項目</span><span class="sxs-lookup"><span data-stu-id="57146-196">See also</span></span>

- [<span data-ttu-id="57146-197">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="57146-197">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="57146-198">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="57146-198">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="57146-199">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57146-199">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="57146-200">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57146-200">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)

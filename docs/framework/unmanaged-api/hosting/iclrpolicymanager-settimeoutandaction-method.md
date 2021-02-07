---
description: '詳細については、次を参照してください: ICLRPolicyManager:: SetTimeoutAndAction メソッド'
title: ICLRPolicyManager::SetTimeoutAndAction メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
ms.openlocfilehash: c91d43cce381bef804b30e9e1dcb50574ddcd1b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716563"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="7cc52-103">ICLRPolicyManager::SetTimeoutAndAction メソッド</span><span class="sxs-lookup"><span data-stu-id="7cc52-103">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>

<span data-ttu-id="7cc52-104">指定された操作のタイムアウト値を設定し、操作が発生したときに共通言語ランタイム (CLR) が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="7cc52-104">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc52-105">構文</span><span class="sxs-lookup"><span data-stu-id="7cc52-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cc52-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7cc52-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="7cc52-107">からタイムアウトとポリシーを設定する操作を示す [EClrOperation](eclroperation-enumeration.md) 値の1つ `action` 。</span><span class="sxs-lookup"><span data-stu-id="7cc52-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="7cc52-108">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7cc52-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="7cc52-109">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="7cc52-109">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="7cc52-110">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="7cc52-110">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="7cc52-111">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="7cc52-111">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="7cc52-112">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="7cc52-112">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="7cc52-113">から新しいタイムアウト値 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="7cc52-113">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="7cc52-114">値が無限であると、 `operation` タイムアウトしません。</span><span class="sxs-lookup"><span data-stu-id="7cc52-114">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="7cc52-115">から [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。 CLR が発生したときに実行するポリシーアクションを示し `operation` ます。</span><span class="sxs-lookup"><span data-stu-id="7cc52-115">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cc52-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="7cc52-116">Return Value</span></span>  
  
|<span data-ttu-id="7cc52-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7cc52-117">HRESULT</span></span>|<span data-ttu-id="7cc52-118">説明</span><span class="sxs-lookup"><span data-stu-id="7cc52-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7cc52-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="7cc52-119">S_OK</span></span>|<span data-ttu-id="7cc52-120">`SetTimeoutAndAction` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="7cc52-120">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="7cc52-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7cc52-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7cc52-122">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="7cc52-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7cc52-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7cc52-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7cc52-124">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="7cc52-124">The call timed out.</span></span>|  
|<span data-ttu-id="7cc52-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7cc52-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7cc52-126">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="7cc52-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7cc52-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7cc52-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7cc52-128">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="7cc52-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7cc52-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7cc52-129">E_FAIL</span></span>|<span data-ttu-id="7cc52-130">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7cc52-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7cc52-131">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="7cc52-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7cc52-132">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="7cc52-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7cc52-133">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7cc52-133">E_INVALIDARG</span></span>|<span data-ttu-id="7cc52-134">指定されたに対してタイムアウトを設定できない `operation` か、に無効な値が指定されました `action` 。</span><span class="sxs-lookup"><span data-stu-id="7cc52-134">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cc52-135">解説</span><span class="sxs-lookup"><span data-stu-id="7cc52-135">Remarks</span></span>  

 <span data-ttu-id="7cc52-136">`SetTimeoutAndAction`[ICLRPolicyManager:: SetTimeout](iclrpolicymanager-settimeout-method.md)メソッドと[ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md)メソッドの機能をカプセル化し、これら2つのメソッドの順次呼び出しの代わりに呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7cc52-136">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7cc52-137">すべてのポリシーアクション値は、CLR 操作のタイムアウト動作として指定できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="7cc52-137">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="7cc52-138">有効な値については、これら2つの方法に関するトピックの「解説」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cc52-138">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cc52-139">要件</span><span class="sxs-lookup"><span data-stu-id="7cc52-139">Requirements</span></span>  

 <span data-ttu-id="7cc52-140">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cc52-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cc52-141">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7cc52-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7cc52-142">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7cc52-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cc52-143">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cc52-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc52-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="7cc52-144">See also</span></span>

- [<span data-ttu-id="7cc52-145">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="7cc52-145">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="7cc52-146">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="7cc52-146">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="7cc52-147">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cc52-147">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="7cc52-148">SetActionOnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="7cc52-148">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="7cc52-149">ICLRPolicyManager:: SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="7cc52-149">ICLRPolicyManager::SetTimeoutAndAction</span></span>](iclrpolicymanager-settimeoutandaction-method.md)

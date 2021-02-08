---
description: '詳細情報: ICLRHostBindingPolicyManager:: EvaluatePolicy メソッド'
title: ICLRHostBindingPolicyManager::EvaluatePolicy メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
ms.openlocfilehash: e92126a8c12d03ee21e4867754b1a418ef11d463
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789971"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="3e88e-103">ICLRHostBindingPolicyManager::EvaluatePolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="3e88e-103">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>

<span data-ttu-id="3e88e-104">ホストの代わりにバインドポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="3e88e-104">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e88e-105">構文</span><span class="sxs-lookup"><span data-stu-id="3e88e-105">Syntax</span></span>  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e88e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e88e-106">Parameters</span></span>  

 `pwzReferenceIdentity`  
 <span data-ttu-id="3e88e-107">からポリシー評価の前のアセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="3e88e-107">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="3e88e-108">からポリシーデータを格納しているバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3e88e-108">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="3e88e-109">からバッファーのサイズ `pbApplicationPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="3e88e-109">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="3e88e-110">入出力新しいポリシーデータを評価した後のアセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="3e88e-110">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="3e88e-111">[入力、出力]新しいポリシーデータを評価した後のアセンブリ id 参照バッファーのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3e88e-111">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="3e88e-112">入出力適用されているポリシーを示す [Ebindpolicylevels](ebindpolicylevels-enumeration.md) 値の論理和の組み合わせへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3e88e-112">[out] A pointer to a logical OR combination of [EBindPolicyLevels](ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e88e-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="3e88e-113">Return Value</span></span>  
  
|<span data-ttu-id="3e88e-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e88e-114">HRESULT</span></span>|<span data-ttu-id="3e88e-115">説明</span><span class="sxs-lookup"><span data-stu-id="3e88e-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e88e-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e88e-116">S_OK</span></span>|<span data-ttu-id="3e88e-117">評価が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="3e88e-117">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="3e88e-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3e88e-118">E_INVALIDARG</span></span>|<span data-ttu-id="3e88e-119">またはのいずれか `pwzReferenceIdentity` `pbApplicationPolicy` が null 参照です。</span><span class="sxs-lookup"><span data-stu-id="3e88e-119">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="3e88e-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3e88e-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="3e88e-121">`cbAppPolicySize` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="3e88e-121">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="3e88e-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e88e-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e88e-123">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="3e88e-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e88e-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e88e-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e88e-125">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3e88e-125">The call timed out.</span></span>|  
|<span data-ttu-id="3e88e-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e88e-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e88e-127">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3e88e-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e88e-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e88e-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e88e-129">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="3e88e-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e88e-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e88e-130">E_FAIL</span></span>|<span data-ttu-id="3e88e-131">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3e88e-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e88e-132">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3e88e-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e88e-133">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="3e88e-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e88e-134">解説</span><span class="sxs-lookup"><span data-stu-id="3e88e-134">Remarks</span></span>  

 <span data-ttu-id="3e88e-135">メソッドを使用すると、ホスト `EvaluatePolicy` は、ホスト固有のアセンブリのバージョン管理要件を維持するために、バインディングポリシーに影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="3e88e-135">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="3e88e-136">ポリシーエンジン自体は CLR 内に残ります。</span><span class="sxs-lookup"><span data-stu-id="3e88e-136">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e88e-137">要件</span><span class="sxs-lookup"><span data-stu-id="3e88e-137">Requirements</span></span>  

 <span data-ttu-id="3e88e-138">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e88e-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e88e-139">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3e88e-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e88e-140">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3e88e-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e88e-141">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e88e-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e88e-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e88e-142">See also</span></span>

- [<span data-ttu-id="3e88e-143">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e88e-143">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)

---
description: '詳細情報: ICLRHostBindingPolicyManager:: ModifyApplicationPolicy メソッド'
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: 3f7d992f4b7d24233da175814f991106bb97a937
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789932"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="c4fd4-103">ICLRHostBindingPolicyManager::ModifyApplicationPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="c4fd4-103">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>

<span data-ttu-id="c4fd4-104">指定したアセンブリのバインディングポリシーを変更し、新しいバージョンのポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-104">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4fd4-105">構文</span><span class="sxs-lookup"><span data-stu-id="c4fd4-105">Syntax</span></span>  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4fd4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c4fd4-106">Parameters</span></span>  

 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="c4fd4-107">から変更するアセンブリの id。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-107">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="c4fd4-108">から変更されたアセンブリの新しい id。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-108">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="c4fd4-109">から変更するアセンブリのバインディングポリシーデータを格納しているバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-109">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="c4fd4-110">から置換されるバインディングポリシーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-110">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="c4fd4-111">からリダイレクトの制御を示す [Ehostbindingpolicymodifyflags](ehostbindingpolicymodifyflags-enumeration.md) 値の論理的または組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-111">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="c4fd4-112">入出力新しいバインドポリシーデータを格納しているバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-112">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="c4fd4-113">[入力、出力]新しいバインドポリシーバッファーのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-113">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4fd4-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="c4fd4-114">Return Value</span></span>  
  
|<span data-ttu-id="c4fd4-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4fd4-115">HRESULT</span></span>|<span data-ttu-id="c4fd4-116">説明</span><span class="sxs-lookup"><span data-stu-id="c4fd4-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4fd4-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4fd4-117">S_OK</span></span>|<span data-ttu-id="c4fd4-118">ポリシーが正常に変更されました。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-118">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="c4fd4-119">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c4fd4-119">E_INVALIDARG</span></span>|<span data-ttu-id="c4fd4-120">`pwzSourceAssemblyIdentity` または `pwzTargetAssemblyIdentity` が null 参照です。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-120">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="c4fd4-121">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c4fd4-121">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c4fd4-122">`pbNewApplicationPolicy` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-122">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="c4fd4-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4fd4-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4fd4-124">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-124">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4fd4-125">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4fd4-125">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4fd4-126">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-126">The call timed out.</span></span>|  
|<span data-ttu-id="c4fd4-127">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4fd4-127">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4fd4-128">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-128">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4fd4-129">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4fd4-129">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4fd4-130">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-130">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4fd4-131">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4fd4-131">E_FAIL</span></span>|<span data-ttu-id="c4fd4-132">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-132">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4fd4-133">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-133">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4fd4-134">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-134">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4fd4-135">解説</span><span class="sxs-lookup"><span data-stu-id="c4fd4-135">Remarks</span></span>  

 <span data-ttu-id="c4fd4-136">メソッドは、 `ModifyApplicationPolicy` 2 回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-136">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="c4fd4-137">最初の呼び出しでは、パラメーターに null 値を指定する必要があり `pbNewApplicationPolicy` ます。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-137">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="c4fd4-138">この呼び出しは、に必要な値で返され `pcbNewAppPolicySize` ます。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-138">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="c4fd4-139">2番目の呼び出しでは、にこの値を指定 `pcbNewAppPolicySize` し、のサイズのバッファーを指す必要があり `pbNewApplicationPolicy` ます。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-139">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4fd4-140">要件</span><span class="sxs-lookup"><span data-stu-id="c4fd4-140">Requirements</span></span>  

 <span data-ttu-id="c4fd4-141">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4fd4-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4fd4-142">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c4fd4-142">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4fd4-143">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c4fd4-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4fd4-144">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4fd4-144">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4fd4-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4fd4-145">See also</span></span>

- [<span data-ttu-id="c4fd4-146">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4fd4-146">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)

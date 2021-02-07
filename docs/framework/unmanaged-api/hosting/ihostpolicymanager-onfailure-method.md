---
description: '詳細について: IHostPolicyManager:: OnFailure メソッド'
title: IHostPolicyManager::OnFailure メソッド
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
ms.openlocfilehash: 9fb359d4ba1b1b89e029a0772a0f67a49b2b380b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671842"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="b51d5-103">IHostPolicyManager::OnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="b51d5-103">IHostPolicyManager::OnFailure Method</span></span>

<span data-ttu-id="b51d5-104">リソース割り当てまたは再利用の失敗に応じて、 [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) メソッドの呼び出しによって指定されたアクションを共通言語ランタイム (CLR) が実行しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="b51d5-104">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b51d5-105">構文</span><span class="sxs-lookup"><span data-stu-id="b51d5-105">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b51d5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b51d5-106">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="b51d5-107">から [Eclrfailure](eclrfailure-enumeration.md) 値の1つ。 CLR が応答しているエラーの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="b51d5-107">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="b51d5-108">から [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。 CLR がに応答して実行しているアクションを示し `failure` ます。</span><span class="sxs-lookup"><span data-stu-id="b51d5-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b51d5-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="b51d5-109">Return Value</span></span>  
  
|<span data-ttu-id="b51d5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b51d5-110">HRESULT</span></span>|<span data-ttu-id="b51d5-111">説明</span><span class="sxs-lookup"><span data-stu-id="b51d5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b51d5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b51d5-112">S_OK</span></span>|<span data-ttu-id="b51d5-113">`OnFailure` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="b51d5-113">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="b51d5-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b51d5-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b51d5-115">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="b51d5-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b51d5-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b51d5-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b51d5-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b51d5-117">The call timed out.</span></span>|  
|<span data-ttu-id="b51d5-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b51d5-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b51d5-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="b51d5-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b51d5-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b51d5-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b51d5-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="b51d5-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b51d5-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b51d5-122">E_FAIL</span></span>|<span data-ttu-id="b51d5-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b51d5-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b51d5-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="b51d5-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b51d5-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="b51d5-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b51d5-126">要件</span><span class="sxs-lookup"><span data-stu-id="b51d5-126">Requirements</span></span>  

 <span data-ttu-id="b51d5-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b51d5-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b51d5-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b51d5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b51d5-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b51d5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b51d5-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b51d5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b51d5-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="b51d5-131">See also</span></span>

- [<span data-ttu-id="b51d5-132">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="b51d5-132">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="b51d5-133">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="b51d5-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="b51d5-134">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b51d5-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="b51d5-135">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b51d5-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)

---
description: '詳細について: IHostPolicyManager:: OnDefaultAction メソッド'
title: IHostPolicyManager::OnDefaultAction メソッド
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: ea474734f7bc0a5210c5aecf605452909b261a87
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671910"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="ed42e-103">IHostPolicyManager::OnDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="ed42e-103">IHostPolicyManager::OnDefaultAction Method</span></span>

<span data-ttu-id="ed42e-104">スレッドの中止またはアンロードに応じて、 [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) メソッドの呼び出しによって設定された既定のアクションを共通言語ランタイム (CLR: common language runtime) が実行しようとしていることをホストに通知し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="ed42e-104">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed42e-105">構文</span><span class="sxs-lookup"><span data-stu-id="ed42e-105">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed42e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ed42e-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="ed42e-107">から [EClrOperation](eclroperation-enumeration.md) 値の1つ。 CLR が応答するイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="ed42e-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="ed42e-108">からイベントへの応答として CLR が実行しているアクションを示す [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="ed42e-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed42e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ed42e-109">Return Value</span></span>  
  
|<span data-ttu-id="ed42e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed42e-110">HRESULT</span></span>|<span data-ttu-id="ed42e-111">説明</span><span class="sxs-lookup"><span data-stu-id="ed42e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed42e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed42e-112">S_OK</span></span>|<span data-ttu-id="ed42e-113">`OnDefaultAction` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="ed42e-113">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="ed42e-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed42e-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed42e-115">CLR がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しを処理できません。</span><span class="sxs-lookup"><span data-stu-id="ed42e-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="ed42e-116">なく</span><span class="sxs-lookup"><span data-stu-id="ed42e-116">successfully</span></span>|  
|<span data-ttu-id="ed42e-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ed42e-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ed42e-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ed42e-118">The call timed out.</span></span>|  
|<span data-ttu-id="ed42e-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed42e-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ed42e-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ed42e-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ed42e-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ed42e-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ed42e-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="ed42e-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ed42e-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed42e-123">E_FAIL</span></span>|<span data-ttu-id="ed42e-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ed42e-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ed42e-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ed42e-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ed42e-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="ed42e-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed42e-127">要件</span><span class="sxs-lookup"><span data-stu-id="ed42e-127">Requirements</span></span>  

 <span data-ttu-id="ed42e-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed42e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed42e-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ed42e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed42e-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ed42e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed42e-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed42e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed42e-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed42e-132">See also</span></span>

- [<span data-ttu-id="ed42e-133">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="ed42e-133">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="ed42e-134">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="ed42e-134">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="ed42e-135">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed42e-135">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="ed42e-136">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed42e-136">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)

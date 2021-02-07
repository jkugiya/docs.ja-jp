---
description: '詳細について: IHostControl:: SetAppDomainManager メソッド'
title: IHostControl::SetAppDomainManager メソッド
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
ms.openlocfilehash: 1fc5efc0afad73d1805338140f186a50913ca542
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708897"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="00ed4-103">IHostControl::SetAppDomainManager メソッド</span><span class="sxs-lookup"><span data-stu-id="00ed4-103">IHostControl::SetAppDomainManager Method</span></span>

<span data-ttu-id="00ed4-104">アプリケーションドメインが作成されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="00ed4-104">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ed4-105">構文</span><span class="sxs-lookup"><span data-stu-id="00ed4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00ed4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00ed4-106">Parameters</span></span>  

 `dwAppDomainID`  
 <span data-ttu-id="00ed4-107">から選択されたの数値識別子 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="00ed4-107">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="00ed4-108">から <xref:System.AppDomainManager> ホストがとして実装しているオブジェクトへのポインター `IUnknown` 。</span><span class="sxs-lookup"><span data-stu-id="00ed4-108">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00ed4-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="00ed4-109">Return Value</span></span>  
  
|<span data-ttu-id="00ed4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00ed4-110">HRESULT</span></span>|<span data-ttu-id="00ed4-111">説明</span><span class="sxs-lookup"><span data-stu-id="00ed4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00ed4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="00ed4-112">S_OK</span></span>|<span data-ttu-id="00ed4-113">`SetAppDomainManager` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="00ed4-113">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="00ed4-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="00ed4-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="00ed4-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="00ed4-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="00ed4-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="00ed4-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="00ed4-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="00ed4-117">The call timed out.</span></span>|  
|<span data-ttu-id="00ed4-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="00ed4-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="00ed4-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="00ed4-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="00ed4-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="00ed4-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="00ed4-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="00ed4-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="00ed4-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00ed4-122">E_FAIL</span></span>|<span data-ttu-id="00ed4-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="00ed4-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="00ed4-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="00ed4-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="00ed4-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="00ed4-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00ed4-126">解説</span><span class="sxs-lookup"><span data-stu-id="00ed4-126">Remarks</span></span>  

 <span data-ttu-id="00ed4-127">は、 <xref:System.AppDomainManager> マネージコードにブートストラップし、それぞれの作成と設定を制御するためのメカニズムをホストに提供し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="00ed4-127">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="00ed4-128">は、作成される <xref:System.AppDomainManager> ときにそれぞれに読み込まれ <xref:System.AppDomain> <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="00ed4-128">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="00ed4-129">このオプションを選択した場合、CLR は、パラメーターの値を設定することによって、アプリケーションドメインが作成されたことをホストに通知 `pUnkAppDomainManager` します。</span><span class="sxs-lookup"><span data-stu-id="00ed4-129">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="00ed4-130">メソッドの実装では、 `SetAppDomainManager` ホストはアプリケーションドメインマネージャーのアセンブリ名と型を設定できます。</span><span class="sxs-lookup"><span data-stu-id="00ed4-130">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00ed4-131">要件</span><span class="sxs-lookup"><span data-stu-id="00ed4-131">Requirements</span></span>  

 <span data-ttu-id="00ed4-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00ed4-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00ed4-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="00ed4-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00ed4-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="00ed4-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00ed4-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00ed4-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ed4-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="00ed4-136">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="00ed4-137">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00ed4-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)

---
description: '詳細について: ICLRRuntimeHost:: ExecuteApplication メソッド'
title: ICLRRuntimeHost::ExecuteApplication メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
ms.openlocfilehash: 1511cc3dcf05c3f2243f4080143789e456c39167
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688976"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="f62de-103">ICLRRuntimeHost::ExecuteApplication メソッド</span><span class="sxs-lookup"><span data-stu-id="f62de-103">ICLRRuntimeHost::ExecuteApplication Method</span></span>

<span data-ttu-id="f62de-104">新しいドメインでアクティブ化するアプリケーションを指定するために、マニフェストベースの ClickOnce 配置シナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="f62de-104">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="f62de-105">これらのシナリオの詳細については、「 [ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f62de-105">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f62de-106">構文</span><span class="sxs-lookup"><span data-stu-id="f62de-106">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f62de-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f62de-107">Parameters</span></span>  

 `pwzAppFullName`  
 <span data-ttu-id="f62de-108">からに定義されているアプリケーションの完全名 <xref:System.ApplicationIdentity> 。</span><span class="sxs-lookup"><span data-stu-id="f62de-108">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="f62de-109">から配列に格納されている文字列の数 `ppwzManifestPaths` 。</span><span class="sxs-lookup"><span data-stu-id="f62de-109">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="f62de-110">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="f62de-110">[in] Optional.</span></span> <span data-ttu-id="f62de-111">アプリケーションのマニフェストパスを格納する文字列配列。</span><span class="sxs-lookup"><span data-stu-id="f62de-111">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="f62de-112">から配列に格納されている文字列の数 `ppwzActivationData` 。</span><span class="sxs-lookup"><span data-stu-id="f62de-112">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="f62de-113">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="f62de-113">[in] Optional.</span></span> <span data-ttu-id="f62de-114">Web に配置されたアプリケーションの URL のクエリ文字列部分など、アプリケーションのアクティベーションデータを格納する文字列配列。</span><span class="sxs-lookup"><span data-stu-id="f62de-114">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="f62de-115">入出力アプリケーションのエントリポイントから返される値。</span><span class="sxs-lookup"><span data-stu-id="f62de-115">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f62de-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="f62de-116">Return Value</span></span>  
  
|<span data-ttu-id="f62de-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f62de-117">HRESULT</span></span>|<span data-ttu-id="f62de-118">説明</span><span class="sxs-lookup"><span data-stu-id="f62de-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f62de-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="f62de-119">S_OK</span></span>|<span data-ttu-id="f62de-120">`ExecuteApplication` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f62de-120">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="f62de-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f62de-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f62de-122">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f62de-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f62de-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f62de-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f62de-124">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f62de-124">The call timed out.</span></span>|  
|<span data-ttu-id="f62de-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f62de-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f62de-126">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f62de-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f62de-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f62de-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f62de-128">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f62de-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f62de-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f62de-129">E_FAIL</span></span>|<span data-ttu-id="f62de-130">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f62de-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f62de-131">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f62de-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f62de-132">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f62de-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f62de-133">解説</span><span class="sxs-lookup"><span data-stu-id="f62de-133">Remarks</span></span>  

 <span data-ttu-id="f62de-134">`ExecuteApplication` は、新しく作成されたアプリケーションドメインで ClickOnce アプリケーションをアクティブ化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f62de-134">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="f62de-135">`pReturnValue`出力パラメーターは、アプリケーションによって返される値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f62de-135">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="f62de-136">に null 値を指定した場合 `pReturnValue` 、 `ExecuteApplication` は失敗しませんが、値を返しません。</span><span class="sxs-lookup"><span data-stu-id="f62de-136">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f62de-137">メソッドを呼び出してからマニフェストベースのアプリケーションをアクティブ化する前に、 [Start メソッド](iclrruntimehost-start-method.md) メソッドを呼び出さないでください `ExecuteApplication` 。</span><span class="sxs-lookup"><span data-stu-id="f62de-137">Do not call the [Start Method](iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="f62de-138">`Start`メソッドが最初に呼び出された場合、 `ExecuteApplication` メソッドの呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="f62de-138">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f62de-139">要件</span><span class="sxs-lookup"><span data-stu-id="f62de-139">Requirements</span></span>  

 <span data-ttu-id="f62de-140">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f62de-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f62de-141">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f62de-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f62de-142">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f62de-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f62de-143">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f62de-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f62de-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="f62de-144">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="f62de-145">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f62de-145">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="f62de-146">SetAppDomainManager メソッド</span><span class="sxs-lookup"><span data-stu-id="f62de-146">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="f62de-147">チュートリアル: デザイナーを使用して ClickOnce 配置 API で必要に応じてアセンブリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="f62de-147">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)

---
description: '詳細情報: ICLRRuntimeHost::UnloadAppDomain メソッド'
title: ICLRRuntimeHost::UnloadAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
ms.openlocfilehash: 2a47c6250434c3ee4122f8eeae75f25ee4c08a34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637288"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="915c2-103">ICLRRuntimeHost::UnloadAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="915c2-103">ICLRRuntimeHost::UnloadAppDomain Method</span></span>

<span data-ttu-id="915c2-104">指定された数値識別子に対応するマネージド <xref:System.AppDomain> をアンロードします。</span><span class="sxs-lookup"><span data-stu-id="915c2-104">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915c2-105">構文</span><span class="sxs-lookup"><span data-stu-id="915c2-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="915c2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="915c2-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="915c2-107">[in] アンロードするアプリケーション ドメインの数値識別子。</span><span class="sxs-lookup"><span data-stu-id="915c2-107">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="915c2-108">[in] アプリケーション ドメインのアンロードを試行する前に、アプリケーションの現在のスレッドの実行が完了するまで共通言語ランタイム (CLR) を待機させる必要がある場合は、`true` を指定します。</span><span class="sxs-lookup"><span data-stu-id="915c2-108">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="915c2-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="915c2-109">Return Value</span></span>  
  
|<span data-ttu-id="915c2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="915c2-110">HRESULT</span></span>|<span data-ttu-id="915c2-111">説明</span><span class="sxs-lookup"><span data-stu-id="915c2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="915c2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="915c2-112">S_OK</span></span>|<span data-ttu-id="915c2-113">`UnloadAppDomain` が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="915c2-113">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="915c2-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="915c2-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="915c2-115">CLR がプロセスに読み込まれていない、または CLR が、マネージド コードを実行したり呼び出しを正常に処理したりできない状態にあります。</span><span class="sxs-lookup"><span data-stu-id="915c2-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="915c2-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="915c2-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="915c2-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="915c2-117">The call timed out.</span></span>|  
|<span data-ttu-id="915c2-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="915c2-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="915c2-119">呼び出し元はロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="915c2-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="915c2-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="915c2-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="915c2-121">ブロックされたスレッドまたはファイバーが待機しているイベントがキャンセルされました。</span><span class="sxs-lookup"><span data-stu-id="915c2-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="915c2-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="915c2-122">E_FAIL</span></span>|<span data-ttu-id="915c2-123">不明な壊滅的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="915c2-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="915c2-124">メソッドで E_FAIL が返される場合、CLR をプロセス内で使用することはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="915c2-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="915c2-125">ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="915c2-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="915c2-126">解説</span><span class="sxs-lookup"><span data-stu-id="915c2-126">Remarks</span></span>  

 <span data-ttu-id="915c2-127">現在のスレッドが実行されているアプリケーション ドメインの数値識別子は、[GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md) を呼び出すことで取得できます。</span><span class="sxs-lookup"><span data-stu-id="915c2-127">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="915c2-128">この識別子は、マネージド <xref:System.AppDomain> 型の <xref:System.AppDomain.Id%2A> プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="915c2-128">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="915c2-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="915c2-129">Requirements</span></span>  

 <span data-ttu-id="915c2-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="915c2-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="915c2-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="915c2-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="915c2-132">**ライブラリ:** リソースとして MSCorEE.dll に含まれている</span><span class="sxs-lookup"><span data-stu-id="915c2-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="915c2-133">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="915c2-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915c2-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="915c2-134">See also</span></span>

- [<span data-ttu-id="915c2-135">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="915c2-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

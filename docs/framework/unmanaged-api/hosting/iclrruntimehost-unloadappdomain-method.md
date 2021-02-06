---
description: '詳細について: ICLRRuntimeHost:: UnloadAppDomain メソッド'
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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637288"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="3de19-103">ICLRRuntimeHost::UnloadAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="3de19-103">ICLRRuntimeHost::UnloadAppDomain Method</span></span>

<span data-ttu-id="3de19-104"><xref:System.AppDomain>指定した数値識別子に対応するマネージをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="3de19-104">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de19-105">構文</span><span class="sxs-lookup"><span data-stu-id="3de19-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3de19-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3de19-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="3de19-107">からアンロードするアプリケーションドメインの数値識別子。</span><span class="sxs-lookup"><span data-stu-id="3de19-107">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="3de19-108">[入力] `true` アプリケーションドメインのアンロードを試行する前に、共通言語ランタイム (CLR) がアプリケーションの現在のスレッドの実行を完了するまで待機する必要があることを示す場合は。</span><span class="sxs-lookup"><span data-stu-id="3de19-108">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3de19-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="3de19-109">Return Value</span></span>  
  
|<span data-ttu-id="3de19-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3de19-110">HRESULT</span></span>|<span data-ttu-id="3de19-111">説明</span><span class="sxs-lookup"><span data-stu-id="3de19-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3de19-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3de19-112">S_OK</span></span>|<span data-ttu-id="3de19-113">`UnloadAppDomain` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="3de19-113">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="3de19-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3de19-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3de19-115">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="3de19-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3de19-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3de19-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3de19-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3de19-117">The call timed out.</span></span>|  
|<span data-ttu-id="3de19-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3de19-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3de19-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3de19-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3de19-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3de19-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3de19-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="3de19-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3de19-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3de19-122">E_FAIL</span></span>|<span data-ttu-id="3de19-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3de19-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3de19-124">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3de19-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3de19-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="3de19-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3de19-126">解説</span><span class="sxs-lookup"><span data-stu-id="3de19-126">Remarks</span></span>  

 <span data-ttu-id="3de19-127">[GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md)を呼び出すことにより、現在のスレッドが実行されているアプリケーションドメインの数値識別子を取得できます。</span><span class="sxs-lookup"><span data-stu-id="3de19-127">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="3de19-128">この識別子は <xref:System.AppDomain.Id%2A> 、マネージ型のプロパティに対応 <xref:System.AppDomain> しています。</span><span class="sxs-lookup"><span data-stu-id="3de19-128">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3de19-129">要件</span><span class="sxs-lookup"><span data-stu-id="3de19-129">Requirements</span></span>  

 <span data-ttu-id="3de19-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3de19-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3de19-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3de19-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3de19-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3de19-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3de19-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3de19-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de19-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="3de19-134">See also</span></span>

- [<span data-ttu-id="3de19-135">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3de19-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

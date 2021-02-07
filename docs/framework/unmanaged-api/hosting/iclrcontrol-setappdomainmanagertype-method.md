---
description: '詳細について: ICLRControl:: SetAppDomainManagerType メソッド'
title: ICLRControl::SetAppDomainManagerType メソッド
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
ms.openlocfilehash: 20d45a0ab14904c778a6ea821fcd63f85b6b0921
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716667"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="4f631-103">ICLRControl::SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="4f631-103">ICLRControl::SetAppDomainManagerType Method</span></span>

<span data-ttu-id="4f631-104">から派生した型を、 <xref:System.AppDomainManager> アプリケーションドメインマネージャーの型として設定します。</span><span class="sxs-lookup"><span data-stu-id="4f631-104">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f631-105">構文</span><span class="sxs-lookup"><span data-stu-id="4f631-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f631-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f631-106">Parameters</span></span>  

 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="4f631-107">からから派生した、要求された型が実装されているアセンブリの名前 <xref:System.AppDomainManager> 。</span><span class="sxs-lookup"><span data-stu-id="4f631-107">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="4f631-108">から `pwzAppDomainManagerAssembly` の機能を実装するパラメーターに実装されている型の名前 <xref:System.AppDomainManager> 。</span><span class="sxs-lookup"><span data-stu-id="4f631-108">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f631-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="4f631-109">Return Value</span></span>  
  
|<span data-ttu-id="4f631-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f631-110">HRESULT</span></span>|<span data-ttu-id="4f631-111">説明</span><span class="sxs-lookup"><span data-stu-id="4f631-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f631-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4f631-112">S_OK</span></span>|<span data-ttu-id="4f631-113">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="4f631-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="4f631-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4f631-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4f631-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="4f631-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4f631-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4f631-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4f631-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4f631-117">The call timed out.</span></span>|  
|<span data-ttu-id="4f631-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4f631-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4f631-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4f631-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4f631-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4f631-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4f631-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="4f631-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4f631-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4f631-122">E_FAIL</span></span>|<span data-ttu-id="4f631-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4f631-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4f631-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="4f631-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4f631-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="4f631-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f631-126">要件</span><span class="sxs-lookup"><span data-stu-id="4f631-126">Requirements</span></span>  

 <span data-ttu-id="4f631-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f631-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f631-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4f631-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f631-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4f631-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f631-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f631-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f631-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f631-131">See also</span></span>

- [<span data-ttu-id="4f631-132">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f631-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="4f631-133">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f631-133">IHostControl Interface</span></span>](ihostcontrol-interface.md)

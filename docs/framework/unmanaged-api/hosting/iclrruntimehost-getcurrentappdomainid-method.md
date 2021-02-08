---
description: '詳細について: ICLRRuntimeHost:: GetCurrentAppDomainId メソッド'
title: ICLRRuntimeHost::GetCurrentAppDomainId メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
ms.openlocfilehash: 88d5288e2e8ee7d8d1f5430261e21052334240be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799728"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="724ce-103">ICLRRuntimeHost::GetCurrentAppDomainId メソッド</span><span class="sxs-lookup"><span data-stu-id="724ce-103">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>

<span data-ttu-id="724ce-104">現在実行中のの数値識別子を取得し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="724ce-104">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="724ce-105">構文</span><span class="sxs-lookup"><span data-stu-id="724ce-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="724ce-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="724ce-106">Parameters</span></span>  

 `pdwAppDomainId`  
 <span data-ttu-id="724ce-107">入出力現在実行中のの数値識別子 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="724ce-107">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="724ce-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="724ce-108">Return Value</span></span>  
  
|<span data-ttu-id="724ce-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="724ce-109">HRESULT</span></span>|<span data-ttu-id="724ce-110">説明</span><span class="sxs-lookup"><span data-stu-id="724ce-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="724ce-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="724ce-111">S_OK</span></span>|<span data-ttu-id="724ce-112">`GetCurrentAppDomainId` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="724ce-112">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="724ce-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="724ce-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="724ce-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="724ce-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="724ce-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="724ce-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="724ce-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="724ce-116">The call timed out.</span></span>|  
|<span data-ttu-id="724ce-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="724ce-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="724ce-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="724ce-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="724ce-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="724ce-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="724ce-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="724ce-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="724ce-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="724ce-121">E_FAIL</span></span>|<span data-ttu-id="724ce-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="724ce-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="724ce-123">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="724ce-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="724ce-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="724ce-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="724ce-125">解説</span><span class="sxs-lookup"><span data-stu-id="724ce-125">Remarks</span></span>  

 <span data-ttu-id="724ce-126">`pdwAppDomainId`パラメーターは <xref:System.AppDomain.Id%2A> 、 <xref:System.AppDomain> 現在のスレッドが実行されているのプロパティの値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="724ce-126">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="724ce-127">要件</span><span class="sxs-lookup"><span data-stu-id="724ce-127">Requirements</span></span>  

 <span data-ttu-id="724ce-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="724ce-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="724ce-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="724ce-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="724ce-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="724ce-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="724ce-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="724ce-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724ce-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="724ce-132">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="724ce-133">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="724ce-133">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

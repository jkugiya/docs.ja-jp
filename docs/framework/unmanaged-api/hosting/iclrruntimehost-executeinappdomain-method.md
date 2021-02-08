---
description: '詳細については、次を参照してください: ICLRRuntimeHost:: ExecuteInAppDomain メソッド'
title: ICLRRuntimeHost::ExecuteInAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
ms.openlocfilehash: 6640713b55e05817f39af819d5e41ee1f2a10b68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799747"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="6f05f-103">ICLRRuntimeHost::ExecuteInAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="6f05f-103">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>

<span data-ttu-id="6f05f-104">指定し <xref:System.AppDomain> たマネージコードを実行するを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f05f-104">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f05f-105">構文</span><span class="sxs-lookup"><span data-stu-id="6f05f-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f05f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6f05f-106">Parameters</span></span>  

 `AppDomainId`  
 <span data-ttu-id="6f05f-107">から <xref:System.AppDomain> 指定したメソッドを実行するの数値 ID。</span><span class="sxs-lookup"><span data-stu-id="6f05f-107">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="6f05f-108">から指定した内で実行する関数へのポインター <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="6f05f-108">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="6f05f-109">から非透過的な呼び出し元に割り当てられたメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6f05f-109">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="6f05f-110">このパラメーターは、共通言語ランタイム (CLR) によってドメインコールバックに渡されます。</span><span class="sxs-lookup"><span data-stu-id="6f05f-110">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="6f05f-111">ランタイムによって管理されるヒープメモリではありません。このメモリの割り当てと有効期間は、どちらも呼び出し元によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="6f05f-111">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f05f-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="6f05f-112">Return Value</span></span>  
  
|<span data-ttu-id="6f05f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f05f-113">HRESULT</span></span>|<span data-ttu-id="6f05f-114">説明</span><span class="sxs-lookup"><span data-stu-id="6f05f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f05f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f05f-115">S_OK</span></span>|<span data-ttu-id="6f05f-116">`ExecuteInAppDomain` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="6f05f-116">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="6f05f-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f05f-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f05f-118">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6f05f-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f05f-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f05f-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f05f-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6f05f-120">The call timed out.</span></span>|  
|<span data-ttu-id="6f05f-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f05f-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f05f-122">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6f05f-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f05f-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f05f-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f05f-124">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="6f05f-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f05f-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f05f-125">E_FAIL</span></span>|<span data-ttu-id="6f05f-126">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6f05f-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f05f-127">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6f05f-127">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f05f-128">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6f05f-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f05f-129">解説</span><span class="sxs-lookup"><span data-stu-id="6f05f-129">Remarks</span></span>  

 <span data-ttu-id="6f05f-130">`ExecuteInAppDomain` 指定したマネージメソッドを実行する管理対象をホストで制御できるように <xref:System.AppDomain> します。</span><span class="sxs-lookup"><span data-stu-id="6f05f-130">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="6f05f-131">アプリケーションドメインの識別子の値を取得できます。これは、 <xref:System.AppDomain.Id%2A> [GetCurrentAppDomainId メソッド](iclrruntimehost-getcurrentappdomainid-method.md)を呼び出すことによって、プロパティの値に対応します。</span><span class="sxs-lookup"><span data-stu-id="6f05f-131">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f05f-132">要件</span><span class="sxs-lookup"><span data-stu-id="6f05f-132">Requirements</span></span>  

 <span data-ttu-id="6f05f-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f05f-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f05f-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6f05f-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f05f-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6f05f-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f05f-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f05f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f05f-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f05f-137">See also</span></span>

- [<span data-ttu-id="6f05f-138">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f05f-138">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

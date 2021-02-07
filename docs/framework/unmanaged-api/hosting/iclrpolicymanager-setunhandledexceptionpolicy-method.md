---
description: '詳細について: ICLRPolicyManager:: SetUnhandledExceptionPolicy メソッド'
title: ICLRPolicyManager::SetUnhandledExceptionPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
ms.openlocfilehash: 489127bb00b2b65466460baa3cfd31439672cd1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716538"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="4bdff-103">ICLRPolicyManager::SetUnhandledExceptionPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="4bdff-103">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>

<span data-ttu-id="4bdff-104">未処理の例外が発生した場合の共通言語ランタイム (CLR) の動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="4bdff-104">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdff-105">構文</span><span class="sxs-lookup"><span data-stu-id="4bdff-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bdff-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4bdff-106">Parameters</span></span>  

 `policy`  
 <span data-ttu-id="4bdff-107">から [EClrUnhandledException](eclrunhandledexception-enumeration.md) 値の1つ。動作が CLR またはホストによって設定されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4bdff-107">[in] One of the [EClrUnhandledException](eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bdff-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="4bdff-108">Return Value</span></span>  
  
|<span data-ttu-id="4bdff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bdff-109">HRESULT</span></span>|<span data-ttu-id="4bdff-110">説明</span><span class="sxs-lookup"><span data-stu-id="4bdff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bdff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bdff-111">S_OK</span></span>|<span data-ttu-id="4bdff-112">`SetUnhandledExceptionPolicy` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="4bdff-112">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="4bdff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4bdff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4bdff-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="4bdff-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4bdff-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4bdff-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4bdff-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4bdff-116">The call timed out.</span></span>|  
|<span data-ttu-id="4bdff-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4bdff-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4bdff-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4bdff-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4bdff-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4bdff-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4bdff-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="4bdff-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4bdff-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4bdff-121">E_FAIL</span></span>|<span data-ttu-id="4bdff-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4bdff-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4bdff-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="4bdff-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4bdff-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="4bdff-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bdff-125">解説</span><span class="sxs-lookup"><span data-stu-id="4bdff-125">Remarks</span></span>  

 <span data-ttu-id="4bdff-126">既定では、CLR はすべてのハンドルされない例外の最終的なハンドラーであり、既定の動作では、プロセスが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="4bdff-126">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="4bdff-127">ホストはこの動作を変更できます。そのためには、 `policy` 値を Ehost決定 Edpolicy に設定します。</span><span class="sxs-lookup"><span data-stu-id="4bdff-127">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="4bdff-128">この値により、ホストは、以前のバージョンの CLR の場合と同様に、独自の既定の動作を実装できます。</span><span class="sxs-lookup"><span data-stu-id="4bdff-128">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bdff-129">要件</span><span class="sxs-lookup"><span data-stu-id="4bdff-129">Requirements</span></span>  

 <span data-ttu-id="4bdff-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bdff-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bdff-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4bdff-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bdff-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4bdff-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bdff-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bdff-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdff-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bdff-134">See also</span></span>

- [<span data-ttu-id="4bdff-135">EClrUnhandledException 列挙型</span><span class="sxs-lookup"><span data-stu-id="4bdff-135">EClrUnhandledException Enumeration</span></span>](eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="4bdff-136">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4bdff-136">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="4bdff-137">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4bdff-137">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="4bdff-138">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4bdff-138">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)

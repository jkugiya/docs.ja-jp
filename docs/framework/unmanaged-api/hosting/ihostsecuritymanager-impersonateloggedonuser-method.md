---
description: '詳細について: IHostSecurityManager:: ImpersonateLoggedOnUser メソッド'
title: IHostSecurityManager::ImpersonateLoggedOnUser メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
ms.openlocfilehash: 7b77e0a163551a48629898b1311fc19ba815aaf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671582"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="318d9-103">IHostSecurityManager::ImpersonateLoggedOnUser メソッド</span><span class="sxs-lookup"><span data-stu-id="318d9-103">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>

<span data-ttu-id="318d9-104">現在のユーザー id の資格情報を使用して、コードの実行を要求します。</span><span class="sxs-lookup"><span data-stu-id="318d9-104">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="318d9-105">構文</span><span class="sxs-lookup"><span data-stu-id="318d9-105">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="318d9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="318d9-106">Parameters</span></span>  

 `hToken`  
 <span data-ttu-id="318d9-107">から権限を借用するユーザーの資格情報を表すトークン。</span><span class="sxs-lookup"><span data-stu-id="318d9-107">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="318d9-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="318d9-108">Return Value</span></span>  
  
|<span data-ttu-id="318d9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="318d9-109">HRESULT</span></span>|<span data-ttu-id="318d9-110">説明</span><span class="sxs-lookup"><span data-stu-id="318d9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="318d9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="318d9-111">S_OK</span></span>|<span data-ttu-id="318d9-112">`ImpersonateLoggedOnUser` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="318d9-112">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="318d9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="318d9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="318d9-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="318d9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="318d9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="318d9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="318d9-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="318d9-116">The call timed out.</span></span>|  
|<span data-ttu-id="318d9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="318d9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="318d9-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="318d9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="318d9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="318d9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="318d9-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="318d9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="318d9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="318d9-121">E_FAIL</span></span>|<span data-ttu-id="318d9-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="318d9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="318d9-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="318d9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="318d9-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="318d9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="318d9-125">解説</span><span class="sxs-lookup"><span data-stu-id="318d9-125">Remarks</span></span>  

 <span data-ttu-id="318d9-126">を呼び出す `LogonUser` か、または関連する Win32 関数を呼び出して、現在のユーザー id の資格情報を識別するハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="318d9-126">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="318d9-127">`HANDLE`この型は COM に準拠していません。つまり、そのサイズはオペレーティングシステムに固有であり、カスタムマーシャリングが必要です。</span><span class="sxs-lookup"><span data-stu-id="318d9-127">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="318d9-128">したがって、このトークンは、CLR とホストの間でプロセス内でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="318d9-128">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="318d9-129">要件</span><span class="sxs-lookup"><span data-stu-id="318d9-129">Requirements</span></span>  

 <span data-ttu-id="318d9-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="318d9-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="318d9-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="318d9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="318d9-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="318d9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="318d9-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="318d9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="318d9-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="318d9-134">See also</span></span>

- [<span data-ttu-id="318d9-135">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="318d9-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="318d9-136">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="318d9-136">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="318d9-137">RevertToSelf メソッド</span><span class="sxs-lookup"><span data-stu-id="318d9-137">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)

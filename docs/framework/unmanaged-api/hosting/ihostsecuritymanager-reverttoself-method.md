---
description: '詳細について: IHostSecurityManager:: RevertToSelf メソッド'
title: IHostSecurityManager::RevertToSelf メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
ms.openlocfilehash: f3488653bcb498c7521de0e368b33bc444967f21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671504"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="2dcab-103">IHostSecurityManager::RevertToSelf メソッド</span><span class="sxs-lookup"><span data-stu-id="2dcab-103">IHostSecurityManager::RevertToSelf Method</span></span>

<span data-ttu-id="2dcab-104">現在のユーザー id の偽装を終了し、元のスレッドトークンを返します。</span><span class="sxs-lookup"><span data-stu-id="2dcab-104">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dcab-105">構文</span><span class="sxs-lookup"><span data-stu-id="2dcab-105">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2dcab-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="2dcab-106">Return Value</span></span>  
  
|<span data-ttu-id="2dcab-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2dcab-107">HRESULT</span></span>|<span data-ttu-id="2dcab-108">説明</span><span class="sxs-lookup"><span data-stu-id="2dcab-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2dcab-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="2dcab-109">S_OK</span></span>|<span data-ttu-id="2dcab-110">`RevertToSelf` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="2dcab-110">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="2dcab-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2dcab-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2dcab-112">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="2dcab-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2dcab-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2dcab-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2dcab-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2dcab-114">The call timed out.</span></span>|  
|<span data-ttu-id="2dcab-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2dcab-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2dcab-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2dcab-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2dcab-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2dcab-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2dcab-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="2dcab-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2dcab-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2dcab-119">E_FAIL</span></span>|<span data-ttu-id="2dcab-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2dcab-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2dcab-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="2dcab-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2dcab-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="2dcab-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dcab-123">解説</span><span class="sxs-lookup"><span data-stu-id="2dcab-123">Remarks</span></span>  

 <span data-ttu-id="2dcab-124">`RevertToSelf` は、 [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) メソッドを以前に呼び出した後、元のスレッドトークンに戻るために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2dcab-124">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dcab-125">要件</span><span class="sxs-lookup"><span data-stu-id="2dcab-125">Requirements</span></span>  

 <span data-ttu-id="2dcab-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dcab-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dcab-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2dcab-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2dcab-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2dcab-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2dcab-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dcab-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dcab-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="2dcab-130">See also</span></span>

- [<span data-ttu-id="2dcab-131">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2dcab-131">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="2dcab-132">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2dcab-132">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="2dcab-133">ImpersonateLoggedOnUser メソッド</span><span class="sxs-lookup"><span data-stu-id="2dcab-133">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)

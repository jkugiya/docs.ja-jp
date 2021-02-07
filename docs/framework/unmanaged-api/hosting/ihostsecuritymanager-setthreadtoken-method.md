---
description: '詳細について: IHostSecurityManager:: SetThreadToken メソッド'
title: IHostSecurityManager::SetThreadToken メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
ms.openlocfilehash: 96fb8d487cecc0e62d9b7787c686c74898d99d70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671387"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="22c61-103">IHostSecurityManager::SetThreadToken メソッド</span><span class="sxs-lookup"><span data-stu-id="22c61-103">IHostSecurityManager::SetThreadToken Method</span></span>

<span data-ttu-id="22c61-104">現在実行中のスレッドのハンドルを設定します。</span><span class="sxs-lookup"><span data-stu-id="22c61-104">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22c61-105">構文</span><span class="sxs-lookup"><span data-stu-id="22c61-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22c61-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="22c61-106">Parameters</span></span>  

 `hToken`  
 <span data-ttu-id="22c61-107">から現在実行中のスレッドに設定するトークンへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="22c61-107">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22c61-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="22c61-108">Return Value</span></span>  
  
|<span data-ttu-id="22c61-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22c61-109">HRESULT</span></span>|<span data-ttu-id="22c61-110">説明</span><span class="sxs-lookup"><span data-stu-id="22c61-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22c61-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="22c61-111">S_OK</span></span>|<span data-ttu-id="22c61-112">`SetThreadToken` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="22c61-112">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="22c61-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22c61-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22c61-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="22c61-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="22c61-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22c61-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="22c61-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="22c61-116">The call timed out.</span></span>|  
|<span data-ttu-id="22c61-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="22c61-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="22c61-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="22c61-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="22c61-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="22c61-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="22c61-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="22c61-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="22c61-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22c61-121">E_FAIL</span></span>|<span data-ttu-id="22c61-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="22c61-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="22c61-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="22c61-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="22c61-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="22c61-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22c61-125">解説</span><span class="sxs-lookup"><span data-stu-id="22c61-125">Remarks</span></span>  

 <span data-ttu-id="22c61-126">`IHostSecurityManager::SetThreadToken` は、同じ名前の対応する Win32 関数と同じように動作します。ただし、Win32 関数では、呼び出し元が任意のスレッドへのハンドルを渡すことができますが、 `IHostSecurityManager::SetThreadToken` は現在実行中のスレッドにのみトークンを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="22c61-126">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="22c61-127">`HANDLE`型は COM に準拠していません。つまり、そのサイズはオペレーティングシステムに固有であり、カスタムマーシャリングが必要です。</span><span class="sxs-lookup"><span data-stu-id="22c61-127">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="22c61-128">したがって、このトークンは、CLR とホストの間でプロセス内でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="22c61-128">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22c61-129">要件</span><span class="sxs-lookup"><span data-stu-id="22c61-129">Requirements</span></span>  

 <span data-ttu-id="22c61-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22c61-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22c61-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="22c61-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22c61-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="22c61-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22c61-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22c61-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c61-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="22c61-134">See also</span></span>

- [<span data-ttu-id="22c61-135">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22c61-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="22c61-136">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22c61-136">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)

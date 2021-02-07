---
description: '詳細について: IHostSecurityManager:: OpenThreadToken メソッド'
title: IHostSecurityManager::OpenThreadToken メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 9e0273f379f4adcf71396630b367a94c623ae15f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671561"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="f9252-103">IHostSecurityManager::OpenThreadToken メソッド</span><span class="sxs-lookup"><span data-stu-id="f9252-103">IHostSecurityManager::OpenThreadToken Method</span></span>

<span data-ttu-id="f9252-104">現在実行中のスレッドに関連付けられている随意アクセストークンを開きます。</span><span class="sxs-lookup"><span data-stu-id="f9252-104">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9252-105">構文</span><span class="sxs-lookup"><span data-stu-id="f9252-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9252-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9252-106">Parameters</span></span>  

 `dwDesiredAccess`  
 <span data-ttu-id="f9252-107">からスレッドトークンへの要求されたアクセスの種類を指定するアクセス値のマスク。</span><span class="sxs-lookup"><span data-stu-id="f9252-107">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="f9252-108">これらの値は、Win32 関数で定義されてい `OpenThreadToken` ます。</span><span class="sxs-lookup"><span data-stu-id="f9252-108">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="f9252-109">要求されたアクセスの種類は、付与または拒否するアクセスの種類を決定するために、トークンの随意アクセス制御リスト (DACL) に対して調整されます。</span><span class="sxs-lookup"><span data-stu-id="f9252-109">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="f9252-110">[入力] `true` 呼び出し元スレッドのプロセスのセキュリティコンテキストを使用してアクセスチェックを行うように指定する場合は。 `false` 呼び出し元スレッドのセキュリティコンテキストを使用してアクセスチェックを実行するように指定する場合は。</span><span class="sxs-lookup"><span data-stu-id="f9252-110">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="f9252-111">スレッドがクライアントを偽装している場合は、クライアントプロセスのセキュリティコンテキストになります。</span><span class="sxs-lookup"><span data-stu-id="f9252-111">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="f9252-112">入出力新しく開かれたアクセストークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f9252-112">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9252-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9252-113">Return Value</span></span>  
  
|<span data-ttu-id="f9252-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9252-114">HRESULT</span></span>|<span data-ttu-id="f9252-115">説明</span><span class="sxs-lookup"><span data-stu-id="f9252-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9252-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9252-116">S_OK</span></span>|<span data-ttu-id="f9252-117">`OpenThreadToken` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f9252-117">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="f9252-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9252-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9252-119">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f9252-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9252-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9252-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9252-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f9252-121">The call timed out.</span></span>|  
|<span data-ttu-id="f9252-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9252-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9252-123">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f9252-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9252-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9252-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9252-125">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f9252-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9252-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9252-126">E_FAIL</span></span>|<span data-ttu-id="f9252-127">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f9252-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9252-128">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f9252-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9252-129">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f9252-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9252-130">解説</span><span class="sxs-lookup"><span data-stu-id="f9252-130">Remarks</span></span>  

 <span data-ttu-id="f9252-131">`IHostSecurityManager::OpenThreadToken` は、同じ名前の対応する Win32 関数と同じように動作します。ただし、Win32 関数では、呼び出し元が任意のスレッドへのハンドルを渡すことを許可し、 `IHostSecurityManager::OpenThreadToken` は呼び出し元のスレッドに関連付けられたトークンのみを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="f9252-131">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="f9252-132">`HANDLE`この型は COM に準拠していません。つまり、そのサイズはオペレーティングシステムに固有であり、カスタムマーシャリングが必要です。</span><span class="sxs-lookup"><span data-stu-id="f9252-132">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="f9252-133">したがって、このトークンは、CLR とホストの間でプロセス内でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="f9252-133">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9252-134">要件</span><span class="sxs-lookup"><span data-stu-id="f9252-134">Requirements</span></span>  

 <span data-ttu-id="f9252-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9252-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9252-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f9252-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9252-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f9252-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9252-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9252-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9252-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9252-139">See also</span></span>

- [<span data-ttu-id="f9252-140">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9252-140">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="f9252-141">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9252-141">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)

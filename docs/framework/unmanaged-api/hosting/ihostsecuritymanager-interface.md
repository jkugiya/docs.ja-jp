---
description: 詳細については、「IHostSecurityManager インターフェイス」を参照してください。
title: IHostSecurityManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
ms.openlocfilehash: 76ba26443fa2a4e65459dd073eb6d22031548112
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671543"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="c1647-103">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1647-103">IHostSecurityManager Interface</span></span>

<span data-ttu-id="c1647-104">現在実行中のスレッドのセキュリティコンテキストに対するアクセスと制御を許可するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c1647-104">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1647-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c1647-105">Methods</span></span>  
  
|<span data-ttu-id="c1647-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c1647-106">Method</span></span>|<span data-ttu-id="c1647-107">説明</span><span class="sxs-lookup"><span data-stu-id="c1647-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1647-108">GetSecurityContext メソッド</span><span class="sxs-lookup"><span data-stu-id="c1647-108">GetSecurityContext Method</span></span>](ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="c1647-109">ホストから要求された [IHostSecurityContext](ihostsecuritycontext-interface.md) を取得します。</span><span class="sxs-lookup"><span data-stu-id="c1647-109">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="c1647-110">ImpersonateLoggedOnUser メソッド</span><span class="sxs-lookup"><span data-stu-id="c1647-110">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="c1647-111">現在のユーザー id の資格情報を使用して、コードの実行を要求します。</span><span class="sxs-lookup"><span data-stu-id="c1647-111">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="c1647-112">OpenThreadToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c1647-112">OpenThreadToken Method</span></span>](ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="c1647-113">現在のスレッドに関連付けられている随意アクセストークンを開きます。</span><span class="sxs-lookup"><span data-stu-id="c1647-113">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="c1647-114">RevertToSelf メソッド</span><span class="sxs-lookup"><span data-stu-id="c1647-114">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="c1647-115">現在のユーザー id の偽装を終了し、元のスレッドトークンを返します。</span><span class="sxs-lookup"><span data-stu-id="c1647-115">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="c1647-116">SetSecurityContext メソッド</span><span class="sxs-lookup"><span data-stu-id="c1647-116">SetSecurityContext Method</span></span>](ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="c1647-117">現在実行中のスレッドのセキュリティコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="c1647-117">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="c1647-118">SetThreadToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c1647-118">SetThreadToken Method</span></span>](ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="c1647-119">現在実行中のスレッドのハンドルを設定します。</span><span class="sxs-lookup"><span data-stu-id="c1647-119">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1647-120">解説</span><span class="sxs-lookup"><span data-stu-id="c1647-120">Remarks</span></span>  

 <span data-ttu-id="c1647-121">ホストは、共通言語ランタイム (CLR) とユーザーコードの両方によって、スレッドトークンへのすべてのコードアクセスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="c1647-121">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="c1647-122">また、完全なセキュリティコンテキスト情報が、制限されたコードアクセスで非同期操作またはコードポイント全体に渡されるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c1647-122">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="c1647-123">`IHostSecurityContext` CLR に対して非透過的なこのセキュリティコンテキスト情報をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="c1647-123">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="c1647-124">CLR は、マネージスレッドコンテキストを内部で処理します。</span><span class="sxs-lookup"><span data-stu-id="c1647-124">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="c1647-125">次のような状況で、プロセス固有のクエリが実行され `IHostSecurityManager` ます。</span><span class="sxs-lookup"><span data-stu-id="c1647-125">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="c1647-126">ファイナライザーの実行中に発生します。</span><span class="sxs-lookup"><span data-stu-id="c1647-126">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="c1647-127">クラスおよびモジュールコンストラクターの実行中。</span><span class="sxs-lookup"><span data-stu-id="c1647-127">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="c1647-128">ワーカースレッドの非同期ポイントで、 [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c1647-128">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="c1647-129">I/o 完了ポートのサービス。</span><span class="sxs-lookup"><span data-stu-id="c1647-129">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1647-130">要件</span><span class="sxs-lookup"><span data-stu-id="c1647-130">Requirements</span></span>  

 <span data-ttu-id="c1647-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1647-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1647-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c1647-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1647-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c1647-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1647-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1647-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1647-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1647-135">See also</span></span>

- [<span data-ttu-id="c1647-136">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1647-136">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="c1647-137">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1647-137">Hosting Interfaces</span></span>](hosting-interfaces.md)

---
description: '詳細について: IHostSecurityManager:: GetSecurityContext メソッド'
title: IHostSecurityManager::GetSecurityContext メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
ms.openlocfilehash: 0dc9e0380d2fb218b68f6beb85fa1ccba8826d85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671565"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="11c94-103">IHostSecurityManager::GetSecurityContext メソッド</span><span class="sxs-lookup"><span data-stu-id="11c94-103">IHostSecurityManager::GetSecurityContext Method</span></span>

<span data-ttu-id="11c94-104">ホストから要求された [IHostSecurityContext](ihostsecuritycontext-interface.md) を取得します。</span><span class="sxs-lookup"><span data-stu-id="11c94-104">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c94-105">構文</span><span class="sxs-lookup"><span data-stu-id="11c94-105">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11c94-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11c94-106">Parameters</span></span>  

 `eContextType`  
 <span data-ttu-id="11c94-107">から [EContextType](econtexttype-enumeration.md) 値の1つ。返されるセキュリティコンテキストの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="11c94-107">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="11c94-108">入出力のへのインターフェイスポインターのアドレス `IHostSecurityContext` `eContextType` 。</span><span class="sxs-lookup"><span data-stu-id="11c94-108">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11c94-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="11c94-109">Return Value</span></span>  
  
|<span data-ttu-id="11c94-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11c94-110">HRESULT</span></span>|<span data-ttu-id="11c94-111">説明</span><span class="sxs-lookup"><span data-stu-id="11c94-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11c94-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="11c94-112">S_OK</span></span>|<span data-ttu-id="11c94-113">`GetSecurityContext` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="11c94-113">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="11c94-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11c94-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11c94-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="11c94-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11c94-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11c94-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11c94-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="11c94-117">The call timed out.</span></span>|  
|<span data-ttu-id="11c94-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11c94-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11c94-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="11c94-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11c94-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11c94-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11c94-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="11c94-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11c94-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11c94-122">E_FAIL</span></span>|<span data-ttu-id="11c94-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="11c94-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11c94-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="11c94-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11c94-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="11c94-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11c94-126">解説</span><span class="sxs-lookup"><span data-stu-id="11c94-126">Remarks</span></span>  

 <span data-ttu-id="11c94-127">ホストは、CLR とユーザーコードの両方によって、スレッドトークンへのすべてのコードアクセスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="11c94-127">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="11c94-128">また、完全なセキュリティコンテキスト情報が、制限されたコードアクセスで非同期操作またはコードポイント全体に渡されるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="11c94-128">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="11c94-129">`IHostSecurityContext` CLR に対して非透過的なこのセキュリティコンテキスト情報をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="11c94-129">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="11c94-130">CLR は、この情報をキャプチャし、スレッドプールのワーカー項目のディスパッチ、ファイナライザーの実行、およびモジュールとクラスの構築の間で移動します。</span><span class="sxs-lookup"><span data-stu-id="11c94-130">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c94-131">要件</span><span class="sxs-lookup"><span data-stu-id="11c94-131">Requirements</span></span>  

 <span data-ttu-id="11c94-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11c94-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c94-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="11c94-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11c94-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="11c94-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11c94-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c94-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c94-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="11c94-136">See also</span></span>

- [<span data-ttu-id="11c94-137">EContextType 列挙型</span><span class="sxs-lookup"><span data-stu-id="11c94-137">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="11c94-138">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11c94-138">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="11c94-139">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11c94-139">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)

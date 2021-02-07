---
description: '詳細について: IHostSecurityContext:: Capture メソッド'
title: IHostSecurityContext::Capture メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
ms.openlocfilehash: d46bbae7b94dcad6d1356243c938c9d3690f26a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671712"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="503bc-103">IHostSecurityContext::Capture メソッド</span><span class="sxs-lookup"><span data-stu-id="503bc-103">IHostSecurityContext::Capture Method</span></span>

<span data-ttu-id="503bc-104">[IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md)への呼び出しから返された[IHostSecurityContext](ihostsecuritycontext-interface.md)インスタンスの複製を取得します。</span><span class="sxs-lookup"><span data-stu-id="503bc-104">Gets a clone of the [IHostSecurityContext](ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="503bc-105">構文</span><span class="sxs-lookup"><span data-stu-id="503bc-105">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="503bc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="503bc-106">Parameters</span></span>  

 `ppClonedContext`  
 <span data-ttu-id="503bc-107">入出力キャプチャするオブジェクトの複製のアドレスへのポインター `IHostSecurityContext` 。</span><span class="sxs-lookup"><span data-stu-id="503bc-107">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="503bc-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="503bc-108">Return Value</span></span>  
  
|<span data-ttu-id="503bc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="503bc-109">HRESULT</span></span>|<span data-ttu-id="503bc-110">説明</span><span class="sxs-lookup"><span data-stu-id="503bc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="503bc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="503bc-111">S_OK</span></span>|<span data-ttu-id="503bc-112">`Capture` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="503bc-112">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="503bc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="503bc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="503bc-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="503bc-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="503bc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="503bc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="503bc-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="503bc-116">The call timed out.</span></span>|  
|<span data-ttu-id="503bc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="503bc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="503bc-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="503bc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="503bc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="503bc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="503bc-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="503bc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="503bc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="503bc-121">E_FAIL</span></span>|<span data-ttu-id="503bc-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="503bc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="503bc-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="503bc-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="503bc-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="503bc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="503bc-125">解説</span><span class="sxs-lookup"><span data-stu-id="503bc-125">Remarks</span></span>  

 <span data-ttu-id="503bc-126">から返されるインターフェイスポインター `Capture` は、キャプチャされたコンテキストの複製です。</span><span class="sxs-lookup"><span data-stu-id="503bc-126">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="503bc-127">この情報が非同期コードポイント間で移動されると、その有効期間は、呼び出しが行われたポインターとは分離されます。</span><span class="sxs-lookup"><span data-stu-id="503bc-127">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="503bc-128">したがって、元のポインターは解放できます。</span><span class="sxs-lookup"><span data-stu-id="503bc-128">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="503bc-129">要件</span><span class="sxs-lookup"><span data-stu-id="503bc-129">Requirements</span></span>  

 <span data-ttu-id="503bc-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="503bc-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="503bc-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="503bc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="503bc-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="503bc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="503bc-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="503bc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503bc-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="503bc-134">See also</span></span>

- [<span data-ttu-id="503bc-135">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="503bc-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="503bc-136">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="503bc-136">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)

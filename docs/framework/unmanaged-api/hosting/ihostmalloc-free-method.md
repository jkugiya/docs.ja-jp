---
description: '詳細について: IHostMAlloc:: Free メソッド'
title: IHostMAlloc::Free メソッド
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
ms.openlocfilehash: 097e2e95b6dfb9d6a1bae68f9e0455a96383159e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708204"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="0054b-103">IHostMAlloc::Free メソッド</span><span class="sxs-lookup"><span data-stu-id="0054b-103">IHostMAlloc::Free Method</span></span>

<span data-ttu-id="0054b-104">[Alloc](ihostmalloc-alloc-method.md)関数を使用して割り当てられたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="0054b-104">Frees memory that was allocated by using the [Alloc](ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0054b-105">構文</span><span class="sxs-lookup"><span data-stu-id="0054b-105">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0054b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0054b-106">Parameters</span></span>  

 `pMem`  
 <span data-ttu-id="0054b-107">から解放するメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0054b-107">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0054b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0054b-108">Return Value</span></span>  
  
|<span data-ttu-id="0054b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0054b-109">HRESULT</span></span>|<span data-ttu-id="0054b-110">説明</span><span class="sxs-lookup"><span data-stu-id="0054b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0054b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0054b-111">S_OK</span></span>|<span data-ttu-id="0054b-112">`Free` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="0054b-112">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="0054b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0054b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0054b-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="0054b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0054b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0054b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0054b-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0054b-116">The call timed out.</span></span>|  
|<span data-ttu-id="0054b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0054b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0054b-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0054b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0054b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0054b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0054b-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="0054b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0054b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0054b-121">E_FAIL</span></span>|<span data-ttu-id="0054b-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0054b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0054b-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="0054b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0054b-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="0054b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0054b-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="0054b-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="0054b-126">ホストを通じて割り当てられていないメモリを解放しようとしました。</span><span class="sxs-lookup"><span data-stu-id="0054b-126">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0054b-127">解説</span><span class="sxs-lookup"><span data-stu-id="0054b-127">Remarks</span></span>  

 <span data-ttu-id="0054b-128">パラメーターが、 `pMem` の呼び出しを使用して割り当てられていないメモリ領域を参照している場合 `Alloc` 、ホストは HOST_E_INVALIDOPERATION を返します。</span><span class="sxs-lookup"><span data-stu-id="0054b-128">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0054b-129">要件</span><span class="sxs-lookup"><span data-stu-id="0054b-129">Requirements</span></span>  

 <span data-ttu-id="0054b-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0054b-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0054b-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0054b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0054b-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0054b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0054b-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0054b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0054b-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="0054b-134">See also</span></span>

- [<span data-ttu-id="0054b-135">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0054b-135">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="0054b-136">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0054b-136">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)

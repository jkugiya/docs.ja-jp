---
description: '詳細について: IHostMAlloc:: Alloc メソッド'
title: IHostMAlloc::Alloc メソッド
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
ms.openlocfilehash: e0349c273ef9e3194bb8bad167510dd8fefcab62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708235"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="961f5-103">IHostMAlloc::Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="961f5-103">IHostMAlloc::Alloc Method</span></span>

<span data-ttu-id="961f5-104">ホストが指定された量のメモリをヒープから割り当てることを要求します。</span><span class="sxs-lookup"><span data-stu-id="961f5-104">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="961f5-105">構文</span><span class="sxs-lookup"><span data-stu-id="961f5-105">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="961f5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="961f5-106">Parameters</span></span>  

 `cbSize`  
 <span data-ttu-id="961f5-107">から現在のメモリ割り当て要求のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="961f5-107">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="961f5-108">から割り当てエラーの影響を示す [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="961f5-108">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="961f5-109">入出力割り当てられたメモリへのポインター。要求を完了できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="961f5-109">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="961f5-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="961f5-110">Return Value</span></span>  
  
|<span data-ttu-id="961f5-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="961f5-111">HRESULT</span></span>|<span data-ttu-id="961f5-112">説明</span><span class="sxs-lookup"><span data-stu-id="961f5-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="961f5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="961f5-113">S_OK</span></span>|<span data-ttu-id="961f5-114">`Alloc` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="961f5-114">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="961f5-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="961f5-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="961f5-116">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="961f5-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="961f5-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="961f5-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="961f5-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="961f5-118">The call timed out.</span></span>|  
|<span data-ttu-id="961f5-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="961f5-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="961f5-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="961f5-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="961f5-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="961f5-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="961f5-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="961f5-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="961f5-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="961f5-123">E_FAIL</span></span>|<span data-ttu-id="961f5-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="961f5-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="961f5-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="961f5-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="961f5-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="961f5-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="961f5-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="961f5-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="961f5-128">割り当て要求を完了するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="961f5-128">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="961f5-129">解説</span><span class="sxs-lookup"><span data-stu-id="961f5-129">Remarks</span></span>  

 <span data-ttu-id="961f5-130">CLR は、 `IHostMalloc` [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md) メソッドを呼び出すことによって、インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="961f5-130">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="961f5-131">要件</span><span class="sxs-lookup"><span data-stu-id="961f5-131">Requirements</span></span>  

 <span data-ttu-id="961f5-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="961f5-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="961f5-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="961f5-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="961f5-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="961f5-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="961f5-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="961f5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="961f5-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="961f5-136">See also</span></span>

- [<span data-ttu-id="961f5-137">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="961f5-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="961f5-138">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="961f5-138">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)

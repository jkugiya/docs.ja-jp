---
description: '詳細については、次を参照してください: IHostMAlloc::D E、Alloc メソッド'
title: IHostMAlloc::DebugAlloc メソッド
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: f94ff0d6cc1e25daee12c67c38167f7f14829510
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708217"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="2f2e4-103">IHostMAlloc::DebugAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="2f2e4-103">IHostMAlloc::DebugAlloc Method</span></span>

<span data-ttu-id="2f2e4-104">ホストがヒープから指定された量のメモリを割り当て、さらにメモリが割り当てられた場所を追跡するように要求します。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-104">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f2e4-105">構文</span><span class="sxs-lookup"><span data-stu-id="2f2e4-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f2e4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f2e4-106">Parameters</span></span>  

 `cbSize`  
 <span data-ttu-id="2f2e4-107">から現在のメモリ割り当て要求のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-107">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="2f2e4-108">から割り当てエラーの影響を示す [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-108">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="2f2e4-109">からデバッグ中の実行可能ファイルのコードファイル。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-109">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="2f2e4-110">から割り当てが要求されたの行番号 `pszFileName` 。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-110">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="2f2e4-111">入出力割り当てられたメモリへのポインター。要求を完了できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-111">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f2e4-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="2f2e4-112">Return Value</span></span>  
  
|<span data-ttu-id="2f2e4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f2e4-113">HRESULT</span></span>|<span data-ttu-id="2f2e4-114">説明</span><span class="sxs-lookup"><span data-stu-id="2f2e4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f2e4-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f2e4-115">S_OK</span></span>|<span data-ttu-id="2f2e4-116">`DebugAlloc` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-116">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="2f2e4-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f2e4-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f2e4-118">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f2e4-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f2e4-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f2e4-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-120">The call timed out.</span></span>|  
|<span data-ttu-id="2f2e4-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f2e4-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f2e4-122">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f2e4-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f2e4-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f2e4-124">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f2e4-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f2e4-125">E_FAIL</span></span>|<span data-ttu-id="2f2e4-126">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f2e4-127">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f2e4-128">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2f2e4-129">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2f2e4-129">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2f2e4-130">割り当て要求を完了するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-130">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f2e4-131">解説</span><span class="sxs-lookup"><span data-stu-id="2f2e4-131">Remarks</span></span>  

 <span data-ttu-id="2f2e4-132">CLR は、 [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md)メソッドを呼び出すことによって、 [IHostMalloc](ihostmalloc-interface.md)インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-132">The CLR gets an interface pointer to an [IHostMalloc](ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="2f2e4-133">`DebugAlloc` ランタイムがデバッグ中に使用するコードファイルの情報を取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-133">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f2e4-134">要件</span><span class="sxs-lookup"><span data-stu-id="2f2e4-134">Requirements</span></span>  

 <span data-ttu-id="2f2e4-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f2e4-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f2e4-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2f2e4-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f2e4-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2f2e4-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f2e4-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f2e4-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f2e4-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f2e4-139">See also</span></span>

- [<span data-ttu-id="2f2e4-140">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f2e4-140">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="2f2e4-141">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f2e4-141">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)

---
description: '詳細情報: IHostMemoryManager:: VirtualAlloc メソッド'
title: IHostMemoryManager::VirtualAlloc メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
ms.openlocfilehash: 28682aea5e6e7951b3b8f0a9af946a3f3828601b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707851"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="878cc-103">IHostMemoryManager::VirtualAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="878cc-103">IHostMemoryManager::VirtualAlloc Method</span></span>

<span data-ttu-id="878cc-104">対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="878cc-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="878cc-105">の Win32 実装は、 `VirtualAlloc` 呼び出し元プロセスの仮想アドレス空間にあるページの領域を予約またはコミットします。</span><span class="sxs-lookup"><span data-stu-id="878cc-105">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="878cc-106">構文</span><span class="sxs-lookup"><span data-stu-id="878cc-106">Syntax</span></span>  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="878cc-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="878cc-107">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="878cc-108">から割り当てる領域の開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="878cc-108">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="878cc-109">から領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="878cc-109">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="878cc-110">からメモリ割り当ての種類。</span><span class="sxs-lookup"><span data-stu-id="878cc-110">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="878cc-111">から割り当てられるページの領域のメモリ保護。</span><span class="sxs-lookup"><span data-stu-id="878cc-111">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="878cc-112">から割り当てエラーの影響を示す [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) 値です。</span><span class="sxs-lookup"><span data-stu-id="878cc-112">[in] An [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="878cc-113">入出力割り当てられたメモリの開始アドレスへのポインター。要求を満たすことができなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="878cc-113">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="878cc-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="878cc-114">Return Value</span></span>  
  
|<span data-ttu-id="878cc-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="878cc-115">HRESULT</span></span>|<span data-ttu-id="878cc-116">説明</span><span class="sxs-lookup"><span data-stu-id="878cc-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="878cc-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="878cc-117">S_OK</span></span>|<span data-ttu-id="878cc-118">`VirtualAlloc` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="878cc-118">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="878cc-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="878cc-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="878cc-120">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="878cc-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="878cc-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="878cc-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="878cc-122">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="878cc-122">The call timed out.</span></span>|  
|<span data-ttu-id="878cc-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="878cc-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="878cc-124">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="878cc-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="878cc-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="878cc-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="878cc-126">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="878cc-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="878cc-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="878cc-127">E_FAIL</span></span>|<span data-ttu-id="878cc-128">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="878cc-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="878cc-129">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="878cc-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="878cc-130">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="878cc-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="878cc-131">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="878cc-131">E_OUTOFMEMORY</span></span>|<span data-ttu-id="878cc-132">割り当て要求を完了するのに十分なメモリがありませんでした</span><span class="sxs-lookup"><span data-stu-id="878cc-132">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="878cc-133">解説</span><span class="sxs-lookup"><span data-stu-id="878cc-133">Remarks</span></span>  

 <span data-ttu-id="878cc-134">を呼び出して、プロセスのアドレス空間にリージョンを予約し `VirtualAlloc` ます。</span><span class="sxs-lookup"><span data-stu-id="878cc-134">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="878cc-135">パラメーターには、 `pAddress` 必要なメモリブロックの開始アドレスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="878cc-135">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="878cc-136">通常、このパラメーターは null に設定されます。</span><span class="sxs-lookup"><span data-stu-id="878cc-136">This parameter is typically set to null.</span></span> <span data-ttu-id="878cc-137">オペレーティングシステムは、プロセスで使用可能な空きアドレス範囲の記録を保持します。</span><span class="sxs-lookup"><span data-stu-id="878cc-137">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="878cc-138">値が null の場合は、 `pAddress` 必要に応じてリージョンを予約するようにシステムに指示します。</span><span class="sxs-lookup"><span data-stu-id="878cc-138">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="878cc-139">または、メモリブロックの特定の開始アドレスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="878cc-139">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="878cc-140">どちらの場合も、出力パラメーター `ppMem` は、割り当てられたメモリへのポインターとして返されます。</span><span class="sxs-lookup"><span data-stu-id="878cc-140">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="878cc-141">関数自体は HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="878cc-141">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="878cc-142">Win32 関数にはパラメーターがないため、 `VirtualAlloc` `ppMem` 代わりに割り当てられたメモリへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="878cc-142">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="878cc-143">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="878cc-143">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="878cc-144">要件</span><span class="sxs-lookup"><span data-stu-id="878cc-144">Requirements</span></span>  

 <span data-ttu-id="878cc-145">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="878cc-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="878cc-146">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="878cc-146">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="878cc-147">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="878cc-147">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="878cc-148">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="878cc-148">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878cc-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="878cc-149">See also</span></span>

- [<span data-ttu-id="878cc-150">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="878cc-150">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)

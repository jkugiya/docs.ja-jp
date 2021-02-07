---
description: 詳細については、「IHostMemoryManager インターフェイス」を参照してください。
title: IHostMemoryManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: c9b6f83b5c70a53388e886e1047798f660b826e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707884"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="244fc-103">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="244fc-103">IHostMemoryManager Interface</span></span>

<span data-ttu-id="244fc-104">標準の Win32 仮想メモリ関数を使用する代わりに、共通言語ランタイム (CLR) がホストを介して仮想メモリ要求を行うことができるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="244fc-104">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="244fc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-105">Methods</span></span>  
  
|<span data-ttu-id="244fc-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-106">Method</span></span>|<span data-ttu-id="244fc-107">説明</span><span class="sxs-lookup"><span data-stu-id="244fc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="244fc-108">AcquiredVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-108">AcquiredVirtualAddressSpace Method</span></span>](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="244fc-109">共通言語ランタイム (CLR) が、指定されたメモリをオペレーティングシステムから取得したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="244fc-109">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="244fc-110">CreateMAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-110">CreateMAlloc Method</span></span>](ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="244fc-111">ホストによって作成されたヒープからメモリ割り当てを要求するために使用される [IHostMAlloc](ihostmalloc-interface.md) インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="244fc-111">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="244fc-112">GetMemoryLoad メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-112">GetMemoryLoad Method</span></span>](ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="244fc-113">ホストによって報告された、現在使用されている物理メモリの量を取得します。</span><span class="sxs-lookup"><span data-stu-id="244fc-113">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="244fc-114">NeedsVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-114">NeedsVirtualAddressSpace Method</span></span>](ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="244fc-115">CLR が指定されたメモリを使用しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="244fc-115">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="244fc-116">RegisterMemoryNotificationCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-116">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="244fc-117">コンピューターの現在のメモリ負荷を CLR に通知するために、ホストが呼び出すコールバック関数へのポインターを登録します。</span><span class="sxs-lookup"><span data-stu-id="244fc-117">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="244fc-118">ReleasedVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-118">ReleasedVirtualAddressSpace Method</span></span>](ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="244fc-119">指定されたメモリを使用して CLR が終了したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="244fc-119">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="244fc-120">VirtualAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-120">VirtualAlloc Method</span></span>](ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="244fc-121">対応する Win32 関数の論理ラッパーとして機能します。これは、呼び出し元プロセスの仮想アドレス空間にあるページの領域を予約またはコミットします。</span><span class="sxs-lookup"><span data-stu-id="244fc-121">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="244fc-122">VirtualFree メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-122">VirtualFree Method</span></span>](ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="244fc-123">呼び出しプロセスの仮想アドレス空間内のページの領域を解放、デ、または解放してデする、対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="244fc-123">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="244fc-124">VirtualProtect メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-124">VirtualProtect Method</span></span>](ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="244fc-125">対応する Win32 関数の論理ラッパーとして機能します。これにより、呼び出し元プロセスの仮想アドレス空間でコミットされたページの領域の保護が変更されます。</span><span class="sxs-lookup"><span data-stu-id="244fc-125">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="244fc-126">VirtualQuery メソッド</span><span class="sxs-lookup"><span data-stu-id="244fc-126">VirtualQuery Method</span></span>](ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="244fc-127">対応する Win32 関数の論理ラッパーとして機能し、呼び出し元プロセスの仮想アドレス空間にあるページの範囲に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="244fc-127">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="244fc-128">解説</span><span class="sxs-lookup"><span data-stu-id="244fc-128">Remarks</span></span>  

 <span data-ttu-id="244fc-129">`IHostMemoryManager` また、は、ヒープ上でメモリ要求を行うためのポインターを取得し、ホストによって報告されたプロセスのメモリ負荷のレベルを取得するために、CLR のメソッドも提供します。</span><span class="sxs-lookup"><span data-stu-id="244fc-129">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="244fc-130">要件</span><span class="sxs-lookup"><span data-stu-id="244fc-130">Requirements</span></span>  

 <span data-ttu-id="244fc-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="244fc-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="244fc-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="244fc-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="244fc-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="244fc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="244fc-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="244fc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244fc-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="244fc-135">See also</span></span>

- [<span data-ttu-id="244fc-136">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="244fc-136">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="244fc-137">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="244fc-137">Hosting Interfaces</span></span>](hosting-interfaces.md)

---
description: '詳細について: IHostMemoryManager:: NeedsVirtualAddressSpace メソッド'
title: IHostMemoryManager::NeedsVirtualAddressSpace メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
ms.openlocfilehash: 95d4128decffc82fdcb198155b48a31420f71220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707788"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="b0146-103">IHostMemoryManager::NeedsVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="b0146-103">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>

<span data-ttu-id="b0146-104">共通言語ランタイム (CLR) が、指定されたメモリを使用しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="b0146-104">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0146-105">構文</span><span class="sxs-lookup"><span data-stu-id="b0146-105">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0146-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0146-106">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="b0146-107">からメモリの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="b0146-107">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="b0146-108">からメモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="b0146-108">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0146-109">解説</span><span class="sxs-lookup"><span data-stu-id="b0146-109">Remarks</span></span>  

 <span data-ttu-id="b0146-110">`NeedsVirtualAddressSpace`メソッドはコールバックメソッドであり、ホストアプリケーションのライターによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0146-110">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="b0146-111">これは CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b0146-111">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="b0146-112">ホストが指定されたメモリを使用しないようにする場合は、E_OUTOFMEMORY HRESULT が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="b0146-112">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0146-113">要件</span><span class="sxs-lookup"><span data-stu-id="b0146-113">Requirements</span></span>  

 <span data-ttu-id="b0146-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0146-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0146-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b0146-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0146-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b0146-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0146-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0146-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0146-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0146-118">See also</span></span>

- [<span data-ttu-id="b0146-119">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0146-119">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)

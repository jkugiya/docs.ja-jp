---
description: '詳細について: IHostMemoryManager:: AcquiredVirtualAddressSpace メソッド'
title: IHostMemoryManager::AcquiredVirtualAddressSpace メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
ms.openlocfilehash: 70424c5bf907cfc3fb2e8951464335323f9331f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707906"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="b8d63-103">IHostMemoryManager::AcquiredVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="b8d63-103">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>

<span data-ttu-id="b8d63-104">共通言語ランタイム (CLR) が、指定されたメモリをオペレーティングシステムから取得したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="b8d63-104">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8d63-105">構文</span><span class="sxs-lookup"><span data-stu-id="b8d63-105">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8d63-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b8d63-106">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="b8d63-107">からメモリの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="b8d63-107">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="b8d63-108">からメモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="b8d63-108">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8d63-109">解説</span><span class="sxs-lookup"><span data-stu-id="b8d63-109">Remarks</span></span>  

 <span data-ttu-id="b8d63-110">`AcquiredVirtualAddressSpace`メソッドはコールバックメソッドであり、ホストアプリケーションのライターによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8d63-110">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="b8d63-111">これは CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b8d63-111">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8d63-112">要件</span><span class="sxs-lookup"><span data-stu-id="b8d63-112">Requirements</span></span>  

 <span data-ttu-id="b8d63-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8d63-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8d63-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b8d63-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8d63-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b8d63-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8d63-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8d63-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d63-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8d63-117">See also</span></span>

- [<span data-ttu-id="b8d63-118">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8d63-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)

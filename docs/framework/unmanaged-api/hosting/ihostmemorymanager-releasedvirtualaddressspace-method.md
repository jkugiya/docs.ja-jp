---
description: '詳細について: IHostMemoryManager:: ReleasedVirtualAddressSpace メソッド'
title: IHostMemoryManager::ReleasedVirtualAddressSpace メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
ms.openlocfilehash: e67e80018b5002bdf2a50530af9ab057696fff4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707775"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="63ff2-103">IHostMemoryManager::ReleasedVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="63ff2-103">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>

<span data-ttu-id="63ff2-104">指定されたメモリを使用して共通言語ランタイム (CLR) が終了したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="63ff2-104">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63ff2-105">構文</span><span class="sxs-lookup"><span data-stu-id="63ff2-105">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63ff2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="63ff2-106">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="63ff2-107">から解放されるメモリの開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="63ff2-107">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63ff2-108">解説</span><span class="sxs-lookup"><span data-stu-id="63ff2-108">Remarks</span></span>  

 <span data-ttu-id="63ff2-109">`ReleasedVirtualAddressSpace`メソッドはコールバックメソッドであり、ホストアプリケーションのライターによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="63ff2-109">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="63ff2-110">これは CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="63ff2-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63ff2-111">要件</span><span class="sxs-lookup"><span data-stu-id="63ff2-111">Requirements</span></span>  

 <span data-ttu-id="63ff2-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63ff2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63ff2-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="63ff2-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63ff2-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="63ff2-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63ff2-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63ff2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63ff2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="63ff2-116">See also</span></span>

- [<span data-ttu-id="63ff2-117">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63ff2-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)

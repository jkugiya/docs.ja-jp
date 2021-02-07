---
description: '詳細について: IGCHost:: SetVirtualMemLimit メソッド'
title: IGCHost::SetVirtualMemLimit メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
ms.openlocfilehash: 62cd9e2d84e51f0544e464bdbf49c50af8086546
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709439"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="9b3e5-103">IGCHost::SetVirtualMemLimit メソッド</span><span class="sxs-lookup"><span data-stu-id="9b3e5-103">IGCHost::SetVirtualMemLimit Method</span></span>

<span data-ttu-id="9b3e5-104">ランタイムの仮想メモリの最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="9b3e5-104">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b3e5-105">構文</span><span class="sxs-lookup"><span data-stu-id="9b3e5-105">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b3e5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b3e5-106">Parameters</span></span>  

 `sztMaxVirtualMemMB`  
 <span data-ttu-id="9b3e5-107">からランタイムの仮想メモリの最大サイズ (mb 単位)。</span><span class="sxs-lookup"><span data-stu-id="9b3e5-107">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b3e5-108">解説</span><span class="sxs-lookup"><span data-stu-id="9b3e5-108">Remarks</span></span>  

 <span data-ttu-id="9b3e5-109">ランタイムの仮想メモリの最大サイズは動的に変更できます。</span><span class="sxs-lookup"><span data-stu-id="9b3e5-109">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b3e5-110">要件</span><span class="sxs-lookup"><span data-stu-id="9b3e5-110">Requirements</span></span>  

 <span data-ttu-id="9b3e5-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b3e5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b3e5-112">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="9b3e5-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="9b3e5-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9b3e5-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b3e5-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b3e5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3e5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b3e5-115">See also</span></span>

- [<span data-ttu-id="9b3e5-116">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b3e5-116">IGCHost Interface</span></span>](igchost-interface.md)

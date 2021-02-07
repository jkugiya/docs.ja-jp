---
description: '詳細について: ICorThreadpool:: Corget Threads メソッド'
title: ICorThreadpool::CorGetAvailableThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
ms.openlocfilehash: ca6b476a00ce781e10c0708f5132b398b4c85398
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760577"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="22d7b-103">ICorThreadpool::CorGetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="22d7b-103">ICorThreadpool::CorGetAvailableThreads Method</span></span>

<span data-ttu-id="22d7b-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="22d7b-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d7b-105">構文</span><span class="sxs-lookup"><span data-stu-id="22d7b-105">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="22d7b-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="22d7b-106">Requirements</span></span>  

 <span data-ttu-id="22d7b-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22d7b-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22d7b-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="22d7b-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22d7b-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="22d7b-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22d7b-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22d7b-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d7b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="22d7b-111">See also</span></span>

- [<span data-ttu-id="22d7b-112">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22d7b-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

---
description: '詳細について: ICorThreadpool:: CorSetMaxThreads メソッド'
title: ICorThreadpool::CorSetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorSetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type:
- apiref
ms.openlocfilehash: 5eb55604b55da58ffb4b5b2806aa3e340274a6b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789542"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="8af4c-103">ICorThreadpool::CorSetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="8af4c-103">ICorThreadpool::CorSetMaxThreads Method</span></span>

<span data-ttu-id="8af4c-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="8af4c-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af4c-105">構文</span><span class="sxs-lookup"><span data-stu-id="8af4c-105">Syntax</span></span>  
  
```cpp  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="8af4c-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="8af4c-106">Requirements</span></span>  

 <span data-ttu-id="8af4c-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8af4c-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8af4c-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8af4c-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8af4c-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8af4c-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8af4c-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8af4c-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af4c-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="8af4c-111">See also</span></span>

- [<span data-ttu-id="8af4c-112">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8af4c-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

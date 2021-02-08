---
description: '詳細について: ICorThreadpool:: CorUnregisterWait メソッド'
title: ICorThreadpool::CorUnregisterWait メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
ms.openlocfilehash: 61b6c7a1fa8459ddd173d2857cff982f353afc31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789529"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="a2815-103">ICorThreadpool::CorUnregisterWait メソッド</span><span class="sxs-lookup"><span data-stu-id="a2815-103">ICorThreadpool::CorUnregisterWait Method</span></span>

<span data-ttu-id="a2815-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="a2815-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2815-105">構文</span><span class="sxs-lookup"><span data-stu-id="a2815-105">Syntax</span></span>  
  
```cpp  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a2815-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="a2815-106">Requirements</span></span>  

 <span data-ttu-id="a2815-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2815-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2815-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a2815-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2815-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a2815-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2815-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2815-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2815-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2815-111">See also</span></span>

- [<span data-ttu-id="a2815-112">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2815-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

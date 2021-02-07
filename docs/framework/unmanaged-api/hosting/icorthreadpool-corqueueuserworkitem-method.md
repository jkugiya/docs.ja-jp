---
description: '詳細について: ICorThreadpool:: CorQueueUserWorkItem メソッド'
title: ICorThreadpool::CorQueueUserWorkItem メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type:
- apiref
ms.openlocfilehash: fc0fc1dc3aa33bf11735fddd2c034af03f269f3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737757"
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="d5677-103">ICorThreadpool::CorQueueUserWorkItem メソッド</span><span class="sxs-lookup"><span data-stu-id="d5677-103">ICorThreadpool::CorQueueUserWorkItem Method</span></span>

<span data-ttu-id="d5677-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="d5677-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5677-105">構文</span><span class="sxs-lookup"><span data-stu-id="d5677-105">Syntax</span></span>  
  
```cpp  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d5677-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="d5677-106">Requirements</span></span>  

 <span data-ttu-id="d5677-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5677-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5677-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d5677-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5677-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d5677-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5677-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5677-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5677-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5677-111">See also</span></span>

- [<span data-ttu-id="d5677-112">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5677-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

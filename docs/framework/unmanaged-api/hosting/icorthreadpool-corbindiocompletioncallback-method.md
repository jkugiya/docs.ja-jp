---
description: '詳細について: ICorThreadpool:: CorBindIoCompletionCallback メソッド'
title: ICorThreadpool::CorBindIoCompletionCallback メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorBindIoCompletionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorBindIoCompletionCallback
helpviewer_keywords:
- CorBindIoCompletionCallback method [.NET Framework hosting]
- ICorThreadpool::CorBindIoCompletionCallback method [.NET Framework hosting]
ms.assetid: 2b159225-f09c-42f1-aa7c-44087e121249
topic_type:
- apiref
ms.openlocfilehash: 9f9e62fd8947c3ab80c4434814ee7e95b5327a24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799435"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="209de-103">ICorThreadpool::CorBindIoCompletionCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="209de-103">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>

<span data-ttu-id="209de-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="209de-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="209de-105">構文</span><span class="sxs-lookup"><span data-stu-id="209de-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="209de-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="209de-106">Requirements</span></span>  

 <span data-ttu-id="209de-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="209de-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="209de-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="209de-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="209de-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="209de-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="209de-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="209de-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="209de-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="209de-111">See also</span></span>

- [<span data-ttu-id="209de-112">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="209de-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

---
description: '詳細について: ICorThreadpool:: CorDeleteTimer メソッド'
title: ICorThreadpool::CorDeleteTimer メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
ms.openlocfilehash: 9096f9969702d522427640b2f881cae4aa23284d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737729"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="21e66-103">ICorThreadpool::CorDeleteTimer メソッド</span><span class="sxs-lookup"><span data-stu-id="21e66-103">ICorThreadpool::CorDeleteTimer Method</span></span>

<span data-ttu-id="21e66-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="21e66-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e66-105">構文</span><span class="sxs-lookup"><span data-stu-id="21e66-105">Syntax</span></span>  
  
```cpp  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="21e66-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="21e66-106">Requirements</span></span>  

 <span data-ttu-id="21e66-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21e66-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e66-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="21e66-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21e66-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="21e66-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21e66-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e66-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e66-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="21e66-111">See also</span></span>

- [<span data-ttu-id="21e66-112">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21e66-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

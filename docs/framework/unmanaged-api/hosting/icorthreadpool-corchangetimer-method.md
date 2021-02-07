---
description: '詳細について: ICorThreadpool:: CorChangeTimer メソッド'
title: ICorThreadpool::CorChangeTimer メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorChangeTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorChangeTimer
helpviewer_keywords:
- CorChangeTimer method [.NET Framework hosting]
- ICorThreadpool::CorChangeTimer method [.NET Framework hosting]
ms.assetid: 82b03a59-5a87-43ed-9b75-e04b256e1a46
topic_type:
- apiref
ms.openlocfilehash: 259974d7c04f0bf0b4cc6b93234b35ab2c96e2ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671998"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="239d2-103">ICorThreadpool::CorChangeTimer メソッド</span><span class="sxs-lookup"><span data-stu-id="239d2-103">ICorThreadpool::CorChangeTimer Method</span></span>

<span data-ttu-id="239d2-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="239d2-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="239d2-105">構文</span><span class="sxs-lookup"><span data-stu-id="239d2-105">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,
    [in]  ULONG  DueTime,
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="239d2-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="239d2-106">Requirements</span></span>  

 <span data-ttu-id="239d2-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="239d2-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="239d2-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="239d2-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="239d2-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="239d2-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="239d2-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="239d2-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239d2-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="239d2-111">See also</span></span>

- [<span data-ttu-id="239d2-112">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="239d2-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

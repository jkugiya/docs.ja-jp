---
description: '詳細情報: ICorPublishEnum:: Skip メソッド'
title: ICorPublishEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
ms.openlocfilehash: f0124681c8051a5c05c1caf3edd06c697da486e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794601"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="f3b0f-103">ICorPublishEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="f3b0f-103">ICorPublishEnum::Skip Method</span></span>

<span data-ttu-id="f3b0f-104">指定した数の項目だけ、列挙内でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="f3b0f-104">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3b0f-105">構文</span><span class="sxs-lookup"><span data-stu-id="f3b0f-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3b0f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3b0f-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="f3b0f-107">からカーソルを前方に移動する項目の数。</span><span class="sxs-lookup"><span data-stu-id="f3b0f-107">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3b0f-108">要件</span><span class="sxs-lookup"><span data-stu-id="f3b0f-108">Requirements</span></span>  

 <span data-ttu-id="f3b0f-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3b0f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3b0f-110">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="f3b0f-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f3b0f-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3b0f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3b0f-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3b0f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b0f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3b0f-113">See also</span></span>

- [<span data-ttu-id="f3b0f-114">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3b0f-114">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)

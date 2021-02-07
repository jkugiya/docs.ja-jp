---
description: '詳細情報: ICorDebugEnum:: Skip メソッド'
title: ICorDebugEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
ms.openlocfilehash: f72e400b3c2c911f609aca19f1b7d6a3a4e785cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694358"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="60b6e-103">ICorDebugEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="60b6e-103">ICorDebugEnum::Skip Method</span></span>

<span data-ttu-id="60b6e-104">指定した数の項目だけ、列挙内でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="60b6e-104">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60b6e-105">構文</span><span class="sxs-lookup"><span data-stu-id="60b6e-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60b6e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60b6e-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="60b6e-107">からカーソルを前方に移動する項目の数。</span><span class="sxs-lookup"><span data-stu-id="60b6e-107">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60b6e-108">要件</span><span class="sxs-lookup"><span data-stu-id="60b6e-108">Requirements</span></span>  

 <span data-ttu-id="60b6e-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60b6e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60b6e-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60b6e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60b6e-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60b6e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60b6e-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60b6e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60b6e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="60b6e-113">See also</span></span>

- [<span data-ttu-id="60b6e-114">ICorDebugEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60b6e-114">ICorDebugEnum Interface</span></span>](icordebugenum-interface1.md)

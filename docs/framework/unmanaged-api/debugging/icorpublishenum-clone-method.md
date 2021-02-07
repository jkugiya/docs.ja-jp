---
description: '詳細情報: ICorPublishEnum:: Clone メソッド'
title: ICorPublishEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
ms.openlocfilehash: 6001f27451afdb564da6275a31256ac348bc693a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721646"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="eb9dd-103">ICorPublishEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="eb9dd-103">ICorPublishEnum::Clone Method</span></span>

<span data-ttu-id="eb9dd-104">この [ICorPublishEnum](icorpublishenum-interface.md) オブジェクトのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb9dd-104">Creates a copy of this [ICorPublishEnum](icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb9dd-105">構文</span><span class="sxs-lookup"><span data-stu-id="eb9dd-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb9dd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb9dd-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="eb9dd-107">入出力 `ICorPublishEnum` このオブジェクトのコピーであるオブジェクトのアドレスへのポインター `ICorPublishEnum` 。</span><span class="sxs-lookup"><span data-stu-id="eb9dd-107">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb9dd-108">要件</span><span class="sxs-lookup"><span data-stu-id="eb9dd-108">Requirements</span></span>  

 <span data-ttu-id="eb9dd-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb9dd-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb9dd-110">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="eb9dd-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="eb9dd-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb9dd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb9dd-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb9dd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb9dd-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb9dd-113">See also</span></span>

- [<span data-ttu-id="eb9dd-114">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb9dd-114">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)

---
description: '詳細について: ICorPublishEnum:: GetCount メソッド'
title: ICorPublishEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
ms.openlocfilehash: 99e831ae366604e2ae7494bf80fb2e7f25532582
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721620"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="cc4de-103">ICorPublishEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="cc4de-103">ICorPublishEnum::GetCount Method</span></span>

<span data-ttu-id="cc4de-104">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc4de-104">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc4de-105">構文</span><span class="sxs-lookup"><span data-stu-id="cc4de-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc4de-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc4de-106">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="cc4de-107">入出力列挙体に含まれる項目の数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cc4de-107">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc4de-108">要件</span><span class="sxs-lookup"><span data-stu-id="cc4de-108">Requirements</span></span>  

 <span data-ttu-id="cc4de-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc4de-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc4de-110">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="cc4de-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cc4de-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc4de-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc4de-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc4de-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc4de-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc4de-113">See also</span></span>

- [<span data-ttu-id="cc4de-114">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc4de-114">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)

---
description: '詳細について: ICorPublishAppDomain:: GetID メソッド'
title: ICorPublishAppDomain::GetID メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
ms.openlocfilehash: b3de19c053b5fcce2af5e0036ee6174b01700aac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721841"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="fc93e-103">ICorPublishAppDomain::GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="fc93e-103">ICorPublishAppDomain::GetID Method</span></span>

<span data-ttu-id="fc93e-104">この [ICorPublishAppDomain](icorpublishappdomain-interface.md)の一意の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="fc93e-104">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc93e-105">構文</span><span class="sxs-lookup"><span data-stu-id="fc93e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc93e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc93e-106">Parameters</span></span>  

 `puId`  
 <span data-ttu-id="fc93e-107">入出力アプリケーションドメインの識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="fc93e-107">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc93e-108">解説</span><span class="sxs-lookup"><span data-stu-id="fc93e-108">Remarks</span></span>  

 <span data-ttu-id="fc93e-109">識別子は、含んでいるプロセスのスコープ内でのみ一意です。</span><span class="sxs-lookup"><span data-stu-id="fc93e-109">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc93e-110">要件</span><span class="sxs-lookup"><span data-stu-id="fc93e-110">Requirements</span></span>  

 <span data-ttu-id="fc93e-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc93e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc93e-112">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="fc93e-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="fc93e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc93e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc93e-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc93e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc93e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc93e-115">See also</span></span>

- [<span data-ttu-id="fc93e-116">ICorPublishAppDomain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc93e-116">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)

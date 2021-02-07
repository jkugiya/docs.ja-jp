---
description: '詳細については、次を参照してください: IsActive メソッド'
title: ICorDebugEval::IsActive メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
ms.openlocfilehash: 2314814f8979f460063017ebdf46beb512417395
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694059"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="5bc3a-103">ICorDebugEval::IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="5bc3a-103">ICorDebugEval::IsActive Method</span></span>

<span data-ttu-id="5bc3a-104">この、このオブジェクトが現在実行されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="5bc3a-104">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc3a-105">構文</span><span class="sxs-lookup"><span data-stu-id="5bc3a-105">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc3a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5bc3a-106">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="5bc3a-107">入出力この評価がアクティブかどうかを示す値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5bc3a-107">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc3a-108">要件</span><span class="sxs-lookup"><span data-stu-id="5bc3a-108">Requirements</span></span>  

 <span data-ttu-id="5bc3a-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bc3a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc3a-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bc3a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bc3a-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bc3a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bc3a-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc3a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

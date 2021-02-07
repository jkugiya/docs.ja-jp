---
description: '詳細情報: ICorDebugArrayValue:: Ge k メソッド'
title: ICorDebugArrayValue::GetRank メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type:
- apiref
ms.openlocfilehash: b84cc8fd49cbb7f7d4aa6fa7fa41b1c6cf8daf29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722998"
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="94da9-103">ICorDebugArrayValue::GetRank メソッド</span><span class="sxs-lookup"><span data-stu-id="94da9-103">ICorDebugArrayValue::GetRank Method</span></span>

<span data-ttu-id="94da9-104">配列のディメンションの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="94da9-104">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94da9-105">構文</span><span class="sxs-lookup"><span data-stu-id="94da9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94da9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94da9-106">Parameters</span></span>  

 `pnRank`  
 <span data-ttu-id="94da9-107">入出力このオブジェクトの次元数へのポインター `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="94da9-107">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94da9-108">要件</span><span class="sxs-lookup"><span data-stu-id="94da9-108">Requirements</span></span>  

 <span data-ttu-id="94da9-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94da9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94da9-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94da9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94da9-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94da9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94da9-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94da9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

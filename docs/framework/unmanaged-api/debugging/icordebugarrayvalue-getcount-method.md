---
description: '詳細について: ICorDebugArrayValue:: GetCount メソッド'
title: ICorDebugArrayValue::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
ms.openlocfilehash: 7b1422714ed9c6f89c65c310165b8cdaa6566360
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723125"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="d2b94-103">ICorDebugArrayValue::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="d2b94-103">ICorDebugArrayValue::GetCount Method</span></span>

<span data-ttu-id="d2b94-104">配列内の要素の合計数を取得します。</span><span class="sxs-lookup"><span data-stu-id="d2b94-104">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2b94-105">構文</span><span class="sxs-lookup"><span data-stu-id="d2b94-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2b94-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2b94-106">Parameters</span></span>  

 `pnCount`  
 <span data-ttu-id="d2b94-107">入出力配列内の要素の合計数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d2b94-107">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2b94-108">要件</span><span class="sxs-lookup"><span data-stu-id="d2b94-108">Requirements</span></span>  

 <span data-ttu-id="d2b94-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2b94-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2b94-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2b94-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2b94-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2b94-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2b94-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2b94-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

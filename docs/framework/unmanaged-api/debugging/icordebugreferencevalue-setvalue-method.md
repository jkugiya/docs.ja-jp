---
description: '詳細については、次を参照してください: を参照してください。値:: SetValue メソッド'
title: ICorDebugReferenceValue::SetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
ms.openlocfilehash: 44909962d2716ddb606d98a2f6b3804247c581cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690913"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="fecaa-103">ICorDebugReferenceValue::SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="fecaa-103">ICorDebugReferenceValue::SetValue Method</span></span>

<span data-ttu-id="fecaa-104">指定されたメモリアドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="fecaa-104">Sets the specified memory address.</span></span> <span data-ttu-id="fecaa-105">つまり、このメソッドは、オブジェクトを指すようにこの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="fecaa-105">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fecaa-106">構文</span><span class="sxs-lookup"><span data-stu-id="fecaa-106">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fecaa-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fecaa-107">Parameters</span></span>  

 `value`  
 <span data-ttu-id="fecaa-108">から `CORDB_ADDRESS` このが指すオブジェクトのアドレスを示す値です `ICorDebugReferenceValue` 。</span><span class="sxs-lookup"><span data-stu-id="fecaa-108">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fecaa-109">要件</span><span class="sxs-lookup"><span data-stu-id="fecaa-109">Requirements</span></span>  

 <span data-ttu-id="fecaa-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fecaa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fecaa-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fecaa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fecaa-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fecaa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fecaa-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fecaa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

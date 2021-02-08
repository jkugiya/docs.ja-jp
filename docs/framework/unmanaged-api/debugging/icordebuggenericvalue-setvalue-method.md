---
description: 詳細については、次を参照
title: ICorDebugGenericValue::SetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
ms.openlocfilehash: e284d9987c8428fadedde0024fd3c65a0d8fe7a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791479"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="1d48b-103">ICorDebugGenericValue::SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="1d48b-103">ICorDebugGenericValue::SetValue Method</span></span>

<span data-ttu-id="1d48b-104">指定したバッファーから新しい値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="1d48b-104">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d48b-105">構文</span><span class="sxs-lookup"><span data-stu-id="1d48b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d48b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1d48b-106">Parameters</span></span>  

 `pFrom`  
 <span data-ttu-id="1d48b-107">から値のコピー元のバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1d48b-107">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d48b-108">解説</span><span class="sxs-lookup"><span data-stu-id="1d48b-108">Remarks</span></span>  

 <span data-ttu-id="1d48b-109">参照型の場合、値は参照であり、コンテンツではありません。</span><span class="sxs-lookup"><span data-stu-id="1d48b-109">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d48b-110">要件</span><span class="sxs-lookup"><span data-stu-id="1d48b-110">Requirements</span></span>  

 <span data-ttu-id="1d48b-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d48b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d48b-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d48b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d48b-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d48b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d48b-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d48b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
description: '詳細について: ICorDebugArrayValue:: GetElementType メソッド'
title: ICorDebugArrayValue::GetElementType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementType
helpviewer_keywords:
- ICorDebugArrayValue::GetElementType method [.NET Framework debugging]
- GetElementType method [.NET Framework debugging]
ms.assetid: ed71961e-ae9b-4dfc-9554-06637696d697
topic_type:
- apiref
ms.openlocfilehash: 97c01a9c8ae7a1d73a1a15b97d3ce3e9aa079365
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723030"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="9656a-103">ICorDebugArrayValue::GetElementType メソッド</span><span class="sxs-lookup"><span data-stu-id="9656a-103">ICorDebugArrayValue::GetElementType Method</span></span>

<span data-ttu-id="9656a-104">配列内の要素の単純型を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9656a-104">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9656a-105">構文</span><span class="sxs-lookup"><span data-stu-id="9656a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9656a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9656a-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="9656a-107">入出力型を示す CorElementType 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9656a-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9656a-108">要件</span><span class="sxs-lookup"><span data-stu-id="9656a-108">Requirements</span></span>  

 <span data-ttu-id="9656a-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9656a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9656a-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9656a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9656a-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9656a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9656a-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9656a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

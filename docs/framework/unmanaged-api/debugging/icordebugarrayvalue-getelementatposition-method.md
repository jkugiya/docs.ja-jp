---
description: '詳細について: ICorDebugArrayValue:: GetElementAtPosition メソッド'
title: ICorDebugArrayValue::GetElementAtPosition メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
ms.openlocfilehash: ef8e4a39f5fe4088b1883803aee037c51f410241
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723033"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="110e9-103">ICorDebugArrayValue::GetElementAtPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="110e9-103">ICorDebugArrayValue::GetElementAtPosition Method</span></span>

<span data-ttu-id="110e9-104">配列を0から始まる1次元配列として扱い、指定された位置にある要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="110e9-104">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="110e9-105">構文</span><span class="sxs-lookup"><span data-stu-id="110e9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="110e9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="110e9-106">Parameters</span></span>  

 `nPosition`  
 <span data-ttu-id="110e9-107">から取得する要素の位置。</span><span class="sxs-lookup"><span data-stu-id="110e9-107">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="110e9-108">入出力要素の値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="110e9-108">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="110e9-109">解説</span><span class="sxs-lookup"><span data-stu-id="110e9-109">Remarks</span></span>  

 <span data-ttu-id="110e9-110">多次元配列のレイアウトは、C++ スタイルの配列レイアウトに従います。</span><span class="sxs-lookup"><span data-stu-id="110e9-110">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="110e9-111">要件</span><span class="sxs-lookup"><span data-stu-id="110e9-111">Requirements</span></span>  

 <span data-ttu-id="110e9-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="110e9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="110e9-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="110e9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="110e9-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="110e9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="110e9-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="110e9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

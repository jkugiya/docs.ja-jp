---
description: '詳細について: ICorDebugArrayValue:: GetBaseIndicies メソッド'
title: ICorDebugArrayValue::GetBaseIndicies メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
ms.openlocfilehash: ac38123860cc3187b7dc2398b32244387d19c5ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723121"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="5f1a8-103">ICorDebugArrayValue::GetBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="5f1a8-103">ICorDebugArrayValue::GetBaseIndicies Method</span></span>

<span data-ttu-id="5f1a8-104">配列内の各次元のベースインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5f1a8-104">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f1a8-105">構文</span><span class="sxs-lookup"><span data-stu-id="5f1a8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f1a8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5f1a8-106">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="5f1a8-107">からこのオブジェクトの次元数 `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="5f1a8-107">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="5f1a8-108">この値は、 `indicies` 配列のサイズがオブジェクトの次元数と同じであるため、配列のサイズでも `ICorDebugArrayValue` あります。</span><span class="sxs-lookup"><span data-stu-id="5f1a8-108">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="5f1a8-109">入出力整数の配列。各整数は、このオブジェクトの次元のベースインデックス (つまり開始インデックス) です `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="5f1a8-109">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f1a8-110">要件</span><span class="sxs-lookup"><span data-stu-id="5f1a8-110">Requirements</span></span>  

 <span data-ttu-id="5f1a8-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f1a8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f1a8-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f1a8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f1a8-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f1a8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f1a8-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f1a8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

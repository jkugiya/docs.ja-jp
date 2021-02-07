---
description: '詳細について: ICorDebugArrayValue:: GetDimensions メソッド'
title: ICorDebugArrayValue::GetDimensions メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: 007a48891a01e5779e3f9ef10cec720d6647c8f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723102"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="76df2-103">ICorDebugArrayValue::GetDimensions メソッド</span><span class="sxs-lookup"><span data-stu-id="76df2-103">ICorDebugArrayValue::GetDimensions Method</span></span>

<span data-ttu-id="76df2-104">この配列の各次元に含まれる要素の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="76df2-104">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76df2-105">構文</span><span class="sxs-lookup"><span data-stu-id="76df2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76df2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="76df2-106">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="76df2-107">からこの ICorDebugArrayValue オブジェクトの次元数。</span><span class="sxs-lookup"><span data-stu-id="76df2-107">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="76df2-108">この値は、 `dims` 配列のサイズがオブジェクトの次元数と同じであるため、配列のサイズでも `ICorDebugArrayValue` あります。</span><span class="sxs-lookup"><span data-stu-id="76df2-108">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="76df2-109">入出力整数の配列。各整数は、このオブジェクト内のディメンション内の要素の数を指定し `ICorDebugArrayValue` ます。</span><span class="sxs-lookup"><span data-stu-id="76df2-109">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76df2-110">要件</span><span class="sxs-lookup"><span data-stu-id="76df2-110">Requirements</span></span>  

 <span data-ttu-id="76df2-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76df2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76df2-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76df2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76df2-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76df2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76df2-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76df2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

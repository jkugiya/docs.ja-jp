---
description: 詳細については、「ICorDebugArrayValue インターフェイス」を参照してください。
title: ICorDebugArrayValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: 2b91c910b9444b061b4a6bea715667bca6a4629c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722894"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="89f47-103">ICorDebugArrayValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89f47-103">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="89f47-104">1次元配列または多次元配列を表す、値のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="89f47-104">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89f47-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="89f47-105">Methods</span></span>  
  
|<span data-ttu-id="89f47-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="89f47-106">Method</span></span>|<span data-ttu-id="89f47-107">説明</span><span class="sxs-lookup"><span data-stu-id="89f47-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89f47-108">GetBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="89f47-108">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="89f47-109">配列内の各次元のベースインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="89f47-109">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="89f47-110">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="89f47-110">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="89f47-111">配列内の要素の合計数を取得します。</span><span class="sxs-lookup"><span data-stu-id="89f47-111">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="89f47-112">GetDimensions メソッド</span><span class="sxs-lookup"><span data-stu-id="89f47-112">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="89f47-113">配列の次元を取得します。</span><span class="sxs-lookup"><span data-stu-id="89f47-113">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="89f47-114">GetElement メソッド</span><span class="sxs-lookup"><span data-stu-id="89f47-114">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="89f47-115">配列内の指定された要素を表す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="89f47-115">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="89f47-116">GetElementAtPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="89f47-116">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="89f47-117">配列を0から始まる1次元配列として扱い、指定された位置にある要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="89f47-117">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="89f47-118">GetElementType メソッド</span><span class="sxs-lookup"><span data-stu-id="89f47-118">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="89f47-119">配列内の要素の単純型を取得します。</span><span class="sxs-lookup"><span data-stu-id="89f47-119">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="89f47-120">GetRank メソッド</span><span class="sxs-lookup"><span data-stu-id="89f47-120">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="89f47-121">配列のディメンションの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="89f47-121">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="89f47-122">HasBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="89f47-122">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="89f47-123">配列にベースインデックスがあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="89f47-123">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89f47-124">解説</span><span class="sxs-lookup"><span data-stu-id="89f47-124">Remarks</span></span>  

 <span data-ttu-id="89f47-125">`ICorDebugArrayValue` では、1次元配列と多次元配列の両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="89f47-125">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89f47-126">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="89f47-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89f47-127">要件</span><span class="sxs-lookup"><span data-stu-id="89f47-127">Requirements</span></span>  

 <span data-ttu-id="89f47-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89f47-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89f47-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89f47-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89f47-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89f47-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89f47-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89f47-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f47-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="89f47-132">See also</span></span>

- [<span data-ttu-id="89f47-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="89f47-133">Debugging Interfaces</span></span>](debugging-interfaces.md)

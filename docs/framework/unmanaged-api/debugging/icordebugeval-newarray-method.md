---
description: '詳細については、次のページを参照してください: いいです。:、NewArray メソッド'
title: ICorDebugEval::NewArray メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
ms.openlocfilehash: 1344a99450974369533b1c54b641c036fc64e3ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693981"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="5c907-103">ICorDebugEval::NewArray メソッド</span><span class="sxs-lookup"><span data-stu-id="5c907-103">ICorDebugEval::NewArray Method</span></span>

<span data-ttu-id="5c907-104">指定した要素の型と次元の新しい配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5c907-104">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="5c907-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="5c907-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5c907-106">代わりに [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="5c907-106">Use [ICorDebugEval2::NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c907-107">構文</span><span class="sxs-lookup"><span data-stu-id="5c907-107">Syntax</span></span>  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c907-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c907-108">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="5c907-109">から配列の要素の型を指定する CorElementType 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="5c907-109">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="5c907-110">から要素のクラスを指定する、ツールオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5c907-110">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="5c907-111">要素の型がプリミティブ型の場合、この値は null になることがあります。</span><span class="sxs-lookup"><span data-stu-id="5c907-111">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="5c907-112">から配列の次元数。</span><span class="sxs-lookup"><span data-stu-id="5c907-112">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="5c907-113">.NET Framework 2.0 では、この値は1である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c907-113">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="5c907-114">から配列の各次元のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5c907-114">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="5c907-115">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="5c907-115">[in] Optional.</span></span> <span data-ttu-id="5c907-116">配列の各次元の下限。</span><span class="sxs-lookup"><span data-stu-id="5c907-116">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="5c907-117">この値を省略すると、次元ごとに下限0が想定されます。</span><span class="sxs-lookup"><span data-stu-id="5c907-117">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c907-118">解説</span><span class="sxs-lookup"><span data-stu-id="5c907-118">Remarks</span></span>  

 <span data-ttu-id="5c907-119">配列は常に、スレッドが現在実行されているアプリケーションドメインで作成されます。</span><span class="sxs-lookup"><span data-stu-id="5c907-119">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c907-120">要件</span><span class="sxs-lookup"><span data-stu-id="5c907-120">Requirements</span></span>  

 <span data-ttu-id="5c907-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c907-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c907-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c907-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c907-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c907-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c907-124">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="5c907-124">**.NET Framework Versions:** 1.1, 1.0</span></span>

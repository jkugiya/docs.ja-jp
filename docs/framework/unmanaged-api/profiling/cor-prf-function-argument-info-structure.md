---
description: '詳細情報: COR_PRF_FUNCTION_ARGUMENT_INFO 構造'
title: COR_PRF_FUNCTION_ARGUMENT_INFO 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
ms.openlocfilehash: c40c9b20dad79fa36a1ed4471106a54f2c55b422
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649066"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="dd1ba-103">COR_PRF_FUNCTION_ARGUMENT_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="dd1ba-103">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>

<span data-ttu-id="dd1ba-104">関数の引数を左から右方向で表します。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-104">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd1ba-105">構文</span><span class="sxs-lookup"><span data-stu-id="dd1ba-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="dd1ba-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="dd1ba-106">Members</span></span>  
  
|<span data-ttu-id="dd1ba-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="dd1ba-107">Member</span></span>|<span data-ttu-id="dd1ba-108">説明</span><span class="sxs-lookup"><span data-stu-id="dd1ba-108">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="dd1ba-109">引数のブロックの数。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-109">The number of blocks of arguments.</span></span> <span data-ttu-id="dd1ba-110">つまり、この値は配列内の [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) 構造体の数です `ranges` 。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-110">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="dd1ba-111">すべての引数の合計サイズ。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-111">The total size of all arguments.</span></span> <span data-ttu-id="dd1ba-112">言い換えると、この値は引数の長さの合計になります。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-112">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="dd1ba-113">`COR_PRF_FUNCTION_ARGUMENT_RANGE`構造体の配列。それぞれが関数の引数の1つのブロックを表します。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-113">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd1ba-114">解説</span><span class="sxs-lookup"><span data-stu-id="dd1ba-114">Remarks</span></span>  

 <span data-ttu-id="dd1ba-115">関数には、多くの引数を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-115">A function may have many arguments.</span></span> <span data-ttu-id="dd1ba-116">これらの引数は、連続してメモリに格納されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-116">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="dd1ba-117">1つの場所に3つの引数のブロック、別の場所に2つの引数のブロック、および別の場所にある1つの引数の最後のブロックがある場合があります。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-117">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="dd1ba-118">これらの引数はすべて同じ関数に対して使用されます。これらは、さまざまな場所に格納されています。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-118">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="dd1ba-119">`COR_PRF_FUNCTION_ARGUMENT_INFO`構造体は、1つの関数のすべての引数を表します。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-119">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="dd1ba-120">配列を使用して、関数の引数のすべてのブロックを参照します。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-120">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="dd1ba-121">そのため、1つの関数に対して1つの構造体を使用して、 `COR_PRF_FUNCTION_ARGUMENT_INFO` `COR_PRF_FUNCTION_ARGUMENT_RANGE` それぞれが1つ以上の関数引数を指し示す複数の構造体を参照します。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-121">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="dd1ba-122">レジスタに格納されている引数は、構造体を構築するためにメモリに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-122">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd1ba-123">要件</span><span class="sxs-lookup"><span data-stu-id="dd1ba-123">Requirements</span></span>  

 <span data-ttu-id="dd1ba-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd1ba-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd1ba-125">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="dd1ba-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="dd1ba-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd1ba-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd1ba-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd1ba-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd1ba-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd1ba-128">See also</span></span>

- [<span data-ttu-id="dd1ba-129">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="dd1ba-129">Profiling Structures</span></span>](profiling-structures.md)

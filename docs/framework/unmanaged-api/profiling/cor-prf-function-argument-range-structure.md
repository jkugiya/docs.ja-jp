---
description: '詳細情報: COR_PRF_FUNCTION_ARGUMENT_RANGE 構造'
title: COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
ms.openlocfilehash: 65d762ba4513341b20426ea56d423a2066f6e714
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649014"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="897f1-103">COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="897f1-103">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>

<span data-ttu-id="897f1-104">メモリに左から右方向へ連続で格納される関数の引数のブロックを表します。</span><span class="sxs-lookup"><span data-stu-id="897f1-104">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="897f1-105">構文</span><span class="sxs-lookup"><span data-stu-id="897f1-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="897f1-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="897f1-106">Members</span></span>  
  
|<span data-ttu-id="897f1-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="897f1-107">Members</span></span>|<span data-ttu-id="897f1-108">説明</span><span class="sxs-lookup"><span data-stu-id="897f1-108">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="897f1-109">ブロックの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="897f1-109">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="897f1-110">連続するブロックの長さ。</span><span class="sxs-lookup"><span data-stu-id="897f1-110">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="897f1-111">要件</span><span class="sxs-lookup"><span data-stu-id="897f1-111">Requirements</span></span>  

 <span data-ttu-id="897f1-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="897f1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="897f1-113">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="897f1-113">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="897f1-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="897f1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="897f1-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="897f1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="897f1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="897f1-116">See also</span></span>

- [<span data-ttu-id="897f1-117">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="897f1-117">Profiling Structures</span></span>](profiling-structures.md)

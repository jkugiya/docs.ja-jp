---
description: '詳細情報: COR_PRF_FUNCTION 構造'
title: COR_PRF_FUNCTION 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
ms.openlocfilehash: 494f3cfe6d1e3641645ef0050c06014e67bf4475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648975"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="10116-103">COR_PRF_FUNCTION 構造体</span><span class="sxs-lookup"><span data-stu-id="10116-103">COR_PRF_FUNCTION Structure</span></span>

<span data-ttu-id="10116-104">関数の一意の表記を、その関数の ID を再コンパイルされたバージョンの ID と組み合わせることによって、提供します。</span><span class="sxs-lookup"><span data-stu-id="10116-104">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10116-105">構文</span><span class="sxs-lookup"><span data-stu-id="10116-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="10116-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="10116-106">Members</span></span>  
  
|<span data-ttu-id="10116-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="10116-107">Member</span></span>|<span data-ttu-id="10116-108">説明</span><span class="sxs-lookup"><span data-stu-id="10116-108">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="10116-109">関数の ID。</span><span class="sxs-lookup"><span data-stu-id="10116-109">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="10116-110">再コンパイルされた関数の ID。</span><span class="sxs-lookup"><span data-stu-id="10116-110">The ID of the recompiled function.</span></span> <span data-ttu-id="10116-111">0 (ゼロ) の値は、関数の元のバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="10116-111">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10116-112">解説</span><span class="sxs-lookup"><span data-stu-id="10116-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10116-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="10116-113">Requirements</span></span>  

 <span data-ttu-id="10116-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10116-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10116-115">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="10116-115">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="10116-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10116-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10116-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10116-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10116-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="10116-118">See also</span></span>

- [<span data-ttu-id="10116-119">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="10116-119">Profiling Structures</span></span>](profiling-structures.md)

---
description: '詳細情報: COR_PRF_CLAUSE_TYPE 列挙型'
title: COR_PRF_CLAUSE_TYPE 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
ms.openlocfilehash: 413dbc0ad94e4ab670cd7cd9537bbd1735ffd7cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649287"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="cdd2e-103">COR_PRF_CLAUSE_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="cdd2e-103">COR_PRF_CLAUSE_TYPE Enumeration</span></span>

<span data-ttu-id="cdd2e-104">コードが入った、または出た例外句のタイプを示します。</span><span class="sxs-lookup"><span data-stu-id="cdd2e-104">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdd2e-105">構文</span><span class="sxs-lookup"><span data-stu-id="cdd2e-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="cdd2e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cdd2e-106">Members</span></span>  
  
|<span data-ttu-id="cdd2e-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="cdd2e-107">Member</span></span>|<span data-ttu-id="cdd2e-108">説明</span><span class="sxs-lookup"><span data-stu-id="cdd2e-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="cdd2e-109">Exception 句が有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="cdd2e-109">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="cdd2e-110">Exception 句はフィルター式です。</span><span class="sxs-lookup"><span data-stu-id="cdd2e-110">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="cdd2e-111">Exception 句は `catch` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="cdd2e-111">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="cdd2e-112">Exception 句は `finally` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="cdd2e-112">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cdd2e-113">要件</span><span class="sxs-lookup"><span data-stu-id="cdd2e-113">Requirements</span></span>  

 <span data-ttu-id="cdd2e-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdd2e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdd2e-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cdd2e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cdd2e-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdd2e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdd2e-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdd2e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd2e-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdd2e-118">See also</span></span>

- [<span data-ttu-id="cdd2e-119">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="cdd2e-119">Profiling Enumerations</span></span>](profiling-enumerations.md)

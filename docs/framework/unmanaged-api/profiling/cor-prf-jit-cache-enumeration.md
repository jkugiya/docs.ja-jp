---
description: '詳細情報: COR_PRF_JIT_CACHE 列挙型'
title: COR_PRF_JIT_CACHE 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_JIT_CACHE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_JIT_CACHE
helpviewer_keywords:
- COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type:
- apiref
ms.openlocfilehash: 94b04b42504760be826f78cee0da3066f1936f32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648754"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="7a0fc-103">COR_PRF_JIT_CACHE 列挙型</span><span class="sxs-lookup"><span data-stu-id="7a0fc-103">COR_PRF_JIT_CACHE Enumeration</span></span>

<span data-ttu-id="7a0fc-104">キャッシュされている関数検索の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="7a0fc-104">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a0fc-105">`COR_PRF_CACHED_FUNCTION_FOUND` の値は0であるため、 `COR_PRF_JIT_CACHE` ブールサロゲートとして使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="7a0fc-105">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a0fc-106">構文</span><span class="sxs-lookup"><span data-stu-id="7a0fc-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="7a0fc-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a0fc-107">Members</span></span>  
  
|<span data-ttu-id="7a0fc-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a0fc-108">Member</span></span>|<span data-ttu-id="7a0fc-109">説明</span><span class="sxs-lookup"><span data-stu-id="7a0fc-109">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="7a0fc-110">検索によって関数が検出されました。</span><span class="sxs-lookup"><span data-stu-id="7a0fc-110">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="7a0fc-111">検索で関数が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="7a0fc-111">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a0fc-112">要件</span><span class="sxs-lookup"><span data-stu-id="7a0fc-112">Requirements</span></span>  

 <span data-ttu-id="7a0fc-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a0fc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a0fc-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a0fc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a0fc-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a0fc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a0fc-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a0fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0fc-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a0fc-117">See also</span></span>

- [<span data-ttu-id="7a0fc-118">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="7a0fc-118">Profiling Enumerations</span></span>](profiling-enumerations.md)

---
description: '詳細情報: COR_PRF_GC_REASON 列挙型'
title: COR_PRF_GC_REASON 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
ms.openlocfilehash: f5c8201f2023e07f9bb9d540f6d5f8fca1c19419
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648796"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="e8f35-103">COR_PRF_GC_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="e8f35-103">COR_PRF_GC_REASON Enumeration</span></span>

<span data-ttu-id="e8f35-104">ガベージ コレクションが発生している理由を示します。</span><span class="sxs-lookup"><span data-stu-id="e8f35-104">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f35-105">構文</span><span class="sxs-lookup"><span data-stu-id="e8f35-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="e8f35-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e8f35-106">Members</span></span>  
  
|<span data-ttu-id="e8f35-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="e8f35-107">Member</span></span>|<span data-ttu-id="e8f35-108">説明</span><span class="sxs-lookup"><span data-stu-id="e8f35-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="e8f35-109">ガベージコレクションは、メソッドによって発生しました <xref:System.GC.Collect%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e8f35-109">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="e8f35-110">理由が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="e8f35-110">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8f35-111">要件</span><span class="sxs-lookup"><span data-stu-id="e8f35-111">Requirements</span></span>  

 <span data-ttu-id="e8f35-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f35-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8f35-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8f35-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8f35-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8f35-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8f35-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8f35-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f35-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8f35-116">See also</span></span>

- [<span data-ttu-id="e8f35-117">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="e8f35-117">Profiling Enumerations</span></span>](profiling-enumerations.md)

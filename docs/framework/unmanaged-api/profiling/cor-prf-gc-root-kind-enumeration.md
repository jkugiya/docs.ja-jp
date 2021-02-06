---
description: '詳細情報: COR_PRF_GC_ROOT_KIND 列挙型'
title: COR_PRF_GC_ROOT_KIND 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: 148d48458c906974d76b9e0ec0cb6b4d15ee49ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648780"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="b3a75-103">COR_PRF_GC_ROOT_KIND 列挙型</span><span class="sxs-lookup"><span data-stu-id="b3a75-103">COR_PRF_GC_ROOT_KIND Enumeration</span></span>

<span data-ttu-id="b3a75-104">[ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md)コールバックによって公開されるガベージコレクションルートの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="b3a75-104">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a75-105">構文</span><span class="sxs-lookup"><span data-stu-id="b3a75-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="b3a75-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b3a75-106">Members</span></span>  
  
|<span data-ttu-id="b3a75-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b3a75-107">Member</span></span>|<span data-ttu-id="b3a75-108">説明</span><span class="sxs-lookup"><span data-stu-id="b3a75-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="b3a75-109">ルートはスタック上の変数です。</span><span class="sxs-lookup"><span data-stu-id="b3a75-109">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="b3a75-110">ルートは、ファイナライザーキュー内のエントリです。</span><span class="sxs-lookup"><span data-stu-id="b3a75-110">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="b3a75-111">ルートはガベージコレクションハンドルです。</span><span class="sxs-lookup"><span data-stu-id="b3a75-111">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="b3a75-112">ルートの種類が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="b3a75-112">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3a75-113">要件</span><span class="sxs-lookup"><span data-stu-id="b3a75-113">Requirements</span></span>  

 <span data-ttu-id="b3a75-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3a75-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3a75-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3a75-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3a75-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3a75-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3a75-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3a75-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a75-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3a75-118">See also</span></span>

- [<span data-ttu-id="b3a75-119">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="b3a75-119">Profiling Enumerations</span></span>](profiling-enumerations.md)

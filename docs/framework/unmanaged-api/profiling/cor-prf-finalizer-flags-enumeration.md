---
description: '詳細情報: COR_PRF_FINALIZER_FLAGS 列挙型'
title: COR_PRF_FINALIZER_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
ms.openlocfilehash: 96430b1ba3a38cce2801ed55f030395154c78dab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649183"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="aa91d-103">COR_PRF_FINALIZER_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="aa91d-103">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>

<span data-ttu-id="aa91d-104">オブジェクトのファイナライザーを記述します。</span><span class="sxs-lookup"><span data-stu-id="aa91d-104">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa91d-105">構文</span><span class="sxs-lookup"><span data-stu-id="aa91d-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="aa91d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="aa91d-106">Members</span></span>  
  
|<span data-ttu-id="aa91d-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="aa91d-107">Member</span></span>|<span data-ttu-id="aa91d-108">説明</span><span class="sxs-lookup"><span data-stu-id="aa91d-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="aa91d-109">ファイナライザーは重要です。</span><span class="sxs-lookup"><span data-stu-id="aa91d-109">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa91d-110">解説</span><span class="sxs-lookup"><span data-stu-id="aa91d-110">Remarks</span></span>  

 <span data-ttu-id="aa91d-111">`COR_PRF_FINALIZER_FLAGS`列挙体は、 [ICorProfilerCallback2:: FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md)メソッドによって、オブジェクトのファイナライザーを記述するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="aa91d-111">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa91d-112">要件</span><span class="sxs-lookup"><span data-stu-id="aa91d-112">Requirements</span></span>  

 <span data-ttu-id="aa91d-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa91d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa91d-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aa91d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aa91d-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa91d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa91d-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa91d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa91d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa91d-117">See also</span></span>

- [<span data-ttu-id="aa91d-118">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="aa91d-118">Profiling Enumerations</span></span>](profiling-enumerations.md)

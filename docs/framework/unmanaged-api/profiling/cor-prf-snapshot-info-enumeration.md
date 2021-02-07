---
description: '詳細情報: COR_PRF_SNAPSHOT_INFO 列挙型'
title: COR_PRF_SNAPSHOT_INFO 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: fcdaeeb6170cb9998281100c5628b3d95f9e9326
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753342"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="50366-103">COR_PRF_SNAPSHOT_INFO 列挙型</span><span class="sxs-lookup"><span data-stu-id="50366-103">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>

<span data-ttu-id="50366-104">プロファイラーの [Stacksnapshotcallback](stacksnapshotcallback-function.md) 関数を呼び出すたびに、スタックスナップショットで返すデータ量を指定します。</span><span class="sxs-lookup"><span data-stu-id="50366-104">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50366-105">構文</span><span class="sxs-lookup"><span data-stu-id="50366-105">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="50366-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="50366-106">Members</span></span>  
  
|<span data-ttu-id="50366-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="50366-107">Members</span></span>|<span data-ttu-id="50366-108">説明</span><span class="sxs-lookup"><span data-stu-id="50366-108">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="50366-109">パラメーターを除くすべてのパラメーターに対して値を渡す必要があることを示し `StackSnapshotCallback` `context` ます。</span><span class="sxs-lookup"><span data-stu-id="50366-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="50366-110">パラメーターを含むすべてのパラメーターに対して値を渡す必要があることを示し `StackSnapshotCallback` `context` ます。</span><span class="sxs-lookup"><span data-stu-id="50366-110">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="50366-111">よりシンプルで代替のスタックウォークアルゴリズムが使用されることを示します。</span><span class="sxs-lookup"><span data-stu-id="50366-111">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50366-112">解説</span><span class="sxs-lookup"><span data-stu-id="50366-112">Remarks</span></span>  

 <span data-ttu-id="50366-113">列挙体によって指定された値 `COR_PRF_SNAPSHOT_INFO` は、パラメーターとして [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="50366-113">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50366-114">要件</span><span class="sxs-lookup"><span data-stu-id="50366-114">Requirements</span></span>  

 <span data-ttu-id="50366-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50366-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50366-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50366-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50366-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50366-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50366-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50366-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50366-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="50366-119">See also</span></span>

- [<span data-ttu-id="50366-120">DoStackSnapshot メソッド</span><span class="sxs-lookup"><span data-stu-id="50366-120">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="50366-121">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="50366-121">Profiling Enumerations</span></span>](profiling-enumerations.md)

---
description: '詳細情報: COR_PRF_REJIT_FLAGS 列挙型'
title: COR_PRF_REJIT_FLAGS 列挙型
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: a27b6d90b51254560f25fbadb18ac95fe838ab2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789022"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="f2302-103">COR_PRF_REJIT_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="f2302-103">COR_PRF_REJIT_FLAGS Enumeration</span></span>

<span data-ttu-id="f2302-104">[ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API の動作を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="f2302-104">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2302-105">構文</span><span class="sxs-lookup"><span data-stu-id="f2302-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="f2302-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f2302-106">Members</span></span>  
  
|<span data-ttu-id="f2302-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="f2302-107">Member</span></span>|<span data-ttu-id="f2302-108">説明</span><span class="sxs-lookup"><span data-stu-id="f2302-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="f2302-109">ReJITted メソッドは、他のメソッドでインライン化されないようにブロックされます。</span><span class="sxs-lookup"><span data-stu-id="f2302-109">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="f2302-110">メソッドをインラインで ReJITted するように `GetFunctionParameters` 要求されたメソッドに対してコールバックを受信します。</span><span class="sxs-lookup"><span data-stu-id="f2302-110">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="f2302-111">要件</span><span class="sxs-lookup"><span data-stu-id="f2302-111">Requirements</span></span>  

 <span data-ttu-id="f2302-112">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2302-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="f2302-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2302-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2302-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2302-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2302-115">**.NET Framework のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2302-115">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f2302-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2302-116">See also</span></span>

- [<span data-ttu-id="f2302-117">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="f2302-117">Profiling Enumerations</span></span>](profiling-enumerations.md)

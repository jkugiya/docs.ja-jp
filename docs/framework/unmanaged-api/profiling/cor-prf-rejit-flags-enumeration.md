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
ms.openlocfilehash: aad66285e9b31558a68b8ccdfc71f103d1772946
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106918"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="b2803-103">COR_PRF_REJIT_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="b2803-103">COR_PRF_REJIT_FLAGS Enumeration</span></span>

<span data-ttu-id="b2803-104">[ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API の動作を示す値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b2803-104">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2803-105">構文</span><span class="sxs-lookup"><span data-stu-id="b2803-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="b2803-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b2803-106">Members</span></span>  
  
|<span data-ttu-id="b2803-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b2803-107">Member</span></span>|<span data-ttu-id="b2803-108">説明</span><span class="sxs-lookup"><span data-stu-id="b2803-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="b2803-109">ReJIT されたメソッドは、他のメソッド内でインライン化されないようにブロックされます。</span><span class="sxs-lookup"><span data-stu-id="b2803-109">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="b2803-110">ReJIT するように要求されたメソッドをインライン化するメソッドの `GetFunctionParameters` コールバックを受信します。</span><span class="sxs-lookup"><span data-stu-id="b2803-110">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="b2803-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="b2803-111">Requirements</span></span>  

 <span data-ttu-id="b2803-112">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2803-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="b2803-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b2803-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2803-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2803-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2803-115">**.NET Framework のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2803-115">**.NET Framework Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b2803-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2803-116">See also</span></span>

- [<span data-ttu-id="b2803-117">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="b2803-117">Profiling Enumerations</span></span>](profiling-enumerations.md)

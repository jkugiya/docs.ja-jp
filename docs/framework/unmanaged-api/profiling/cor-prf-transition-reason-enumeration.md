---
description: '詳細情報: COR_PRF_TRANSITION_REASON 列挙型'
title: COR_PRF_TRANSITION_REASON 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 8d0b7852f80f80a47f910e9f1240a5315772cd23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788996"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="57bdb-103">COR_PRF_TRANSITION_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="57bdb-103">COR_PRF_TRANSITION_REASON Enumeration</span></span>

<span data-ttu-id="57bdb-104">マネージド コードからアンマネージド コードへ、またはその逆の遷移の理由を示します。</span><span class="sxs-lookup"><span data-stu-id="57bdb-104">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57bdb-105">構文</span><span class="sxs-lookup"><span data-stu-id="57bdb-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="57bdb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="57bdb-106">Members</span></span>  
  
|<span data-ttu-id="57bdb-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="57bdb-107">Member</span></span>|<span data-ttu-id="57bdb-108">説明</span><span class="sxs-lookup"><span data-stu-id="57bdb-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="57bdb-109">遷移は、関数の呼び出しによるものです。</span><span class="sxs-lookup"><span data-stu-id="57bdb-109">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="57bdb-110">遷移は、関数からの戻り値によるものです。</span><span class="sxs-lookup"><span data-stu-id="57bdb-110">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57bdb-111">解説</span><span class="sxs-lookup"><span data-stu-id="57bdb-111">Remarks</span></span>  

 <span data-ttu-id="57bdb-112">遷移が発生すると、プロファイラーは [ICorProfilerCallback:: ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) または [ICorProfilerCallback:: UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) コールバックを受け取ります。どちらのコールバックでも、 `COR_PRF_TRANSITION_REASON` 遷移の理由を示す列挙体の値が提供されます。</span><span class="sxs-lookup"><span data-stu-id="57bdb-112">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57bdb-113">要件</span><span class="sxs-lookup"><span data-stu-id="57bdb-113">Requirements</span></span>  

 <span data-ttu-id="57bdb-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57bdb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57bdb-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="57bdb-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="57bdb-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57bdb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57bdb-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57bdb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

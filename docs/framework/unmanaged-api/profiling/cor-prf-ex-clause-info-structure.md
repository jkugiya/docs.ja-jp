---
description: '詳細情報: COR_PRF_EX_CLAUSE_INFO 構造'
title: COR_PRF_EX_CLAUSE_INFO 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
ms.openlocfilehash: af8d404e55a8996abc69923924e87c95e3c5eae8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649209"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="f18ae-103">COR_PRF_EX_CLAUSE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="f18ae-103">COR_PRF_EX_CLAUSE_INFO Structure</span></span>

<span data-ttu-id="f18ae-104">特定の例外句インスタンスおよび関連するフレームに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="f18ae-104">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f18ae-105">構文</span><span class="sxs-lookup"><span data-stu-id="f18ae-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="f18ae-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f18ae-106">Members</span></span>  
  
|<span data-ttu-id="f18ae-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="f18ae-107">Member</span></span>|<span data-ttu-id="f18ae-108">説明</span><span class="sxs-lookup"><span data-stu-id="f18ae-108">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="f18ae-109">入力または左にあるコードの例外句の種類を指定する [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="f18ae-109">A value of the [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="f18ae-110">句ハンドラーのネイティブエントリポイント (たとえば、X86 EIP レジスタの内容)。</span><span class="sxs-lookup"><span data-stu-id="f18ae-110">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="f18ae-111">句ハンドラーの論理フレームへのポインター。たとえば、X86 EBP レジスタの内容。</span><span class="sxs-lookup"><span data-stu-id="f18ae-111">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="f18ae-112">シャドウスタックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f18ae-112">The pointer to the shadow stack.</span></span> <span data-ttu-id="f18ae-113">この値は、BSP レジスタの内容であり、IA64 にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f18ae-113">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f18ae-114">解説</span><span class="sxs-lookup"><span data-stu-id="f18ae-114">Remarks</span></span>  

 <span data-ttu-id="f18ae-115">例外通知が受信されると、 [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)を使用して、実行しようとし `catch` / `finally` ているまたは実行されたばかりの例外句 (フィルター) のネイティブアドレスとフレーム情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f18ae-115">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="f18ae-116">Exception 句の実行には、共通言語ランタイム (CLR) からのこれらのコールバックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f18ae-116">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="f18ae-117">ICorProfilerCallback:: ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="f18ae-117">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="f18ae-118">ICorProfilerCallback:: ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="f18ae-118">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="f18ae-119">ICorProfilerCallback:: ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="f18ae-119">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="f18ae-120">ICorProfilerCallback:: ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="f18ae-120">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="f18ae-121">ICorProfilerCallback:: ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="f18ae-121">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="f18ae-122">ICorProfilerCallback:: ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="f18ae-122">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="f18ae-123">要件</span><span class="sxs-lookup"><span data-stu-id="f18ae-123">Requirements</span></span>  

 <span data-ttu-id="f18ae-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f18ae-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f18ae-125">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="f18ae-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f18ae-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f18ae-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f18ae-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f18ae-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18ae-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f18ae-128">See also</span></span>

- [<span data-ttu-id="f18ae-129">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="f18ae-129">Profiling Structures</span></span>](profiling-structures.md)

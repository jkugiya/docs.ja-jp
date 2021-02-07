---
description: '詳細について: ICorProfilerInfo4:: EnumThreads メソッド'
title: ICorProfilerInfo4::EnumThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: d597e68b8765e135d5bdb403dbdb161b7acbaa9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686935"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="32dfa-103">ICorProfilerInfo4::EnumThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="32dfa-103">ICorProfilerInfo4::EnumThreads Method</span></span>

<span data-ttu-id="32dfa-104">プロファイリングされたプロセス内のすべてのマネージスレッドのコレクションを順番に反復処理するメソッドを提供する列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="32dfa-104">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32dfa-105">構文</span><span class="sxs-lookup"><span data-stu-id="32dfa-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32dfa-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="32dfa-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="32dfa-107">入出力 [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="32dfa-107">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32dfa-108">解説</span><span class="sxs-lookup"><span data-stu-id="32dfa-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32dfa-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="32dfa-109">Requirements</span></span>  

 <span data-ttu-id="32dfa-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32dfa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32dfa-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32dfa-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32dfa-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32dfa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32dfa-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32dfa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32dfa-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="32dfa-114">See also</span></span>

- [<span data-ttu-id="32dfa-115">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32dfa-115">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="32dfa-116">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32dfa-116">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="32dfa-117">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="32dfa-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="32dfa-118">プロファイル</span><span class="sxs-lookup"><span data-stu-id="32dfa-118">Profiling</span></span>](index.md)

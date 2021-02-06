---
description: '詳細について: ICorProfilerInfo3:: EnumJITedFunctions メソッド'
title: ICorProfilerInfo3::EnumJITedFunctions メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: 2f5f8358e7f01c20fc6edee60869bad01b0936c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646934"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="40fb5-103">ICorProfilerInfo3::EnumJITedFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="40fb5-103">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>

<span data-ttu-id="40fb5-104">以前に JIT でコンパイルされたすべての関数の列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="40fb5-104">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40fb5-105">構文</span><span class="sxs-lookup"><span data-stu-id="40fb5-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40fb5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="40fb5-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="40fb5-107">入出力 [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) 列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="40fb5-107">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40fb5-108">解説</span><span class="sxs-lookup"><span data-stu-id="40fb5-108">Remarks</span></span>  

 <span data-ttu-id="40fb5-109">このメソッドは `JITCompilation` 、 [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) メソッドなどのコールバックと重複する場合があります。</span><span class="sxs-lookup"><span data-stu-id="40fb5-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="40fb5-110">このメソッドによって返される列挙子には、Ngen.exe で生成されたネイティブイメージから読み込まれた関数は含まれません。</span><span class="sxs-lookup"><span data-stu-id="40fb5-110">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40fb5-111">返された列挙体には、フィールドの値に対して "0" のみが含まれ `COR_PRF_FUNCTION::reJitId` ます。</span><span class="sxs-lookup"><span data-stu-id="40fb5-111">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="40fb5-112">有効な値が必要な場合は `COR_PRF_FUNCTION::reJitId` 、 [ICorProfilerInfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="40fb5-112">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40fb5-113">要件</span><span class="sxs-lookup"><span data-stu-id="40fb5-113">Requirements</span></span>  

 <span data-ttu-id="40fb5-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40fb5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40fb5-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="40fb5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40fb5-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40fb5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40fb5-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40fb5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40fb5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="40fb5-118">See also</span></span>

- [<span data-ttu-id="40fb5-119">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40fb5-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="40fb5-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="40fb5-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="40fb5-121">プロファイル</span><span class="sxs-lookup"><span data-stu-id="40fb5-121">Profiling</span></span>](index.md)

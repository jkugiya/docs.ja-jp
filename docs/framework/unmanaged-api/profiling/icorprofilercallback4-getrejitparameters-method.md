---
description: '詳細について: ICorProfilerCallback4:: GetReJITParameters メソッド'
title: ICorProfilerCallback4::GetReJITParameters メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: f8dbf2c6ae80e41b8427fdaf0ef617a83138bb14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788762"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="bf9be-103">ICorProfilerCallback4::GetReJITParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="bf9be-103">ICorProfilerCallback4::GetReJITParameters Method</span></span>

<span data-ttu-id="bf9be-104">再コンパイルされた新しいメソッド本体の代替コード生成フラグをコードプロファイラーで設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="bf9be-104">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf9be-105">構文</span><span class="sxs-lookup"><span data-stu-id="bf9be-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf9be-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf9be-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="bf9be-107">からCLR が JIT 再コンパイルパラメーターを必要とするメソッドを含むモジュール。</span><span class="sxs-lookup"><span data-stu-id="bf9be-107">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="bf9be-108">から `MethodDef` CLR が JIT 再コンパイルパラメーターを必要とするメソッドの。</span><span class="sxs-lookup"><span data-stu-id="bf9be-108">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="bf9be-109">から再コンパイルされるメソッドの JIT 再コンパイル情報を提供するためにプロファイラーが使用できる [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bf9be-109">[in] A pointer to an [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf9be-110">解説</span><span class="sxs-lookup"><span data-stu-id="bf9be-110">Remarks</span></span>  

 <span data-ttu-id="bf9be-111">CLR は、 `GetReJITParameters` 指定されたメソッドを再コンパイルするためのパラメーターをプロファイラーが指定できるように、コールバックを発行します。</span><span class="sxs-lookup"><span data-stu-id="bf9be-111">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="bf9be-112">`GetReJITParameters`コールバックは、関数ごとに1回だけ発行されます。プロファイラーによって提供されるパラメーターは、その関数のすべてのインスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="bf9be-112">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf9be-113">要件</span><span class="sxs-lookup"><span data-stu-id="bf9be-113">Requirements</span></span>  

 <span data-ttu-id="bf9be-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf9be-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf9be-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf9be-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf9be-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf9be-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf9be-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf9be-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf9be-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf9be-118">See also</span></span>

- [<span data-ttu-id="bf9be-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf9be-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="bf9be-120">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf9be-120">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="bf9be-121">JITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="bf9be-121">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="bf9be-122">ReJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="bf9be-122">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)

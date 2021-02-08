---
description: '詳細について: ICorProfilerCallback4:: ReJITError メソッド'
title: ICorProfilerCallback4::ReJITError メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: f5173d90e65a1e9f1049ba7eadc1ce9cf7630096
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788697"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="38360-103">ICorProfilerCallback4::ReJITError メソッド</span><span class="sxs-lookup"><span data-stu-id="38360-103">ICorProfilerCallback4::ReJITError Method</span></span>

<span data-ttu-id="38360-104">Just-in-time (JIT) コンパイラが再コンパイルプロセスでエラーを検出したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="38360-104">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38360-105">構文</span><span class="sxs-lookup"><span data-stu-id="38360-105">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38360-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38360-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="38360-107">から再 `ModuleID` コンパイルの試行が失敗した。</span><span class="sxs-lookup"><span data-stu-id="38360-107">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="38360-108">から再 `MethodDef` コンパイルの試行が失敗したメソッドの。</span><span class="sxs-lookup"><span data-stu-id="38360-108">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="38360-109">から再コンパイルまたは再コンパイルのマークが付けられている関数インスタンス。</span><span class="sxs-lookup"><span data-stu-id="38360-109">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="38360-110">この値は、インスタンス化ごとではなく、メソッドごとにエラーが発生した場合に発生する可能性があり `NULL` ます (たとえば、プロファイラーが、再コンパイルするメソッドに対して無効なメタデータトークンを指定した場合など)。</span><span class="sxs-lookup"><span data-stu-id="38360-110">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="38360-111">からエラーの性質を示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="38360-111">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="38360-112">値の一覧については、「Status HRESULT」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="38360-112">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38360-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="38360-113">Return Value</span></span>  

 <span data-ttu-id="38360-114">このコールバックからの戻り値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="38360-114">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="38360-115">状態 HRESULT</span><span class="sxs-lookup"><span data-stu-id="38360-115">Status HRESULTS</span></span>  
  
|<span data-ttu-id="38360-116">状態配列 HRESULT</span><span class="sxs-lookup"><span data-stu-id="38360-116">Status array HRESULT</span></span>|<span data-ttu-id="38360-117">説明</span><span class="sxs-lookup"><span data-stu-id="38360-117">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="38360-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="38360-118">E_INVALIDARG</span></span>|<span data-ttu-id="38360-119">`moduleID`または `methodDef` トークンが `NULL` です。</span><span class="sxs-lookup"><span data-stu-id="38360-119">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="38360-120">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="38360-120">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="38360-121">モジュールが完全に読み込まれていないか、またはアンロード中です。</span><span class="sxs-lookup"><span data-stu-id="38360-121">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="38360-122">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="38360-122">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="38360-123">指定されたモジュールは (などによって) 動的に生成された `Reflection.Emit` ため、このメソッドではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="38360-123">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="38360-124">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="38360-124">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="38360-125">メソッドは、収集可能なアセンブリにインスタンス化されるため、再コンパイルできません。</span><span class="sxs-lookup"><span data-stu-id="38360-125">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="38360-126">非リフレクションコンテキスト (たとえば、) で定義されている型と関数は、 `List<MyCollectibleStruct>` 収集可能なアセンブリにインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="38360-126">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="38360-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="38360-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="38360-128">CLR は、指定されたメソッドに JIT 再コンパイルのマークを付けようとしている間にメモリ不足になりました。</span><span class="sxs-lookup"><span data-stu-id="38360-128">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="38360-129">その他</span><span class="sxs-lookup"><span data-stu-id="38360-129">Other</span></span>|<span data-ttu-id="38360-130">オペレーティング システムは、CLR 制御範囲外のエラーを返しました。</span><span class="sxs-lookup"><span data-stu-id="38360-130">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="38360-131">たとえば、メモリページのアクセス保護を変更するシステムコールが失敗した場合、オペレーティングシステムエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="38360-131">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38360-132">要件</span><span class="sxs-lookup"><span data-stu-id="38360-132">Requirements</span></span>  

 <span data-ttu-id="38360-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38360-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38360-134">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38360-134">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38360-135">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38360-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38360-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38360-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38360-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="38360-137">See also</span></span>

- [<span data-ttu-id="38360-138">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38360-138">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="38360-139">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38360-139">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)

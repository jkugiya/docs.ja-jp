---
description: '詳細について: ICorProfilerInfo3:: GetFunctionEnter3Info メソッド'
title: ICorProfilerInfo3::GetFunctionEnter3Info メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
ms.openlocfilehash: 3e6c0cfbf2518301e62ed5c57e956190066504ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646817"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="7b781-103">ICorProfilerInfo3::GetFunctionEnter3Info メソッド</span><span class="sxs-lookup"><span data-stu-id="7b781-103">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>

<span data-ttu-id="7b781-104">[FunctionEnter3WithInfo](functionenter3withinfo-function.md)関数によってプロファイラーに報告される関数のスタックフレームと引数の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="7b781-104">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="7b781-105">このメソッドは、`FunctionEnter3WithInfo` コールバック中にのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7b781-105">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b781-106">構文</span><span class="sxs-lookup"><span data-stu-id="7b781-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b781-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7b781-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="7b781-108">[in] 入力される関数の `FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="7b781-108">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="7b781-109">[in] 特定のスタック フレームに関する情報を表す不透明ハンドル。</span><span class="sxs-lookup"><span data-stu-id="7b781-109">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="7b781-110">プロファイラーは、 `eltInfo` [FunctionEnter3WithInfo](functionenter3withinfo-function.md) 関数によって指定されたものと同じものを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b781-110">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="7b781-111">[out] 特定のスタック フレームに関するジェネリック情報を表す不透明ハンドル。</span><span class="sxs-lookup"><span data-stu-id="7b781-111">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="7b781-112">このハンドルは、プロファイラーが `FunctionEnter3WithInfo` メソッドを呼び出した `GetFunctionEnter3Info` コールバック内でのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="7b781-112">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="7b781-113">[入力、出力] [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) 構造体の合計サイズ (バイト単位) へのポインター。は、によって示される引数範囲の追加の [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) 構造体を加算したもの `pArgumentInfo` です。</span><span class="sxs-lookup"><span data-stu-id="7b781-113">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="7b781-114">指定されたサイズの大きさが十分でない場合、ERROR_INSUFFICIENT_BUFFER が戻り、必要なサイズが `pcbArgumentInfo` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="7b781-114">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="7b781-115">`GetFunctionEnter3Info` を呼び出して `*pcbArgumentInfo` の必要な値を取得するには、`*pcbArgumentInfo` を 0 に、`pArgumentInfo` を NULL にそれぞれ設定します。</span><span class="sxs-lookup"><span data-stu-id="7b781-115">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="7b781-116">入出力メモリ内の関数の引数の位置を左から右の順序で記述する [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7b781-116">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b781-117">解説</span><span class="sxs-lookup"><span data-stu-id="7b781-117">Remarks</span></span>  

 <span data-ttu-id="7b781-118">プロファイラーは、調べている関数の `COR_PRF_FUNCTION_ARGUMENT_INFO` 構造体に十分な領域を割り当て、`pcbArgumentInfo` パラメーターでサイズを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b781-118">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b781-119">要件</span><span class="sxs-lookup"><span data-stu-id="7b781-119">Requirements</span></span>  

 <span data-ttu-id="7b781-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b781-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b781-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b781-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b781-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b781-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b781-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b781-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b781-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b781-124">See also</span></span>

- [<span data-ttu-id="7b781-125">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7b781-125">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="7b781-126">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7b781-126">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="7b781-127">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7b781-127">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="7b781-128">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b781-128">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="7b781-129">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b781-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7b781-130">プロファイル</span><span class="sxs-lookup"><span data-stu-id="7b781-130">Profiling</span></span>](index.md)

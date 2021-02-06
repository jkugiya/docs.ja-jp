---
description: '詳細について: ICorProfilerInfo3:: GetFunctionTailcall3Info メソッド'
title: ICorProfilerInfo3::GetFunctionTailcall3Info メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: a8976a11cf7a2c556afa62a559e3a294d81b9a1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646802"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="2c46d-103">ICorProfilerInfo3::GetFunctionTailcall3Info メソッド</span><span class="sxs-lookup"><span data-stu-id="2c46d-103">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>

<span data-ttu-id="2c46d-104">[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)関数によってプロファイラーに報告される関数のスタックフレームを提供します。</span><span class="sxs-lookup"><span data-stu-id="2c46d-104">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="2c46d-105">このメソッドは、`FunctionTailcall3WithInfo` コールバック中にのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2c46d-105">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c46d-106">構文</span><span class="sxs-lookup"><span data-stu-id="2c46d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c46d-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2c46d-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="2c46d-108">からを `FunctionID` 返す関数の。</span><span class="sxs-lookup"><span data-stu-id="2c46d-108">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="2c46d-109">[in] 特定のスタック フレームに関する情報を表す不透明ハンドル。</span><span class="sxs-lookup"><span data-stu-id="2c46d-109">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="2c46d-110">プロファイラーは、 `eltInfo` 関数によってプロファイラーに与えられたものと同じを提供する必要があり `FunctionTailcall3WithInfo` ます。</span><span class="sxs-lookup"><span data-stu-id="2c46d-110">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="2c46d-111">[out] 特定のスタック フレームに関するジェネリック情報を表す不透明ハンドル。</span><span class="sxs-lookup"><span data-stu-id="2c46d-111">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="2c46d-112">このハンドルは、プロファイラーが `FunctionTailcall3WithInfo` メソッドを呼び出した `GetFunctionTailcall3Info` コールバック内でのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="2c46d-112">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c46d-113">解説</span><span class="sxs-lookup"><span data-stu-id="2c46d-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c46d-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="2c46d-114">Requirements</span></span>  

 <span data-ttu-id="2c46d-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c46d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c46d-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c46d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c46d-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c46d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c46d-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c46d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c46d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c46d-119">See also</span></span>

- [<span data-ttu-id="2c46d-120">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="2c46d-120">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="2c46d-121">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="2c46d-121">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="2c46d-122">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="2c46d-122">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="2c46d-123">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c46d-123">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="2c46d-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c46d-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2c46d-125">プロファイル</span><span class="sxs-lookup"><span data-stu-id="2c46d-125">Profiling</span></span>](index.md)

---
description: '詳細について: ICorProfilerCallback3:: InitializeForAttach メソッド'
title: ICorProfilerCallback3::InitializeForAttach メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
ms.openlocfilehash: b3c5b8701df9e680e4fcbd57f4e08395dfe0b8da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788814"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="f6500-103">ICorProfilerCallback3::InitializeForAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="f6500-103">ICorProfilerCallback3::InitializeForAttach Method</span></span>

<span data-ttu-id="f6500-104">アタッチ操作後にその状態を初期化する機会をプロファイラーに与えるために、共通言語ランタイム (CLR) により呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f6500-104">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6500-105">構文</span><span class="sxs-lookup"><span data-stu-id="f6500-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6500-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f6500-106">Parameters</span></span>  

 `pCorProfilerInfoUnk`  
 <span data-ttu-id="f6500-107">[in] `ICorProfilerInfo*` インターフェイスへのインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="f6500-107">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="f6500-108">からパラメーターの [IClrProfiling:: AttachProfiler](iclrprofiling-attachprofiler-method.md) メソッドに渡されるデータへのポインター `pvClientData` 。</span><span class="sxs-lookup"><span data-stu-id="f6500-108">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="f6500-109">このパラメーターが null の場合、`cbClientData` は 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="f6500-109">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="f6500-110">CLR は、`InitializeForAttach` から戻るとこのメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="f6500-110">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="f6500-111">[in] `pvClientData` がポイントするデータのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="f6500-111">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6500-112">解説</span><span class="sxs-lookup"><span data-stu-id="f6500-112">Remarks</span></span>  

 <span data-ttu-id="f6500-113">CLR は `InitializeForAttach` を呼び出し、コールバックを要求できる機会をプロファイラーに与えます。</span><span class="sxs-lookup"><span data-stu-id="f6500-113">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6500-114">要件</span><span class="sxs-lookup"><span data-stu-id="f6500-114">Requirements</span></span>  

 <span data-ttu-id="f6500-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6500-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6500-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f6500-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f6500-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6500-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6500-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6500-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6500-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6500-119">See also</span></span>

- [<span data-ttu-id="f6500-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6500-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f6500-121">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6500-121">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f6500-122">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6500-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f6500-123">プロファイル</span><span class="sxs-lookup"><span data-stu-id="f6500-123">Profiling</span></span>](index.md)

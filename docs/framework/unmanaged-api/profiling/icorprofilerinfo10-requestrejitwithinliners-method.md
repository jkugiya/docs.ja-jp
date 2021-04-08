---
description: '詳細情報: ICorProfilerInfo10::RequestReJITWithInliners メソッド'
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 925a61bf2521950cad7fb0dce8f1484198f3f806
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106515"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="11dca-103">ICorProfilerInfo10::RequestReJITWithInliners メソッド</span><span class="sxs-lookup"><span data-stu-id="11dca-103">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="11dca-104">要求されたメソッドに加えて、要求されたメソッドのすべてのインライナも ReJIT します。</span><span class="sxs-lookup"><span data-stu-id="11dca-104">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="11dca-105">構文</span><span class="sxs-lookup"><span data-stu-id="11dca-105">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="11dca-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11dca-106">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="11dca-107">\[入力] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md) のビットマスク。</span><span class="sxs-lookup"><span data-stu-id="11dca-107">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="11dca-108">\[入力] 再コンパイルする関数の数。</span><span class="sxs-lookup"><span data-stu-id="11dca-108">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="11dca-109">\[入力] 再コンパイルする関数を識別する (`module`, `methodDef`) ペアの `moduleId` 部分を指定します。</span><span class="sxs-lookup"><span data-stu-id="11dca-109">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="11dca-110">\[入力] 再コンパイルする関数を識別する (`module`, `methodDef`) ペアの `methodId` 部分を指定します。</span><span class="sxs-lookup"><span data-stu-id="11dca-110">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="11dca-111">解説</span><span class="sxs-lookup"><span data-stu-id="11dca-111">Remarks</span></span>

<span data-ttu-id="11dca-112">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) では、インライン化されたメソッドの追跡は行われません。</span><span class="sxs-lookup"><span data-stu-id="11dca-112">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="11dca-113">プロファイラーは、インライン化をブロックするか、または、インライン化を追跡し、すべてのインライナに対して `RequestReJIT` を呼び出すことで、インライン化されたメソッドの各インスタンスが確実に ReJIT されるようにする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="11dca-113">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="11dca-114">インライン化を監視するためのプロファイラーは存在しないため、これにより、アタッチ時に ReJIT に関する問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="11dca-114">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="11dca-115">このメソッドを呼び出すと、インライナの完全なセットも ReJIT されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="11dca-115">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="11dca-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="11dca-116">Requirements</span></span>

<span data-ttu-id="11dca-117">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="11dca-117">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="11dca-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11dca-118">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="11dca-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11dca-119">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="11dca-120">**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11dca-120">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="11dca-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="11dca-121">See also</span></span>

- [<span data-ttu-id="11dca-122">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11dca-122">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)

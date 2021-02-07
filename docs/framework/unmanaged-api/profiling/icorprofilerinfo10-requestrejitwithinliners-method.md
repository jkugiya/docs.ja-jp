---
description: '詳細について: ICorProfilerInfo10:: RequestReJITWithInliners メソッド'
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
ms.openlocfilehash: da3434926b36408adfdee2171d56f23ba764f0eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753264"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="4d7b0-103">ICorProfilerInfo10:: RequestReJITWithInliners メソッド</span><span class="sxs-lookup"><span data-stu-id="4d7b0-103">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="4d7b0-104">要求されたメソッドのほか、要求されたメソッドの inliners を再適用します。</span><span class="sxs-lookup"><span data-stu-id="4d7b0-104">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d7b0-105">構文</span><span class="sxs-lookup"><span data-stu-id="4d7b0-105">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="4d7b0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4d7b0-106">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="4d7b0-107">\[in) [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)のビットマスク。</span><span class="sxs-lookup"><span data-stu-id="4d7b0-107">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="4d7b0-108">\[in] 再コンパイルする関数の数。</span><span class="sxs-lookup"><span data-stu-id="4d7b0-108">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="4d7b0-109">\[in] は、再 `moduleId` `module` コンパイルする関数を識別する (、) ペアの部分を指定し `methodDef` ます。</span><span class="sxs-lookup"><span data-stu-id="4d7b0-109">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="4d7b0-110">\[in] は、再 `methodId` `module` コンパイルする関数を識別する (、) ペアの部分を指定し `methodDef` ます。</span><span class="sxs-lookup"><span data-stu-id="4d7b0-110">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d7b0-111">解説</span><span class="sxs-lookup"><span data-stu-id="4d7b0-111">Remarks</span></span>

<span data-ttu-id="4d7b0-112">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) では、インラインメソッドの追跡は行われません。</span><span class="sxs-lookup"><span data-stu-id="4d7b0-112">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="4d7b0-113">プロファイラーは、インライン化された `RequestReJIT` メソッドのすべてのインスタンスが ReJITted であることを確認するために、インライン展開をブロックするか、インライン展開を追跡し、すべての inliners に対してを呼び出す必要がありました</span><span class="sxs-lookup"><span data-stu-id="4d7b0-113">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="4d7b0-114">これにより、再インライン化を監視するためのプロファイラーが存在しないため、ReJIT on attach に問題が生じます。</span><span class="sxs-lookup"><span data-stu-id="4d7b0-114">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="4d7b0-115">このメソッドを呼び出すことにより、inliners の完全なセットも ReJITted になることを保証できます。</span><span class="sxs-lookup"><span data-stu-id="4d7b0-115">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="4d7b0-116">要件</span><span class="sxs-lookup"><span data-stu-id="4d7b0-116">Requirements</span></span>

<span data-ttu-id="4d7b0-117">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d7b0-117">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="4d7b0-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4d7b0-118">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="4d7b0-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d7b0-119">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="4d7b0-120">**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d7b0-120">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4d7b0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d7b0-121">See also</span></span>

- [<span data-ttu-id="4d7b0-122">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d7b0-122">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)

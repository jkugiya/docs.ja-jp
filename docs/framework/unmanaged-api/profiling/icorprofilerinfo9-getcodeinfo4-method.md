---
description: '詳細情報: ICorProfilerInfo9::GetCodeInfo4 メソッド'
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c7897e266fbb84d44df719c127e24bd375b560bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759092"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="19516-103">ICorProfilerInfo9::GetCodeInfo4 メソッド</span><span class="sxs-lookup"><span data-stu-id="19516-103">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="19516-104">ネイティブ コードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。</span><span class="sxs-lookup"><span data-stu-id="19516-104">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="19516-105">構文</span><span class="sxs-lookup"><span data-stu-id="19516-105">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="19516-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="19516-106">Parameters</span></span>

<span data-ttu-id="19516-107">`pNativeCodeStartAddress` [in] ネイティブ関数の開始へのポインター。</span><span class="sxs-lookup"><span data-stu-id="19516-107">`pNativeCodeStartAddress` [in] A pointer to the start of a native function.</span></span>

<span data-ttu-id="19516-108">`cCodeInfos` [in] `codeInfos` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="19516-108">`cCodeInfos` [in] The size of the `codeInfos` array.</span></span>

<span data-ttu-id="19516-109">`pcCodeInfos` [out] 使用できる [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="19516-109">`pcCodeInfos` [out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

<span data-ttu-id="19516-110">`codeInfos` [out] 呼び出し元が提供したバッファー。</span><span class="sxs-lookup"><span data-stu-id="19516-110">`codeInfos` [out] A caller-provided buffer.</span></span> <span data-ttu-id="19516-111">メソッドから制御が戻った後で、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` の構造体の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="19516-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="19516-112">解説</span><span class="sxs-lookup"><span data-stu-id="19516-112">Remarks</span></span>

<span data-ttu-id="19516-113">`GetCodeInfo4` メソッドは、メソッドのさまざまなネイティブ バージョンのコード情報を参照できることを除いて、[GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md) に似ています。</span><span class="sxs-lookup"><span data-stu-id="19516-113">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="19516-114">`GetCodeInfo4` によって、ガベージ コレクションをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="19516-114">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="19516-115">エクステントは共通中間言語 (CIL) オフセットの昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="19516-115">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="19516-116">`GetCodeInfo4` から制御が戻ったら、`codeInfos` バッファーのサイズが十分で、すべての [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体を格納できることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19516-116">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="19516-117">これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="19516-117">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="19516-118">[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体のサイズによって除算された `cCodeInfos` が `pcCodeInfos` より小さい場合は、`codeInfos` バッファーの割り当てを増やし、`cCodeInfos` を新しい大きいサイズに更新した後、`GetCodeInfo4` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="19516-118">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="19516-119">別の方法として、最初に `GetCodeInfo4` を長さゼロの `codeInfos` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="19516-119">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="19516-120">その後 `codeInfos` バッファーのサイズを、`pcCodeInfos` で返された値と、[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体のサイズを乗算した値に設定し、`GetCodeInfo4` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="19516-120">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="19516-121">要件</span><span class="sxs-lookup"><span data-stu-id="19516-121">Requirements</span></span>

<span data-ttu-id="19516-122">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="19516-122">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="19516-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="19516-123">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="19516-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19516-124">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="19516-125">**.NET のバージョン:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19516-125">**.NET Versions:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="19516-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="19516-126">See also</span></span>

- [<span data-ttu-id="19516-127">ICorProfilerInfo9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19516-127">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)

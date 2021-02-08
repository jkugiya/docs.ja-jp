---
description: '詳細について: ICorProfilerInfo9:: GetCodeInfo4 メソッド'
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
ms.openlocfilehash: 765f3dfee6c56148eb7807b0606e79d4b3a2e7a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783808"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="b5d29-103">ICorProfilerInfo9:: GetCodeInfo4 メソッド</span><span class="sxs-lookup"><span data-stu-id="b5d29-103">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="b5d29-104">ネイティブコードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。</span><span class="sxs-lookup"><span data-stu-id="b5d29-104">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5d29-105">構文</span><span class="sxs-lookup"><span data-stu-id="b5d29-105">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="b5d29-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5d29-106">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="b5d29-107">\[) ネイティブ関数の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b5d29-107">\[in] A pointer to the start of a native function.</span></span>

- `cCodeInfos`

  <span data-ttu-id="b5d29-108">\[in] 配列のサイズ `codeInfos` 。</span><span class="sxs-lookup"><span data-stu-id="b5d29-108">\[in] The size of the `codeInfos` array.</span></span>

- `pcCodeInfos`

  <span data-ttu-id="b5d29-109">\[out] 使用可能な [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b5d29-109">\[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

- `codeInfos`

  <span data-ttu-id="b5d29-110">\[out] 呼び出し元が指定したバッファー。</span><span class="sxs-lookup"><span data-stu-id="b5d29-110">\[out] A caller-provided buffer.</span></span> <span data-ttu-id="b5d29-111">メソッドから制御が戻った後で、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` の構造体の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b5d29-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5d29-112">解説</span><span class="sxs-lookup"><span data-stu-id="b5d29-112">Remarks</span></span>

<span data-ttu-id="b5d29-113">メソッドは、 `GetCodeInfo4` メソッドのさまざまなネイティブバージョンのコード情報を検索できる点を除いて、 [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md)に似ています。</span><span class="sxs-lookup"><span data-stu-id="b5d29-113">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="b5d29-114">`GetCodeInfo4` ガベージコレクションをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="b5d29-114">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="b5d29-115">エクステントは共通中間言語 (CIL) オフセットの昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="b5d29-115">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="b5d29-116">が返された後 `GetCodeInfo4` 、バッファーが `codeInfos` すべての [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造を格納するのに十分な大きさであったことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5d29-116">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="b5d29-117">これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="b5d29-117">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="b5d29-118">`cCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)構造体のサイズで除算されたがより小さい場合は `pcCodeInfos` 、大きいバッファーを割り当て、を `codeInfos` `cCodeInfos` 新しい大きいサイズに更新して、を `GetCodeInfo4` 再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b5d29-118">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="b5d29-119">別の方法として、最初に `GetCodeInfo4` を長さゼロの `codeInfos` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="b5d29-119">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="b5d29-120">次に、 `codeInfos` バッファーサイズをで返された値に設定し、 `pcCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体のサイズを乗算して、を `GetCodeInfo4` 再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b5d29-120">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="b5d29-121">要件</span><span class="sxs-lookup"><span data-stu-id="b5d29-121">Requirements</span></span>

<span data-ttu-id="b5d29-122">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5d29-122">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="b5d29-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b5d29-123">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b5d29-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5d29-124">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b5d29-125">**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5d29-125">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b5d29-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5d29-126">See also</span></span>

- [<span data-ttu-id="b5d29-127">ICorProfilerInfo9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5d29-127">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)

---
description: '詳細について: ICorProfilerInfo4:: GetCodeInfo3 メソッド'
title: ICorProfilerInfo4::GetCodeInfo3 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
ms.openlocfilehash: 6bc2beb291101257448ab58ac9a93362005fecbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686828"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="d70bf-103">ICorProfilerInfo4::GetCodeInfo3 メソッド</span><span class="sxs-lookup"><span data-stu-id="d70bf-103">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>

<span data-ttu-id="d70bf-104">指定した関数の JIT 再コンパイル バージョンに関連付けられているネイティブ コードの範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="d70bf-104">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="d70bf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d70bf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d70bf-106">Parameters</span></span>  

 `functionID`  
 <span data-ttu-id="d70bf-107">[in] ネイティブ コードが関連付けられている関数の ID。</span><span class="sxs-lookup"><span data-stu-id="d70bf-107">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="d70bf-108">[in] JIT 再コンパイルされた関数のID。</span><span class="sxs-lookup"><span data-stu-id="d70bf-108">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="d70bf-109">[in] `codeInfos` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="d70bf-109">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="d70bf-110">入出力使用可能な [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体の合計数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d70bf-110">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="d70bf-111">[out] 呼び出し元が提供したバッファー。</span><span class="sxs-lookup"><span data-stu-id="d70bf-111">[out] A caller-provided buffer.</span></span> <span data-ttu-id="d70bf-112">メソッドから制御が戻った後で、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` の構造体の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d70bf-112">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d70bf-113">解説</span><span class="sxs-lookup"><span data-stu-id="d70bf-113">Remarks</span></span>  

 <span data-ttu-id="d70bf-114">`GetCodeInfo3`メソッドは、指定された IP アドレスを含む関数の JIT 再コンパイルされた ID を取得する点を除いて、 [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)に似ています。</span><span class="sxs-lookup"><span data-stu-id="d70bf-114">The `GetCodeInfo3` method is similar to [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d70bf-115">`GetCodeInfo3` はガベージコレクションをトリガーできますが、 [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) はトリガーしません。</span><span class="sxs-lookup"><span data-stu-id="d70bf-115">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="d70bf-116">詳細については、 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d70bf-116">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="d70bf-117">エクステントは共通中間言語 (CIL) オフセットの昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="d70bf-117">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="d70bf-118">が返された後 `GetCodeInfo3` 、バッファーが `codeInfos` すべての [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造を格納するのに十分な大きさであったことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d70bf-118">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="d70bf-119">これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="d70bf-119">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="d70bf-120">`cCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)構造体のサイズで除算されたがより小さい場合は `pcCodeInfos` 、大きいバッファーを割り当て、を `codeInfos` `cCodeInfos` 新しい大きいサイズに更新して、を `GetCodeInfo3` 再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d70bf-120">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="d70bf-121">別の方法として、最初に `GetCodeInfo3` を長さゼロの `codeInfos` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="d70bf-121">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d70bf-122">次に、 `codeInfos` バッファーサイズをで返された値に設定し、 `pcCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体のサイズを乗算して、を `GetCodeInfo3` 再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d70bf-122">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d70bf-123">要件</span><span class="sxs-lookup"><span data-stu-id="d70bf-123">Requirements</span></span>  

 <span data-ttu-id="d70bf-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d70bf-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d70bf-125">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d70bf-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d70bf-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d70bf-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d70bf-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d70bf-127">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d70bf-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d70bf-128">See also</span></span>

- [<span data-ttu-id="d70bf-129">GetCodeInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="d70bf-129">GetCodeInfo2 Method</span></span>](icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="d70bf-130">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d70bf-130">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="d70bf-131">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d70bf-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d70bf-132">プロファイル</span><span class="sxs-lookup"><span data-stu-id="d70bf-132">Profiling</span></span>](index.md)

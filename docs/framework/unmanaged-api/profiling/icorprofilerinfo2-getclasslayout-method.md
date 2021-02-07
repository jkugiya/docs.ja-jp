---
description: '詳細について: ICorProfilerInfo2:: GetClassLayout メソッド'
title: ICorProfilerInfo2::GetClassLayout メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
ms.openlocfilehash: 6b515ff84240e227914404379efcfc063c25c5a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760480"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="b5034-103">ICorProfilerInfo2::GetClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="b5034-103">ICorProfilerInfo2::GetClassLayout Method</span></span>

<span data-ttu-id="b5034-104">指定したクラスで定義されるフィールドのメモリ内レイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="b5034-104">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="b5034-105">つまり、このメソッドはクラスのフィールドのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="b5034-105">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5034-106">構文</span><span class="sxs-lookup"><span data-stu-id="b5034-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5034-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5034-107">Parameters</span></span>  

 `classID`  
 <span data-ttu-id="b5034-108">[in] レイアウトを取得するクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="b5034-108">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="b5034-109">[入力、出力] [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) 構造体の配列。各構造体には、クラスのフィールドのトークンとオフセットが格納されます。</span><span class="sxs-lookup"><span data-stu-id="b5034-109">[in, out] An array of [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="b5034-110">[in] `rFieldOffset` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="b5034-110">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="b5034-111">[out] 使用できる要素の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b5034-111">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="b5034-112">`cFieldOffset` が 0 である場合、この値は必要な要素の数を示します。</span><span class="sxs-lookup"><span data-stu-id="b5034-112">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="b5034-113">[out] クラスのサイズ (バイト単位) を含む位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b5034-113">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5034-114">解説</span><span class="sxs-lookup"><span data-stu-id="b5034-114">Remarks</span></span>  

 <span data-ttu-id="b5034-115">`GetClassLayout` メソッドは、クラス自体によって定義されているフィールドのみを返します。</span><span class="sxs-lookup"><span data-stu-id="b5034-115">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="b5034-116">クラスの親クラスもフィールドを定義している場合、プロファイラーは親クラスで `GetClassLayout` を呼び出してそのフィールドを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5034-116">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="b5034-117">`GetClassLayout` を文字列クラスと一緒に使用する場合、このメソッドは E_INVALIDARG というエラー コードで失敗します。</span><span class="sxs-lookup"><span data-stu-id="b5034-117">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="b5034-118">文字列のレイアウトに関する情報を取得するには、 [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b5034-118">Use [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="b5034-119">`GetClassLayout` は、配列クラスを使用して呼び出される場合も失敗します。</span><span class="sxs-lookup"><span data-stu-id="b5034-119">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="b5034-120">`GetClassLayout` から制御が戻ったら、`rFieldOffset` バッファーのサイズが十分で、すべての使用可能な `COR_FIELD_OFFSET` 構造体を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5034-120">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="b5034-121">これを行うには、`pcFieldOffset` が指している値と、`rFieldOffset` のサイズを `COR_FIELD_OFFSET` 構造体のサイズで割った値を比較します。</span><span class="sxs-lookup"><span data-stu-id="b5034-121">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="b5034-122">`rFieldOffset` の大きさが十分でない場合は、`rFieldOffset` バッファーの割り当てを増やし、`cFieldOffset` を新しい大きいサイズに更新して、`GetClassLayout` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b5034-122">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="b5034-123">別の方法として、最初に `GetClassLayout` を長さゼロの `rFieldOffset` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="b5034-123">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="b5034-124">その後、バッファーのサイズを `pcFieldOffset` で返された値に設定し、`GetClassLayout` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b5034-124">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5034-125">要件</span><span class="sxs-lookup"><span data-stu-id="b5034-125">Requirements</span></span>  

 <span data-ttu-id="b5034-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5034-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5034-127">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b5034-127">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5034-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5034-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5034-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5034-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5034-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5034-130">See also</span></span>

- [<span data-ttu-id="b5034-131">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5034-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="b5034-132">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5034-132">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="b5034-133">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5034-133">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b5034-134">プロファイル</span><span class="sxs-lookup"><span data-stu-id="b5034-134">Profiling</span></span>](index.md)

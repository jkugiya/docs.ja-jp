---
description: '詳細について: ICorProfilerInfo:: GetILToNativeMapping メソッド'
title: ICorProfilerInfo::GetILToNativeMapping メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
ms.openlocfilehash: ce3473365eb98beca4d2e9116251200d7539e4c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647389"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="2adfe-103">ICorProfilerInfo::GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="2adfe-103">ICorProfilerInfo::GetILToNativeMapping Method</span></span>

<span data-ttu-id="2adfe-104">Microsoft Intermediate Language (MSIL) オフセットから、指定した関数に含まれるコードのネイティブ オフセットへのマップを取得します。</span><span class="sxs-lookup"><span data-stu-id="2adfe-104">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2adfe-105">構文</span><span class="sxs-lookup"><span data-stu-id="2adfe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2adfe-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2adfe-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="2adfe-107">[in] コードを含む関数の ID。</span><span class="sxs-lookup"><span data-stu-id="2adfe-107">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="2adfe-108">[in] `map` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="2adfe-108">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="2adfe-109">[out]使用できる COR_DEBUG_IL_TO_NATIVE_MAP 構造体の総数。</span><span class="sxs-lookup"><span data-stu-id="2adfe-109">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="2adfe-110">[out] `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の配列。各構造体はオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="2adfe-110">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="2adfe-111">`GetILToNativeMapping` メソッドから制御が戻ると、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の一部または全部が `map` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="2adfe-111">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2adfe-112">解説</span><span class="sxs-lookup"><span data-stu-id="2adfe-112">Remarks</span></span>  

 <span data-ttu-id="2adfe-113">`GetILToNativeMapping` メソッドは、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="2adfe-113">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="2adfe-114">ネイティブ命令の特定の範囲がコードの特別な領域 (プロローグなど) に対応することを伝えるために、配列内のエントリは、その `ilOffset` フィールドを [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) 列挙値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="2adfe-114">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="2adfe-115">`GetILToNativeMapping` から制御が戻ったら、`map` バッファーのサイズが十分で、すべての `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2adfe-115">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="2adfe-116">これを行うには、`cMap` の値を `pcMap` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="2adfe-116">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="2adfe-117">`pcMap` 値 に `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体のサイズを乗算した結果が `cMap` より大きい場合は、`map` バッファーの割り当てを増やし、`cMap` を新しい大きいサイズに更新した後、`GetILToNativeMapping` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2adfe-117">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="2adfe-118">別の方法として、最初に `GetILToNativeMapping` を長さゼロの `map` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="2adfe-118">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="2adfe-119">その後、バッファーのサイズを `pcMap` で返された値に設定し、`GetILToNativeMapping` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2adfe-119">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2adfe-120">要件</span><span class="sxs-lookup"><span data-stu-id="2adfe-120">Requirements</span></span>  

 <span data-ttu-id="2adfe-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2adfe-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2adfe-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2adfe-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2adfe-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2adfe-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2adfe-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2adfe-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2adfe-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="2adfe-125">See also</span></span>

- [<span data-ttu-id="2adfe-126">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2adfe-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="2adfe-127">GetILToNativeMapping2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2adfe-127">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="2adfe-128">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2adfe-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2adfe-129">プロファイル</span><span class="sxs-lookup"><span data-stu-id="2adfe-129">Profiling</span></span>](index.md)

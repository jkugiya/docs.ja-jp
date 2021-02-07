---
description: '詳細について: ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs メソッド'
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
ms.openlocfilehash: 810445d2617beff55e00df6bb30130d81c740ba4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760488"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="70751-103">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs メソッド</span><span class="sxs-lookup"><span data-stu-id="70751-103">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>

<span data-ttu-id="70751-104">`ClassID`指定されたメタデータトークンと `ClassID` 任意の型引数の値を使用して、型のを取得します。</span><span class="sxs-lookup"><span data-stu-id="70751-104">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70751-105">構文</span><span class="sxs-lookup"><span data-stu-id="70751-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70751-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="70751-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="70751-107">から型が存在するモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="70751-107">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="70751-108">から `mdTypeDef` 型を参照するメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="70751-108">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="70751-109">から指定された型の型パラメーターの数。</span><span class="sxs-lookup"><span data-stu-id="70751-109">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="70751-110">非ジェネリック型の場合、この値は0である必要があります。</span><span class="sxs-lookup"><span data-stu-id="70751-110">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="70751-111">から値の配列 `ClassID` 。それぞれが型の引数になります。</span><span class="sxs-lookup"><span data-stu-id="70751-111">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="70751-112">が0に設定されている場合、の値は `typeArgs` NULL `cTypeArgs` になります。</span><span class="sxs-lookup"><span data-stu-id="70751-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="70751-113">入出力 `ClassID` 指定した型のへのポインター。</span><span class="sxs-lookup"><span data-stu-id="70751-113">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70751-114">解説</span><span class="sxs-lookup"><span data-stu-id="70751-114">Remarks</span></span>  

 <span data-ttu-id="70751-115">メタデータトークンの代わりにを指定してメソッドを呼び出すと、 `GetClassFromTokenAndTypeArgs` `mdTypeRef` `mdTypeDef` 予期しない結果が発生する可能性があります。呼び出し元は、 `mdTypeRef` を `mdTypeDef` 渡すときにを解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70751-115">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="70751-116">型がまだ読み込まれていない場合、を呼び出す `GetClassFromTokenAndTypeArgs` と読み込みがトリガーされます。これは、多くのコンテキストでは危険な操作です。</span><span class="sxs-lookup"><span data-stu-id="70751-116">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="70751-117">たとえば、モジュールまたはその他の型の読み込み中にこのメソッドを呼び出すと、ランタイムが循環読み込みを試みたときに無限ループが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="70751-117">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="70751-118">一般に、の使用 `GetClassFromTokenAndTypeArgs` は推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="70751-118">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="70751-119">プロファイラーが特定の型のイベントに関心を持っている場合は、その型のとを格納し、ICorProfilerInfo2:: GetClassIDInfo2 を使用して、特定の `ModuleID` `mdTypeDef` [](icorprofilerinfo2-getclassidinfo2-method.md) `ClassID` が目的の型であるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70751-119">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70751-120">要件</span><span class="sxs-lookup"><span data-stu-id="70751-120">Requirements</span></span>  

 <span data-ttu-id="70751-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70751-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70751-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="70751-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="70751-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70751-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70751-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70751-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70751-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="70751-125">See also</span></span>

- [<span data-ttu-id="70751-126">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="70751-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="70751-127">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="70751-127">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)

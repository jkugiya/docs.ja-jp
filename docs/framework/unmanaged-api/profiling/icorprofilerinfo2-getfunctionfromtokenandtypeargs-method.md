---
description: '詳細について: ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs メソッド'
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
ms.openlocfilehash: 4b4bb8631a5f33c939666af68226b19d2e4d666d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799035"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="12321-103">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs メソッド</span><span class="sxs-lookup"><span data-stu-id="12321-103">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>

<span data-ttu-id="12321-104">`FunctionID`指定されたメタデータトークン、クラス、および `ClassID` 任意の型引数の値を使用して、関数のを取得します。</span><span class="sxs-lookup"><span data-stu-id="12321-104">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12321-105">構文</span><span class="sxs-lookup"><span data-stu-id="12321-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12321-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12321-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="12321-107">から関数が存在するモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="12321-107">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="12321-108">から `mdMethodDef` 関数を参照するメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="12321-108">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="12321-109">からクラスを含んでいる関数の ID。</span><span class="sxs-lookup"><span data-stu-id="12321-109">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="12321-110">から指定された関数の型パラメーターの数。</span><span class="sxs-lookup"><span data-stu-id="12321-110">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="12321-111">非ジェネリック関数の場合、この値は0である必要があります。</span><span class="sxs-lookup"><span data-stu-id="12321-111">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="12321-112">から値の配列 `ClassID` 。それぞれが関数の引数です。</span><span class="sxs-lookup"><span data-stu-id="12321-112">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="12321-113">が0に設定されている場合、の値は `typeArgs` NULL `cTypeArgs` になります。</span><span class="sxs-lookup"><span data-stu-id="12321-113">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="12321-114">入出力 `FunctionID` 指定した関数のへのポインター。</span><span class="sxs-lookup"><span data-stu-id="12321-114">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12321-115">解説</span><span class="sxs-lookup"><span data-stu-id="12321-115">Remarks</span></span>  

 <span data-ttu-id="12321-116">メタデータ `GetFunctionFromTokenAndTypeArgs` トークンではなくメタデータを使用してメソッドを呼び出すと、 `mdMethodRef` `mdMethodDef` 予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="12321-116">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="12321-117">呼び出し元は、 `mdMethodRef` を渡すときにをに解決する必要があり `mdMethodDef` ます。</span><span class="sxs-lookup"><span data-stu-id="12321-117">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="12321-118">関数がまだ読み込まれていない場合、を呼び出すと `GetFunctionFromTokenAndTypeArgs` 読み込みが発生します。これは、多くのコンテキストでは危険な操作です。</span><span class="sxs-lookup"><span data-stu-id="12321-118">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="12321-119">たとえば、モジュールまたは型の読み込み中にこのメソッドを呼び出すと、ランタイムが循環読み込みを試みたときに無限ループが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="12321-119">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="12321-120">一般に、の使用 `GetFunctionFromTokenAndTypeArgs` は推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="12321-120">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="12321-121">プロファイラーが特定の関数のイベントに関心を持っている場合は、 `ModuleID` その関数のとを格納し、 `mdMethodDef` [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) を使用して、 `FunctionID` 目的の関数のが指定されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="12321-121">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12321-122">要件</span><span class="sxs-lookup"><span data-stu-id="12321-122">Requirements</span></span>  

 <span data-ttu-id="12321-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12321-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12321-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12321-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12321-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12321-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12321-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12321-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12321-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="12321-127">See also</span></span>

- [<span data-ttu-id="12321-128">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12321-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="12321-129">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12321-129">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)

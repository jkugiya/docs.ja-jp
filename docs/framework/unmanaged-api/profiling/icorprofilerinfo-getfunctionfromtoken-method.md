---
description: '詳細について: ICorProfilerInfo:: GetFunctionFromToken メソッド'
title: ICorProfilerInfo::GetFunctionFromToken メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
ms.openlocfilehash: 58dea413539d6e3a625f515aa7e8d5123152c90a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647454"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="0aa9c-103">ICorProfilerInfo::GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="0aa9c-103">ICorProfilerInfo::GetFunctionFromToken Method</span></span>

<span data-ttu-id="0aa9c-104">関数の ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="0aa9c-104">Gets the ID of a function.</span></span> <span data-ttu-id="0aa9c-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="0aa9c-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="0aa9c-106">代わりに [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="0aa9c-106">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa9c-107">構文</span><span class="sxs-lookup"><span data-stu-id="0aa9c-107">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="0aa9c-108">解説</span><span class="sxs-lookup"><span data-stu-id="0aa9c-108">Remarks</span></span>  

 <span data-ttu-id="0aa9c-109">メソッドは、ジェネリック `GetFunctionFromToken` 型のジェネリック関数または関数に対しては機能しません。現在は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="0aa9c-109">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="0aa9c-110">`ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs`すべての関数に使用します。</span><span class="sxs-lookup"><span data-stu-id="0aa9c-110">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa9c-111">要件</span><span class="sxs-lookup"><span data-stu-id="0aa9c-111">Requirements</span></span>  

 <span data-ttu-id="0aa9c-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0aa9c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa9c-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0aa9c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0aa9c-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0aa9c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0aa9c-115">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="0aa9c-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa9c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0aa9c-116">See also</span></span>

- [<span data-ttu-id="0aa9c-117">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0aa9c-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

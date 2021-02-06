---
description: '詳細について: ICorProfilerInfo:: GetClassFromToken メソッド'
title: ICorProfilerInfo::GetClassFromToken メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
ms.openlocfilehash: 0460a9b767f29f108a2b290b848f4cc6b6394ecb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647753"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="cbc24-103">ICorProfilerInfo::GetClassFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="cbc24-103">ICorProfilerInfo::GetClassFromToken Method</span></span>

<span data-ttu-id="cbc24-104">メタデータトークンを指定して、クラスの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="cbc24-104">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="cbc24-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="cbc24-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="cbc24-106">代わりに [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="cbc24-106">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc24-107">構文</span><span class="sxs-lookup"><span data-stu-id="cbc24-107">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbc24-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cbc24-108">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="cbc24-109">からクラスを含むモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="cbc24-109">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="cbc24-110">から `mdTypeDef` クラスを参照するメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="cbc24-110">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="cbc24-111">入出力クラス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cbc24-111">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbc24-112">解説</span><span class="sxs-lookup"><span data-stu-id="cbc24-112">Remarks</span></span>  

 <span data-ttu-id="cbc24-113">このメソッドは互換性のために残されています。代わりに、 `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` すべての型に対してを使用します。</span><span class="sxs-lookup"><span data-stu-id="cbc24-113">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbc24-114">要件</span><span class="sxs-lookup"><span data-stu-id="cbc24-114">Requirements</span></span>  

 <span data-ttu-id="cbc24-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbc24-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbc24-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cbc24-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cbc24-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbc24-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbc24-118">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="cbc24-118">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc24-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="cbc24-119">See also</span></span>

- [<span data-ttu-id="cbc24-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cbc24-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
